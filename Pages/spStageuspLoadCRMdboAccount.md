Stored Procedure Stage.uspLoadCRMdboAccount {#spStageuspLoadCRMdboAccount}
-------------------------------------------

Definition of Stored procedure:

``` {.sql}
CREATE PROCEDURE [Stage].[uspLoadCRMdboAccount] 
    @ThreadLogId int
        , @DataSourceId int
    AS
    BEGIN TRY
        -- set up the enviroment
        SET NOCOUNT ON;
    

        TRUNCATE TABLE [Stage].[CRMdboAccount]; 

        -- log the initial table state
        UPDATE Etl.ThreadLog
            SET TableInitialRowCount = (SELECT COUNT(*) FROM [Stage].[CRMdboAccount] WITH (NOLOCK))
        WHERE ThreadLogId = @ThreadLogId;

        DECLARE @loadDateFrom datetime2;
        SELECT @loadDateFrom = '1901-01-01';

        INSERT INTO [Stage].[CRMdboAccount]
            ( 
                [accountcategorycode]
                , [accountid]
                , [address1_city]
                , [address2_city]
                , [Id]
                , [llp_cantonid]
                , [llp_cantondid]
                , [llp_promisingas]
                , [llp_promisingnv]
                , [llp_respactivesalesid]
                , [llp_respnewvehiclesid]
                , [llp_vatnumber]
                , [name]
                , [ownerid]
                , [owningbusinessunit]
                , [statecode]
                , [wa_registrationnumber]
                , [DataSourceId]
                , [ThreadLogId]
    )

        SELECT 
                [accountcategorycode] = s.[accountcategorycode]
                , [accountid] = s.[accountid]
                , [address1_city] = s.[address1_city]
                , [address2_city] = s.[address2_city]
                , [Id] = s.[Id]
                , [llp_cantonid] = s.[llp_cantonid]
                , [llp_cantondid] = s.[llp_cantondid]
                , [llp_promisingas] = s.[llp_promisingas]
                , [llp_promisingnv] = s.[llp_promisingnv]
                , [llp_respactivesalesid] = s.[llp_respactivesalesid]
                , [llp_respnewvehiclesid] = s.[llp_respnewvehiclesid]
                , [llp_vatnumber] = s.[llp_vatnumber]
                , [name] = s.[name]
                , [ownerid] = s.[ownerid]
                , [owningbusinessunit] = s.[owningbusinessunit]
                , [statecode] = s.[statecode]
                , [wa_registrationnumber] = s.[wa_registrationnumber]
                , [DataSourceId] = @DataSourceId
                , [ThreadLogId] = @ThreadLogId
    
        FROM [scaniacrmexport.database.windows.net].[ScaniaCRMExport].[dbo].[account] AS s WITH (NOLOCK)

        --Log ThreadLog Success
        UPDATE Etl.ThreadLog
        SET ExtractRowCount = (SELECT COUNT(*) FROM [Stage].[CRMdboAccount] WITH (NOLOCK) WHERE ThreadLogId = @ThreadLogId)
            , InsertRowCount = (SELECT COUNT(*) FROM [Stage].[CRMdboAccount] WITH (NOLOCK) WHERE ThreadLogId = @ThreadLogId)
            , TableFinalRowCount = (SELECT COUNT(*) FROM [Stage].[CRMdboAccount] WITH (NOLOCK) )
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
