Stored Procedure Stage.uspLoadCERTdboRenting {#spStageuspLoadCERTdboRenting}
--------------------------------------------

Definition of Stored procedure:

``` {.sql}
CREATE PROCEDURE [Stage].[uspLoadCERTdboRenting] 
    @ThreadLogId int
        , @DataSourceId int
    AS
    BEGIN TRY
        -- set up the enviroment
        SET NOCOUNT ON;
    

        TRUNCATE TABLE [Stage].[CERTdboRenting]; 

        -- log the initial table state
        UPDATE Etl.ThreadLog
            SET TableInitialRowCount = (SELECT COUNT(*) FROM [Stage].[CERTdboRenting] WITH (NOLOCK))
        WHERE ThreadLogId = @ThreadLogId;

        DECLARE @loadDateFrom datetime2;
        SELECT @loadDateFrom = '1901-01-01';

        INSERT INTO [Stage].[CERTdboRenting]
            ( 
                [ContractNo]
                , [CustomerChargeCZK]
                , [CustomerChargeEUR]
                , [DoplatekCZK]
                , [DoplatekEUR]
                , [ID_Customer]
                , [ID_DealerConveyor]
                , [ID_DobaPronajmu]
                , [ID_Projezd]
                , [ID_RENTING]
                , [ID_Trailer]
                , [ID_User]
                , [IDD]
                , [LastMonthFree]
                , [OdometerEND]
                , [OdometerSTART]
                , [OverKMchargeCZK]
                , [OverKMchargeEUR]
                , [RENTend]
                , [RENTremark]
                , [RENTstart]
                , [DataSourceId]
                , [ThreadLogId]
    )

        SELECT 
                [ContractNo] = s.[ContractNo]
                , [CustomerChargeCZK] = s.[CustomerChargeCZK]
                , [CustomerChargeEUR] = s.[CustomerChargeEUR]
                , [DoplatekCZK] = s.[DoplatekCZK]
                , [DoplatekEUR] = s.[DoplatekEUR]
                , [ID_Customer] = s.[ID_Customer]
                , [ID_DealerConveyor] = s.[ID_DealerConveyor]
                , [ID_DobaPronajmu] = s.[ID_DobaPronajmu]
                , [ID_Projezd] = s.[ID_Projezd]
                , [ID_RENTING] = s.[ID_RENTING]
                , [ID_Trailer] = s.[ID_Trailer]
                , [ID_User] = s.[ID_User]
                , [IDD] = s.[IDD]
                , [LastMonthFree] = s.[LastMonthFree]
                , [OdometerEND] = s.[OdometerEND]
                , [OdometerSTART] = s.[OdometerSTART]
                , [OverKMchargeCZK] = s.[OverKMchargeCZK]
                , [OverKMchargeEUR] = s.[OverKMchargeEUR]
                , [RENTend] = s.[RENTend]
                , [RENTremark] = s.[RENTremark]
                , [RENTstart] = s.[RENTstart]
                , [DataSourceId] = @DataSourceId
                , [ThreadLogId] = @ThreadLogId
    
        FROM [CERTST10].[CERT].[dbo].[Renting] AS s WITH (NOLOCK)

        --Log ThreadLog Success
        UPDATE Etl.ThreadLog
        SET ExtractRowCount = (SELECT COUNT(*) FROM [Stage].[CERTdboRenting] WITH (NOLOCK) WHERE ThreadLogId = @ThreadLogId)
            , InsertRowCount = (SELECT COUNT(*) FROM [Stage].[CERTdboRenting] WITH (NOLOCK) WHERE ThreadLogId = @ThreadLogId)
            , TableFinalRowCount = (SELECT COUNT(*) FROM [Stage].[CERTdboRenting] WITH (NOLOCK) )
            , EndTime = GETDATE()
            , LoadDateFrom = @loadDateFrom
            , LoadDateTo = GETDATE()
            , StatusId = 3
        WHERE ThreadLogId = @ThreadLogId;

        END TRY

        BEGIN CATCH
            EXEC [dbo].[uspErrorHandler] @ThreadLogId = @ThreadLogId;
        END CATCH
            
        RETURN;
```

\[Back to stored procedure list\]\[listofprocedures\]
