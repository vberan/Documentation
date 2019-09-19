Stored Procedure Stage.uspLoadCRMdboOptionSetMetadata {#spStageuspLoadCRMdboOptionSetMetadata}
-----------------------------------------------------

Definition of Stored procedure:

``` {.sql}
CREATE PROCEDURE [Stage].[uspLoadCRMdboOptionSetMetadata] 
    @ThreadLogId int
        , @DataSourceId int
    AS
    BEGIN TRY
        -- set up the enviroment
        SET NOCOUNT ON;
    

        TRUNCATE TABLE [Stage].[CRMdboOptionSetMetadata]; 

        -- log the initial table state
        UPDATE Etl.ThreadLog
            SET TableInitialRowCount = (SELECT COUNT(*) FROM [Stage].[CRMdboOptionSetMetadata] WITH (NOLOCK))
        WHERE ThreadLogId = @ThreadLogId;

        DECLARE @loadDateFrom datetime2;
        SELECT @loadDateFrom = '1901-01-01';

        INSERT INTO [Stage].[CRMdboOptionSetMetadata]
            ( 
                [EntityName]
                , [IsUserLocalizedLabel]
                , [LocalizedLabel]
                , [LocalizedLabelLanguageCode]
                , [Option]
                , [OptionSetName]
                , [DataSourceId]
                , [ThreadLogId]
    )

        SELECT 
                [EntityName] = s.[EntityName]
                , [IsUserLocalizedLabel] = s.[IsUserLocalizedLabel]
                , [LocalizedLabel] = s.[LocalizedLabel]
                , [LocalizedLabelLanguageCode] = s.[LocalizedLabelLanguageCode]
                , [Option] = s.[Option]
                , [OptionSetName] = s.[OptionSetName]
                , [DataSourceId] = @DataSourceId
                , [ThreadLogId] = @ThreadLogId
    
        FROM [scaniacrmexport.database.windows.net].[ScaniaCRMExport].[dbo].[OptionSetMetadata] AS s WITH (NOLOCK)

        --Log ThreadLog Success
        UPDATE Etl.ThreadLog
        SET ExtractRowCount = (SELECT COUNT(*) FROM [Stage].[CRMdboOptionSetMetadata] WITH (NOLOCK) WHERE ThreadLogId = @ThreadLogId)
            , InsertRowCount = (SELECT COUNT(*) FROM [Stage].[CRMdboOptionSetMetadata] WITH (NOLOCK) WHERE ThreadLogId = @ThreadLogId)
            , TableFinalRowCount = (SELECT COUNT(*) FROM [Stage].[CRMdboOptionSetMetadata] WITH (NOLOCK) )
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
