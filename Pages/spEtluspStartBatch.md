Stored Procedure Etl.uspStartBatch {#spEtluspStartBatch}
----------------------------------

List of dependent objects: Etl.uspUserLoad

Definition of Stored procedure:

``` {.sql}
CREATE PROCEDURE Etl.uspStartBatch
AS
BEGIN TRY
    -- set up the enviroment
    SET NOCOUNT ON;

    IF EXISTS (SELECT * FROM Etl.ThreadLog WHERE ScheduledTime <= GETDATE() AND StatusId = 5)

    BEGIN
    --Declare variables for threads of actual batch
    DECLARE @ThreadList TABLE 
    (
        ThreadId int
    );
    DECLARE @threadCount int;

    --Create batch for thread request
    --Declare variables
    DECLARE @Batch TABLE 
    (
        BatchId int
    );
    DECLARE @BatchId int;

    --Create new batch
    INSERT INTO Etl.Batch (
        CreatedTime
        , StatusId
    )
    OUTPUT INSERTED.BatchId INTO @Batch
    SELECT 
        CreatedTime = GETDATE()
        , StatusId = 5;

    --Get that batch number
    SELECT @BatchId = BatchId FROM @Batch;

    UPDATE Etl.ThreadLog
    SET BatchId = @BatchId
        , StatusId = 2
    OUTPUT INSERTED.ThreadId INTO @ThreadList
    WHERE ScheduledTime <= GETDATE() AND StatusId = 5;

    SELECT @threadCount = COUNT(*) FROM @ThreadList;

    UPDATE Etl.Batch 
    SET StatusId = 2
        , NumberOfThreads = @threadCount
    WHERE BatchId = @BatchId;

    --Start Etl SSIS Package

    -- get the ETL package name
    DECLARE @etlProjectName nvarchar(100)
            , @etlFoldername nvarchar(100);

    SELECT @etlProjectName = ParameterValue FROM Admin.DwParameter WHERE ParameterName = 'EtlProjectName';
    SELECT @etlFoldername = ParameterValue FROM Admin.DwParameter WHERE ParameterName = 'EtlFolderName';
    DECLARE @reference_id int;

    SELECT @reference_id = r.reference_id 
    FROM SSISDB.internal.environment_references r
    INNER JOIN SSISDB.internal.projects p
        ON r.project_id = p.project_id 
    INNER JOIN SSISDB.internal.folders f
        ON p.folder_id = f.folder_id 
    WHERE 
    r.environment_name = N'Publish'
    AND p.name = 'Etl'
    AND f.name = 'Etl';



    DECLARE @execution_id bigint; 
    EXEC [SSISDB].[catalog].[create_execution] 
        @package_name=N'Master.dtsx'
        , @execution_id=@execution_id OUTPUT
        , @folder_name=@etlFoldername
        , @project_name=@etlProjectName
        , @use32bitruntime=False
        , @reference_id=@reference_id;

    EXEC [SSISDB].[catalog].[set_execution_parameter_value] 
        @execution_id
        , @object_type=30
        , @parameter_name=N'BatchId'
        , @parameter_value=@BatchId;

    EXEC [SSISDB].[catalog].[start_execution] @execution_id

    END

    ELSE 
    PRINT N'No threads for create Batch.';


END TRY

BEGIN CATCH

    DECLARE @errMessage NVARCHAR(2048)
            , @errSeverity INT
            , @errState INT;
    SELECT 
        @errMessage = ERROR_MESSAGE()
        , @errSeverity = ERROR_SEVERITY()
        , @errState = ERROR_STATE();

    -- rollback the transaction, in which the error occured
    IF @@TRANCOUNT > 0 
        ROLLBACK;

    PRINT N'Error during starting batch. Error meassage:' + @errMessage;

    -- re-raise the error for the calling process
    RAISERROR
    (   
        @errMessage     -- Message text
        , @errSeverity  -- Severity
        , @errState     -- State
    );
       

END CATCH
```

\[Back to stored procedure list\]\[listofprocedures\]
