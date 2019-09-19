Stored Procedure Vault.uspLoadCERTdboRenting {#spVaultuspLoadCERTdboRenting}
--------------------------------------------

Definition of Stored procedure:

``` {.sql}
CREATE PROCEDURE [Vault].[uspLoadCERTdboRenting] 
    @ThreadLogId int
        , @DataSourceId int
    AS
    BEGIN TRY
            -- set up the enviroment
            SET NOCOUNT ON;
            
            DECLARE @rowCounts TABLE
            (
                MergeAction nvarchar(10)
            );
            DECLARE @UpdateRowCounts TABLE
            (
                ThreadLogUpdateId int
            );
            DECLARE @DeleteRowCounts TABLE
            (
                ThreadLogDeleteId int
            );
    -- log the initial table state
        UPDATE Etl.ThreadLog
            SET TableInitialRowCount = (SELECT COUNT(*) FROM [Vault].[CERTdboRenting] WITH (NOLOCK))
        WHERE ThreadLogId = @ThreadLogId;

            BEGIN TRANSACTION;

    
        MERGE INTO [Vault].[CERTdboRenting] AS v
        USING [Stage].[CERTdboRenting] AS s
            ON ( s.[ID_RENTING] = v.[ID_RENTING]AND s.[DataSourceId] = v.[DataSourceId]
     AND v.[ThreadLogDeleteId] = -1 AND v.[ThreadLogUpdateId] = -1 AND v.[ChangeOperation] <> N'D'
    )

        WHEN MATCHED AND
            (
            v.[ContractNo] <> s.[ContractNo]
            OR (v.[ContractNo] IS NULL AND s.[ContractNo] IS NOT NULL)
        OR (v.[ContractNo] IS NOT NULL AND s.[ContractNo] IS NULL)
        OR v.[CustomerChargeCZK] <> s.[CustomerChargeCZK]
            OR (v.[CustomerChargeCZK] IS NULL AND s.[CustomerChargeCZK] IS NOT NULL)
        OR (v.[CustomerChargeCZK] IS NOT NULL AND s.[CustomerChargeCZK] IS NULL)
        OR v.[CustomerChargeEUR] <> s.[CustomerChargeEUR]
            OR (v.[CustomerChargeEUR] IS NULL AND s.[CustomerChargeEUR] IS NOT NULL)
        OR (v.[CustomerChargeEUR] IS NOT NULL AND s.[CustomerChargeEUR] IS NULL)
        OR v.[DoplatekCZK] <> s.[DoplatekCZK]
            OR (v.[DoplatekCZK] IS NULL AND s.[DoplatekCZK] IS NOT NULL)
        OR (v.[DoplatekCZK] IS NOT NULL AND s.[DoplatekCZK] IS NULL)
        OR v.[DoplatekEUR] <> s.[DoplatekEUR]
            OR (v.[DoplatekEUR] IS NULL AND s.[DoplatekEUR] IS NOT NULL)
        OR (v.[DoplatekEUR] IS NOT NULL AND s.[DoplatekEUR] IS NULL)
        OR v.[ID_Customer] <> s.[ID_Customer]
            OR (v.[ID_Customer] IS NULL AND s.[ID_Customer] IS NOT NULL)
        OR (v.[ID_Customer] IS NOT NULL AND s.[ID_Customer] IS NULL)
        OR v.[ID_DealerConveyor] <> s.[ID_DealerConveyor]
            OR (v.[ID_DealerConveyor] IS NULL AND s.[ID_DealerConveyor] IS NOT NULL)
        OR (v.[ID_DealerConveyor] IS NOT NULL AND s.[ID_DealerConveyor] IS NULL)
        OR v.[ID_DobaPronajmu] <> s.[ID_DobaPronajmu]
            OR (v.[ID_DobaPronajmu] IS NULL AND s.[ID_DobaPronajmu] IS NOT NULL)
        OR (v.[ID_DobaPronajmu] IS NOT NULL AND s.[ID_DobaPronajmu] IS NULL)
        OR v.[ID_Projezd] <> s.[ID_Projezd]
            OR (v.[ID_Projezd] IS NULL AND s.[ID_Projezd] IS NOT NULL)
        OR (v.[ID_Projezd] IS NOT NULL AND s.[ID_Projezd] IS NULL)
        OR v.[ID_Trailer] <> s.[ID_Trailer]
            OR (v.[ID_Trailer] IS NULL AND s.[ID_Trailer] IS NOT NULL)
        OR (v.[ID_Trailer] IS NOT NULL AND s.[ID_Trailer] IS NULL)
        OR v.[ID_User] <> s.[ID_User]
            OR (v.[ID_User] IS NULL AND s.[ID_User] IS NOT NULL)
        OR (v.[ID_User] IS NOT NULL AND s.[ID_User] IS NULL)
        OR v.[IDD] <> s.[IDD]
            OR (v.[IDD] IS NULL AND s.[IDD] IS NOT NULL)
        OR (v.[IDD] IS NOT NULL AND s.[IDD] IS NULL)
        OR v.[LastMonthFree] <> s.[LastMonthFree]
            OR v.[OdometerEND] <> s.[OdometerEND]
            OR (v.[OdometerEND] IS NULL AND s.[OdometerEND] IS NOT NULL)
        OR (v.[OdometerEND] IS NOT NULL AND s.[OdometerEND] IS NULL)
        OR v.[OdometerSTART] <> s.[OdometerSTART]
            OR (v.[OdometerSTART] IS NULL AND s.[OdometerSTART] IS NOT NULL)
        OR (v.[OdometerSTART] IS NOT NULL AND s.[OdometerSTART] IS NULL)
        OR v.[OverKMchargeCZK] <> s.[OverKMchargeCZK]
            OR (v.[OverKMchargeCZK] IS NULL AND s.[OverKMchargeCZK] IS NOT NULL)
        OR (v.[OverKMchargeCZK] IS NOT NULL AND s.[OverKMchargeCZK] IS NULL)
        OR v.[OverKMchargeEUR] <> s.[OverKMchargeEUR]
            OR (v.[OverKMchargeEUR] IS NULL AND s.[OverKMchargeEUR] IS NOT NULL)
        OR (v.[OverKMchargeEUR] IS NOT NULL AND s.[OverKMchargeEUR] IS NULL)
        OR v.[RENTend] <> s.[RENTend]
            OR (v.[RENTend] IS NULL AND s.[RENTend] IS NOT NULL)
        OR (v.[RENTend] IS NOT NULL AND s.[RENTend] IS NULL)
        OR v.[RENTremark] <> s.[RENTremark]
            OR (v.[RENTremark] IS NULL AND s.[RENTremark] IS NOT NULL)
        OR (v.[RENTremark] IS NOT NULL AND s.[RENTremark] IS NULL)
        OR v.[RENTstart] <> s.[RENTstart]
            OR (v.[RENTstart] IS NULL AND s.[RENTstart] IS NOT NULL)
        OR (v.[RENTstart] IS NOT NULL AND s.[RENTstart] IS NULL)
        )
        THEN 
            UPDATE SET
                [ThreadLogUpdateId] = @ThreadLogId
            

                
        WHEN NOT MATCHED BY TARGET 
            THEN INSERT
            ( 
            [ID_RENTING]
            , [ContractNo]
            , [CustomerChargeCZK]
            , [CustomerChargeEUR]
            , [DoplatekCZK]
            , [DoplatekEUR]
            , [ID_Customer]
            , [ID_DealerConveyor]
            , [ID_DobaPronajmu]
            , [ID_Projezd]
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
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
            
    ) VALUES (
            s.[ID_RENTING]
            , s.[ContractNo]
            , s.[CustomerChargeCZK]
            , s.[CustomerChargeEUR]
            , s.[DoplatekCZK]
            , s.[DoplatekEUR]
            , s.[ID_Customer]
            , s.[ID_DealerConveyor]
            , s.[ID_DobaPronajmu]
            , s.[ID_Projezd]
            , s.[ID_Trailer]
            , s.[ID_User]
            , s.[IDD]
            , s.[LastMonthFree]
            , s.[OdometerEND]
            , s.[OdometerSTART]
            , s.[OverKMchargeCZK]
            , s.[OverKMchargeEUR]
            , s.[RENTend]
            , s.[RENTremark]
            , s.[RENTstart]
            , s.[DataSourceId]
            , @ThreadLogId
            , -1
            , -1
            , N'I' -- insert
        )
        WHEN NOT MATCHED BY SOURCE AND v.[ThreadLogDeleteId] = -1 AND v.[ThreadLogUpdateId] = -1 AND v.[ChangeOperation] <> N'D'
        THEN UPDATE
            SET 
                [ThreadLogDeleteId] = @ThreadLogId
    OUTPUT $ACTION INTO @rowCounts;
    
    INSERT INTO [Vault].[CERTdboRenting] (
            [ID_RENTING]
            , [ContractNo]
            , [CustomerChargeCZK]
            , [CustomerChargeEUR]
            , [DoplatekCZK]
            , [DoplatekEUR]
            , [ID_Customer]
            , [ID_DealerConveyor]
            , [ID_DobaPronajmu]
            , [ID_Projezd]
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
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
        
    ) 
    OUTPUT Inserted.ThreadLogUpdateId INTO @UpdateRowCounts
    SELECT

            s.[ID_RENTING]
            , s.[ContractNo]
            , s.[CustomerChargeCZK]
            , s.[CustomerChargeEUR]
            , s.[DoplatekCZK]
            , s.[DoplatekEUR]
            , s.[ID_Customer]
            , s.[ID_DealerConveyor]
            , s.[ID_DobaPronajmu]
            , s.[ID_Projezd]
            , s.[ID_Trailer]
            , s.[ID_User]
            , s.[IDD]
            , s.[LastMonthFree]
            , s.[OdometerEND]
            , s.[OdometerSTART]
            , s.[OverKMchargeCZK]
            , s.[OverKMchargeEUR]
            , s.[RENTend]
            , s.[RENTremark]
            , s.[RENTstart]
            , s.[DataSourceId]
            , @ThreadLogId
            , -1
            , -1
            , N'U' -- update
    FROM Stage.CERTdboRenting AS s
    INNER JOIN Vault.CERTdboRenting AS v
        ON  s.[ID_RENTING] = v.[ID_RENTING] AND v.ThreadLogUpdateId = @ThreadLogId
    
    INSERT INTO [Vault].[CERTdboRenting] (
            [ID_RENTING]
            , [ContractNo]
            , [CustomerChargeCZK]
            , [CustomerChargeEUR]
            , [DoplatekCZK]
            , [DoplatekEUR]
            , [ID_Customer]
            , [ID_DealerConveyor]
            , [ID_DobaPronajmu]
            , [ID_Projezd]
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
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
            
    ) 
    OUTPUT Inserted.ThreadLogDeleteId INTO @DeleteRowCounts
    SELECT
            v.[ID_RENTING]
            , v.[ContractNo]
            , v.[CustomerChargeCZK]
            , v.[CustomerChargeEUR]
            , v.[DoplatekCZK]
            , v.[DoplatekEUR]
            , v.[ID_Customer]
            , v.[ID_DealerConveyor]
            , v.[ID_DobaPronajmu]
            , v.[ID_Projezd]
            , v.[ID_Trailer]
            , v.[ID_User]
            , v.[IDD]
            , v.[LastMonthFree]
            , v.[OdometerEND]
            , v.[OdometerSTART]
            , v.[OverKMchargeCZK]
            , v.[OverKMchargeEUR]
            , v.[RENTend]
            , v.[RENTremark]
            , v.[RENTstart]
            , v.[DataSourceId]
            , @ThreadLogId
            , -1
            , -1
            , N'D' -- update
    FROM Vault.CERTdboRenting AS v
    WHERE v.ThreadLogDeleteId = @ThreadLogId
    ;

        DECLARE @insertCount int,
                @updateCount int,
                @deleteCount int;

        SELECT @insertCount = COUNT(*) FROM @rowCounts WHERE [MergeAction] = N'INSERT';
        SELECT @updateCount = COUNT(*) FROM @UpdateRowCounts;
        SELECT @deleteCount = COUNT(*) FROM @DeleteRowCounts;


        --Log ThreadLog Success
        UPDATE Etl.ThreadLog
            SET
                UpdateRowCount = @updateCount
                , InsertRowCount = @insertCount
                , DeleteRowCount = @deleteCount
                , TableFinalRowCount = (SELECT COUNT(*) FROM [Vault].[CERTdboRenting] WITH (NOLOCK))
                , EndTime = GETDATE()
                , StatusId = 3      -- Finished
            WHERE ThreadLogId = @ThreadLogId;

        COMMIT TRANSACTION;
    END TRY

    BEGIN CATCH
            EXEC [dbo].[uspErrorHandler] @ThreadLogId = @ThreadLogId;
    END CATCH
```

\[Back to stored procedure list\]\[listofprocedures\]
