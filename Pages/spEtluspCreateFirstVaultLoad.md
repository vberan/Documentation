Stored Procedure Etl.uspCreateFirstVaultLoad {#spEtluspCreateFirstVaultLoad}
--------------------------------------------

Definition of Stored procedure:

``` {.sql}
CREATE PROCEDURE Etl.uspCreateFirstVaultLoad
AS
BEGIN TRY

    -- set up the enviroment
    SET NOCOUNT ON;

    IF NOT EXISTS (SELECT ParameterValue FROM Admin.DwParameter WHERE ParameterName = N'LoadStartTime')
    BEGIN
     Start:
    IF EXISTS(
    SELECT ThreadId FROM Etl.ThreadLog WHERE RequestId = 1 AND StatusId <> 3
    )
    BEGIN
        WAITFOR DELAY '00:01' 
        GOTO Start
    END
    ELSE

    BEGIN

    -- Create Request
    -- Declare table
    DECLARE @Request TABLE (
        RequestId int
        , CreatedTime datetime2
    )
    DECLARE @RequestId int;
    DECLARE @RequestCreatedTime datetime2
    -- 
    INSERT INTO Etl.Request (
        CreatedTime
    )
    OUTPUT inserted.* INTO @Request
    SELECT GETDATE()

    SELECT 
        @RequestId = RequestId
        , @RequestCreatedTime = CreatedTime
    FROM @Request;


    --Fill first load objects in ThreadLog
    INSERT INTO Etl.ThreadLog (
        ThreadId
        , RequestId
        , StatusId
        , ScheduledTime
    )
    SELECT 
        ThreadId = tv.ThreadId
        , RequestId = @RequestId
        , StatusId = 5
        , ScheduledTime = GETDATE()
    FROM Etl.Thread tf
    LEFT OUTER JOIN Etl.Thread tv
        ON RIGHT(tf.LoadObjectName, LEN(tf.LoadObjectName) - CHARINDEX('.', tf.LoadObjectName)) =  RIGHT(tv.LoadObjectName, LEN(tv.LoadObjectName) - CHARINDEX('.', tv.LoadObjectName))
        AND tv.DwLevelId = 4
    WHERE tf.DwLevelId = 1 AND tf.ThreadId <> -1;
    

    DECLARE @startTime nvarchar(20) = N'08:10';
    DECLARE @LoadStartTime datetime2;

    SELECT @LoadStartTime = CAST(CASE WHEN CAST(GETDATE() AS Time) > CAST(@startTime AS time)
                THEN CAST(CONCAT(CAST(DATEADD(dd,1,GETDATE()) AS date), ' ',CAST(@startTime AS time)) AS datetime2) 
                ELSE CAST(CONCAT(CAST(GETDATE() AS date), ' ', CAST(@startTime AS time)) AS datetime2)
            END
            AS nvarchar(50))

    INSERT INTO Admin.DwParameter
    (
        ParameterName
        , ParameterValue
    )
    VALUES
    (N'LoadStartTime', @LoadStartTime);

    END
    END
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

    PRINT N'Error during Filling First Vault queue. Error meassage:' + @errMessage;

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
