Stored Procedure dbo.uspErrorHandler {#spdbouspErrorHandler}
------------------------------------

Description: Error handling procedure with error info logging

List of dependent objects: Stage.uspLoadCERTdboBusOrders,
Vault.uspLoadCERTdboBusOrders, Stage.uspLoadCERTdboCountry,
Vault.uspLoadCERTdboCountry, Vault.uspLoadCERTdboDealers,
Stage.uspLoadCERTdboDealers, Vault.uspLoadCERTdboOrders,
Stage.uspLoadCERTdboOrders, Vault.uspLoadCERTdboRenting,
Stage.uspLoadCERTdboRenting, Stage.uspLoadCERTdboUsers,
Vault.uspLoadCERTdboUsers, Vault.uspLoadCRMdboAccount,
Stage.uspLoadCRMdboAccount, Stage.uspLoadCRMdboAppointment,
Vault.uspLoadCRMdboAppointment, Vault.uspLoadCRMdboBusinessunit,
Stage.uspLoadCRMdboBusinessunit, Stage.uspLoadCRMdboEmail,
Vault.uspLoadCRMdboEmail, Vault.uspLoadCRMdboGlobalOptionSetMetadata,
Stage.uspLoadCRMdboGlobalOptionSetMetadata,
Stage.uspLoadCRMdboLlp\_canton, Vault.uspLoadCRMdboLlp\_canton,
Vault.uspLoadCRMdboLlp\_country, Stage.uspLoadCRMdboLlp\_country,
Stage.uspLoadCRMdboOpportunity, Vault.uspLoadCRMdboOpportunity,
Vault.uspLoadCRMdboOptionSetMetadata,
Stage.uspLoadCRMdboOptionSetMetadata, Stage.uspLoadCRMdboPhonecall,
Vault.uspLoadCRMdboPhonecall, Vault.uspLoadCRMdboStateMetadata,
Stage.uspLoadCRMdboStateMetadata, Stage.uspLoadCRMdboStatusMetadata,
Vault.uspLoadCRMdboStatusMetadata, Vault.uspLoadCRMdboSystemuser,
Stage.uspLoadCRMdboSystemuser

Definition of Stored procedure:

``` {.sql}
CREATE PROCEDURE dbo.uspErrorHandler
    @ThreadLogId int    -- ID of Thread log, where the error was caught
AS
    DECLARE @errMessage NVARCHAR(2048)
            , @errSeverity INT
            , @errState INT
            , @errNumber INT
            , @errProcName NVARCHAR(70);

    -- get the calling sp name

    SELECT 
        @errMessage = ERROR_MESSAGE()
        , @errSeverity = ERROR_SEVERITY()
        , @errState = ERROR_STATE()
        , @errNumber = ERROR_NUMBER ();


    -- rollback the transaction, in which the error occured
    IF @@TRANCOUNT > 0 
        ROLLBACK;

    -- log the error info
    UPDATE Etl.ThreadLog
    SET
        ErrorNumber = @errNumber
        , ErrorMessage = @errMessage
        , ErrorSeverity = @errSeverity
        , ErrorState = @errState
        , StatusId = 4                      -- Error
        , EndTime = GETDATE()
    WHERE ThreadLogId = @ThreadLogId;

    -- re-raise the error for the calling process
    RAISERROR
    (   
        @errMessage     -- Message text
        , @errSeverity  -- Severity
        , @errState     -- State
    );
```

\[Back to stored procedure list\]\[listofprocedures\]
