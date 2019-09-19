Stored Procedure Stage.uspLoadCERTdboUsers {#spStageuspLoadCERTdboUsers}
------------------------------------------

Definition of Stored procedure:

``` {.sql}
CREATE PROCEDURE [Stage].[uspLoadCERTdboUsers] 
    @ThreadLogId int
        , @DataSourceId int
    AS
    BEGIN TRY
        -- set up the enviroment
        SET NOCOUNT ON;
    

        TRUNCATE TABLE [Stage].[CERTdboUsers]; 

        -- log the initial table state
        UPDATE Etl.ThreadLog
            SET TableInitialRowCount = (SELECT COUNT(*) FROM [Stage].[CERTdboUsers] WITH (NOLOCK))
        WHERE ThreadLogId = @ThreadLogId;

        DECLARE @loadDateFrom datetime2;
        SELECT @loadDateFrom = '1901-01-01';

        INSERT INTO [Stage].[CERTdboUsers]
            ( 
                [_ID_UserCAST]
                , [Approver]
                , [BonusSystemAlowed]
                , [BranchCode]
                , [BUS_Sales]
                , [DealerModul_Prices]
                , [DistribRights]
                , [Email]
                , [ID_DealerNr]
                , [ID_User]
                , [NT_Sales]
                , [Oslovení]
                , [SalesmanCode]
                , [UT_Sales]
                , [UV_ModificationAlowed]
                , [Uzivatel]
                , [Uzivatel_Jmeno]
                , [Uzivatel_Prijmeni]
                , [DataSourceId]
                , [ThreadLogId]
    )

        SELECT 
                [_ID_UserCAST] = s.[_ID_UserCAST]
                , [Approver] = s.[Approver]
                , [BonusSystemAlowed] = s.[BonusSystemAlowed]
                , [BranchCode] = s.[BranchCode]
                , [BUS_Sales] = s.[BUS_Sales]
                , [DealerModul_Prices] = s.[DealerModul_Prices]
                , [DistribRights] = s.[DistribRights]
                , [Email] = s.[Email]
                , [ID_DealerNr] = s.[ID_DealerNr]
                , [ID_User] = s.[ID_User]
                , [NT_Sales] = s.[NT_Sales]
                , [Oslovení] = s.[Oslovení]
                , [SalesmanCode] = s.[SalesmanCode]
                , [UT_Sales] = s.[UT_Sales]
                , [UV_ModificationAlowed] = s.[UV_ModificationAlowed]
                , [Uzivatel] = s.[Uzivatel]
                , [Uzivatel_Jmeno] = s.[Uzivatel_Jmeno]
                , [Uzivatel_Prijmeni] = s.[Uzivatel_Prijmeni]
                , [DataSourceId] = @DataSourceId
                , [ThreadLogId] = @ThreadLogId
    
        FROM [CERTST10].[CERT].[dbo].[Users] AS s WITH (NOLOCK)

        --Log ThreadLog Success
        UPDATE Etl.ThreadLog
        SET ExtractRowCount = (SELECT COUNT(*) FROM [Stage].[CERTdboUsers] WITH (NOLOCK) WHERE ThreadLogId = @ThreadLogId)
            , InsertRowCount = (SELECT COUNT(*) FROM [Stage].[CERTdboUsers] WITH (NOLOCK) WHERE ThreadLogId = @ThreadLogId)
            , TableFinalRowCount = (SELECT COUNT(*) FROM [Stage].[CERTdboUsers] WITH (NOLOCK) )
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
