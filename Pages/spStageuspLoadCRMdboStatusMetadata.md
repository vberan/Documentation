Stored Procedure Stage.uspLoadCRMdboStatusMetadata {#spStageuspLoadCRMdboStatusMetadata}
--------------------------------------------------

Definition of Stored procedure:

``` {.sql}
CREATE PROCEDURE [Stage].[uspLoadCRMdboStatusMetadata] 
    @ThreadLogId int
        , @DataSourceId int
    AS
    BEGIN TRY
        -- set up the enviroment
        SET NOCOUNT ON;
    

        TRUNCATE TABLE [Stage].[CRMdboStatusMetadata]; 

        -- log the initial table state
        UPDATE Etl.ThreadLog
            SET TableInitialRowCount = (SELECT COUNT(*) FROM [Stage].[CRMdboStatusMetadata] WITH (NOLOCK))
        WHERE ThreadLogId = @ThreadLogId;

        DECLARE @loadDateFrom datetime2;
        SELECT @loadDateFrom = '1901-01-01';

        INSERT INTO [Stage].[CRMdboStatusMetadata]
            ( 
                [EntityName]
                , [IsUserLocalizedLabel]
                , [LocalizedLabel]
                , [LocalizedLabelLanguageCode]
                , [State]
                , [Status]
                , [DataSourceId]
                , [ThreadLogId]
    )

        SELECT 
                [EntityName] = s.[EntityName]
                , [IsUserLocalizedLabel] = s.[IsUserLocalizedLabel]
                , [LocalizedLabel] = s.[LocalizedLabel]
                , [LocalizedLabelLanguageCode] = s.[LocalizedLabelLanguageCode]
                , [State] = s.[State]
                , [Status] = s.[Status]
                , [DataSourceId] = @DataSourceId
                , [ThreadLogId] = @ThreadLogId
    
        FROM [scaniacrmexport.database.windows.net].[ScaniaCRMExport].[dbo].[StatusMetadata] AS s WITH (NOLOCK)

        --Log ThreadLog Success
        UPDATE Etl.ThreadLog
        SET ExtractRowCount = (SELECT COUNT(*) FROM [Stage].[CRMdboStatusMetadata] WITH (NOLOCK) WHERE ThreadLogId = @ThreadLogId)
            , InsertRowCount = (SELECT COUNT(*) FROM [Stage].[CRMdboStatusMetadata] WITH (NOLOCK) WHERE ThreadLogId = @ThreadLogId)
            , TableFinalRowCount = (SELECT COUNT(*) FROM [Stage].[CRMdboStatusMetadata] WITH (NOLOCK) )
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
