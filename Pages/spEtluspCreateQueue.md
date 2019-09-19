Stored Procedure Etl.uspCreateQueue {#spEtluspCreateQueue}
-----------------------------------

Definition of Stored procedure:

``` {.sql}
CREATE PROCEDURE Etl.uspCreateQueue
AS
BEGIN TRY
    -- set up the enviroment
    SET NOCOUNT ON;

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

    --Get Actual Vault Status
    DROP TABLE IF EXISTS #VaultLastRun;

    SELECT * 
    INTO #VaultLastRun
    FROM Etl.VaultLastRun

    --Insert request on Vault object that can be loaded
    INSERT INTO Etl.ThreadLog (
        ThreadId
        , RequestId
        , StatusId
        , ScheduledTime
    )
    SELECT 
        ThreadId = VaultThreadId
        , RequestId = @RequestId
        , StatusId = 5
        , ScheduledTime = GETDATE()
    FROM #VaultLastRun
    WHERE VaultThreadId NOT IN (
        --Not load Threads their Stage object was not corectly loaded
        SELECT VaultThreadId 
        FROM #VaultLastRun
        WHERE COALESCE(StageStatusId, 0) <> 3 
        UNION ALL
        --Not load Threads that has been already loaded
        SELECT VaultThreadId 
        FROM #VaultLastRun
        WHERE VaultStatusId = 3 AND StageEndTime < VaultEndTime AND StageStatusId = 3
        --Not load Vault Threads that are now loading 
        UNION ALL
        SELECT VaultThreadId
        FROM Etl.VaultLastRun
        WHERE VaultStatusId IN (1,2,5)
    )

    DECLARE @FirsLoadTime datetime2;

    SELECT @FirsLoadTime = CONVERT(varchar, ParameterValue, 108)
    FROM Admin.DwParameter 
    WHERE ParameterName = N'LoadStartTime';

    IF @FirsLoadTime <= GETDATE()
    BEGIN


    --Get Actual Stage Status
    DROP TABLE IF EXISTS #StageLastRun;

    SELECT * 
    INTO #StageLastRun
    FROM Etl.StageLastRun

    --Insert request on Stage object that can be loaded
    INSERT INTO Etl.ThreadLog (
        ThreadId
        , RequestId
        , StatusId
        , ScheduledTime
    )
    SELECT 
        ThreadId = StageThreadId
        , RequestId = @RequestId
        , StatusId = 5
        , ScheduledTime = GETDATE()
    FROM #StageLastRun
    WHERE StageThreadId NOT IN (
        --Not load Threads that were not correctly loaded by Vault
        SELECT StageThreadId 
        FROM #StageLastRun
        WHERE VaultStatusId <> 3 
        UNION ALL
        --Not load Threads that has not been loaded by Vault yet
        SELECT StageThreadId 
        FROM #StageLastRun
        WHERE COALESCE(VaultStatusId, 3) = 3 AND StageEndTime > COALESCE(VaultEndTime, '1901-01-01') AND StageStatusId = 3

    )
    --Load only Threads that go through frequency condition
    AND StageLoadFrequency <= DATEDIFF(mi,COALESCE(StageStartTime,'1901-01-01'), @RequestCreatedTime)
    AND COALESCE(StageStatusId, 3) NOT IN (1,2,5)

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

    PRINT N'Error during Filling queue. Error meassage:' + @errMessage;

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
