Stored Procedure Etl.uspCreateFirstLoadQueue {#spEtluspCreateFirstLoadQueue}
--------------------------------------------

Definition of Stored procedure:

``` {.sql}
CREATE PROCEDURE Etl.uspCreateFirstLoadQueue
AS
BEGIN TRY
    -- set up the enviroment
    SET NOCOUNT ON;
    
    --Fill first load objects in ThreadLog
    INSERT INTO Etl.ThreadLog (
        ThreadId
        , RequestId
        , StatusId
        , ScheduledTime
    )
    SELECT 
        ThreadId = t.ThreadId
        , RequestId = 1
        , StatusId = 5
        , ScheduledTime = GETDATE()
    FROM Etl.Thread t
    WHERE t.DwLevelId = 1 AND t.ThreadId <> -1;

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

    PRINT N'Error during Filling First Load queue. Error meassage:' + @errMessage;

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
