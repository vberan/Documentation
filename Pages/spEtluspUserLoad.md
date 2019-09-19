Stored Procedure Etl.uspUserLoad {#spEtluspUserLoad}
--------------------------------

Definition of Stored procedure:

``` {.sql}
CREATE PROCEDURE Etl.uspUserLoad
AS
BEGIN TRY
    -- set up the enviroment
    SET NOCOUNT ON;

    IF EXISTS (SELECT * FROM Etl.ThreadLog WHERE StatusId NOT IN (3,4))
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

    --Insert request on Stage object that can be loaded
    DECLARE @ThreadLog TABLE (
        ThreadLogId int
    )
    INSERT INTO Etl.ThreadLog (
        ThreadId
        , RequestId
        , StatusId
        , ScheduledTime
    )
    OUTPUT inserted.ThreadLogId INTO @ThreadLog
    SELECT 
        ThreadId = ThreadId
        , RequestId = @RequestId
        , StatusId = 5
        , ScheduledTime = GETDATE()
    FROM Etl.Thread
    WHERE DwLevelId = 2;

    --Log ThreadLogId into UserThreadLog table
    INSERT INTO Etl.UserThreadLog (
        ThreadLogId
    )
    SELECT 
        ThreadLogId
    FROM @ThreadLog;

    EXEC Etl.uspStartBatch;


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

    PRINT N'Error during creating user load Batch. Error meassage:' + @errMessage;

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
