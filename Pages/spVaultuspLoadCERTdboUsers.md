Stored Procedure Vault.uspLoadCERTdboUsers {#spVaultuspLoadCERTdboUsers}
------------------------------------------

Definition of Stored procedure:

``` {.sql}
CREATE PROCEDURE [Vault].[uspLoadCERTdboUsers] 
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
            SET TableInitialRowCount = (SELECT COUNT(*) FROM [Vault].[CERTdboUsers] WITH (NOLOCK))
        WHERE ThreadLogId = @ThreadLogId;

            BEGIN TRANSACTION;

    
        MERGE INTO [Vault].[CERTdboUsers] AS v
        USING [Stage].[CERTdboUsers] AS s
            ON ( s.[ID_User] = v.[ID_User]AND s.[DataSourceId] = v.[DataSourceId]
     AND v.[ThreadLogDeleteId] = -1 AND v.[ThreadLogUpdateId] = -1 AND v.[ChangeOperation] <> N'D'
    )

        WHEN MATCHED AND
            (
            v.[_ID_UserCAST] <> s.[_ID_UserCAST]
            OR (v.[_ID_UserCAST] IS NULL AND s.[_ID_UserCAST] IS NOT NULL)
        OR (v.[_ID_UserCAST] IS NOT NULL AND s.[_ID_UserCAST] IS NULL)
        OR v.[Approver] <> s.[Approver]
            OR v.[BonusSystemAlowed] <> s.[BonusSystemAlowed]
            OR v.[BranchCode] <> s.[BranchCode]
            OR (v.[BranchCode] IS NULL AND s.[BranchCode] IS NOT NULL)
        OR (v.[BranchCode] IS NOT NULL AND s.[BranchCode] IS NULL)
        OR v.[BUS_Sales] <> s.[BUS_Sales]
            OR v.[DealerModul_Prices] <> s.[DealerModul_Prices]
            OR v.[DistribRights] <> s.[DistribRights]
            OR v.[Email] <> s.[Email]
            OR (v.[Email] IS NULL AND s.[Email] IS NOT NULL)
        OR (v.[Email] IS NOT NULL AND s.[Email] IS NULL)
        OR v.[ID_DealerNr] <> s.[ID_DealerNr]
            OR (v.[ID_DealerNr] IS NULL AND s.[ID_DealerNr] IS NOT NULL)
        OR (v.[ID_DealerNr] IS NOT NULL AND s.[ID_DealerNr] IS NULL)
        OR v.[NT_Sales] <> s.[NT_Sales]
            OR v.[Oslovení] <> s.[Oslovení]
            OR (v.[Oslovení] IS NULL AND s.[Oslovení] IS NOT NULL)
        OR (v.[Oslovení] IS NOT NULL AND s.[Oslovení] IS NULL)
        OR v.[SalesmanCode] <> s.[SalesmanCode]
            OR (v.[SalesmanCode] IS NULL AND s.[SalesmanCode] IS NOT NULL)
        OR (v.[SalesmanCode] IS NOT NULL AND s.[SalesmanCode] IS NULL)
        OR v.[UT_Sales] <> s.[UT_Sales]
            OR v.[UV_ModificationAlowed] <> s.[UV_ModificationAlowed]
            OR v.[Uzivatel] <> s.[Uzivatel]
            OR (v.[Uzivatel] IS NULL AND s.[Uzivatel] IS NOT NULL)
        OR (v.[Uzivatel] IS NOT NULL AND s.[Uzivatel] IS NULL)
        OR v.[Uzivatel_Jmeno] <> s.[Uzivatel_Jmeno]
            OR (v.[Uzivatel_Jmeno] IS NULL AND s.[Uzivatel_Jmeno] IS NOT NULL)
        OR (v.[Uzivatel_Jmeno] IS NOT NULL AND s.[Uzivatel_Jmeno] IS NULL)
        OR v.[Uzivatel_Prijmeni] <> s.[Uzivatel_Prijmeni]
            OR (v.[Uzivatel_Prijmeni] IS NULL AND s.[Uzivatel_Prijmeni] IS NOT NULL)
        OR (v.[Uzivatel_Prijmeni] IS NOT NULL AND s.[Uzivatel_Prijmeni] IS NULL)
        )
        THEN 
            UPDATE SET
                [ThreadLogUpdateId] = @ThreadLogId
            

                
        WHEN NOT MATCHED BY TARGET 
            THEN INSERT
            ( 
            [ID_User]
            , [_ID_UserCAST]
            , [Approver]
            , [BonusSystemAlowed]
            , [BranchCode]
            , [BUS_Sales]
            , [DealerModul_Prices]
            , [DistribRights]
            , [Email]
            , [ID_DealerNr]
            , [NT_Sales]
            , [Oslovení]
            , [SalesmanCode]
            , [UT_Sales]
            , [UV_ModificationAlowed]
            , [Uzivatel]
            , [Uzivatel_Jmeno]
            , [Uzivatel_Prijmeni]
            , [DataSourceId]
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
            
    ) VALUES (
            s.[ID_User]
            , s.[_ID_UserCAST]
            , s.[Approver]
            , s.[BonusSystemAlowed]
            , s.[BranchCode]
            , s.[BUS_Sales]
            , s.[DealerModul_Prices]
            , s.[DistribRights]
            , s.[Email]
            , s.[ID_DealerNr]
            , s.[NT_Sales]
            , s.[Oslovení]
            , s.[SalesmanCode]
            , s.[UT_Sales]
            , s.[UV_ModificationAlowed]
            , s.[Uzivatel]
            , s.[Uzivatel_Jmeno]
            , s.[Uzivatel_Prijmeni]
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
    
    INSERT INTO [Vault].[CERTdboUsers] (
            [ID_User]
            , [_ID_UserCAST]
            , [Approver]
            , [BonusSystemAlowed]
            , [BranchCode]
            , [BUS_Sales]
            , [DealerModul_Prices]
            , [DistribRights]
            , [Email]
            , [ID_DealerNr]
            , [NT_Sales]
            , [Oslovení]
            , [SalesmanCode]
            , [UT_Sales]
            , [UV_ModificationAlowed]
            , [Uzivatel]
            , [Uzivatel_Jmeno]
            , [Uzivatel_Prijmeni]
            , [DataSourceId]
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
        
    ) 
    OUTPUT Inserted.ThreadLogUpdateId INTO @UpdateRowCounts
    SELECT

            s.[ID_User]
            , s.[_ID_UserCAST]
            , s.[Approver]
            , s.[BonusSystemAlowed]
            , s.[BranchCode]
            , s.[BUS_Sales]
            , s.[DealerModul_Prices]
            , s.[DistribRights]
            , s.[Email]
            , s.[ID_DealerNr]
            , s.[NT_Sales]
            , s.[Oslovení]
            , s.[SalesmanCode]
            , s.[UT_Sales]
            , s.[UV_ModificationAlowed]
            , s.[Uzivatel]
            , s.[Uzivatel_Jmeno]
            , s.[Uzivatel_Prijmeni]
            , s.[DataSourceId]
            , @ThreadLogId
            , -1
            , -1
            , N'U' -- update
    FROM Stage.CERTdboUsers AS s
    INNER JOIN Vault.CERTdboUsers AS v
        ON  s.[ID_User] = v.[ID_User] AND v.ThreadLogUpdateId = @ThreadLogId
    
    INSERT INTO [Vault].[CERTdboUsers] (
            [ID_User]
            , [_ID_UserCAST]
            , [Approver]
            , [BonusSystemAlowed]
            , [BranchCode]
            , [BUS_Sales]
            , [DealerModul_Prices]
            , [DistribRights]
            , [Email]
            , [ID_DealerNr]
            , [NT_Sales]
            , [Oslovení]
            , [SalesmanCode]
            , [UT_Sales]
            , [UV_ModificationAlowed]
            , [Uzivatel]
            , [Uzivatel_Jmeno]
            , [Uzivatel_Prijmeni]
            , [DataSourceId]
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
            
    ) 
    OUTPUT Inserted.ThreadLogDeleteId INTO @DeleteRowCounts
    SELECT
            v.[ID_User]
            , v.[_ID_UserCAST]
            , v.[Approver]
            , v.[BonusSystemAlowed]
            , v.[BranchCode]
            , v.[BUS_Sales]
            , v.[DealerModul_Prices]
            , v.[DistribRights]
            , v.[Email]
            , v.[ID_DealerNr]
            , v.[NT_Sales]
            , v.[Oslovení]
            , v.[SalesmanCode]
            , v.[UT_Sales]
            , v.[UV_ModificationAlowed]
            , v.[Uzivatel]
            , v.[Uzivatel_Jmeno]
            , v.[Uzivatel_Prijmeni]
            , v.[DataSourceId]
            , @ThreadLogId
            , -1
            , -1
            , N'D' -- update
    FROM Vault.CERTdboUsers AS v
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
                , TableFinalRowCount = (SELECT COUNT(*) FROM [Vault].[CERTdboUsers] WITH (NOLOCK))
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
