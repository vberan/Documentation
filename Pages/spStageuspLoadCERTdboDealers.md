Stored Procedure Stage.uspLoadCERTdboDealers {#spStageuspLoadCERTdboDealers}
--------------------------------------------

Definition of Stored procedure:

``` {.sql}
CREATE PROCEDURE [Stage].[uspLoadCERTdboDealers] 
    @ThreadLogId int
        , @DataSourceId int
    AS
    BEGIN TRY
        -- set up the enviroment
        SET NOCOUNT ON;
    

        TRUNCATE TABLE [Stage].[CERTdboDealers]; 

        -- log the initial table state
        UPDATE Etl.ThreadLog
            SET TableInitialRowCount = (SELECT COUNT(*) FROM [Stage].[CERTdboDealers] WITH (NOLOCK))
        WHERE ThreadLogId = @ThreadLogId;

        DECLARE @loadDateFrom datetime2;
        SELECT @loadDateFrom = '1901-01-01';

        INSERT INTO [Stage].[CERTdboDealers]
            ( 
                [DealerActive]
                , [DealerCity]
                , [DealerCode]
                , [DealerFactCode]
                , [DealerName]
                , [ID_Country]
                , [ID_DealerNr]
                , [ID_DLRtyp]
                , [MailTO]
                , [DataSourceId]
                , [ThreadLogId]
    )

        SELECT 
                [DealerActive] = s.[DealerActive]
                , [DealerCity] = s.[DealerCity]
                , [DealerCode] = s.[DealerCode]
                , [DealerFactCode] = s.[DealerFactCode]
                , [DealerName] = s.[DealerName]
                , [ID_Country] = s.[ID_Country]
                , [ID_DealerNr] = s.[ID_DealerNr]
                , [ID_DLRtyp] = s.[ID_DLRtyp]
                , [MailTO] = s.[MailTO]
                , [DataSourceId] = @DataSourceId
                , [ThreadLogId] = @ThreadLogId
    
        FROM [CERTST10].[CERT].[dbo].[Dealers] AS s WITH (NOLOCK)

        --Log ThreadLog Success
        UPDATE Etl.ThreadLog
        SET ExtractRowCount = (SELECT COUNT(*) FROM [Stage].[CERTdboDealers] WITH (NOLOCK) WHERE ThreadLogId = @ThreadLogId)
            , InsertRowCount = (SELECT COUNT(*) FROM [Stage].[CERTdboDealers] WITH (NOLOCK) WHERE ThreadLogId = @ThreadLogId)
            , TableFinalRowCount = (SELECT COUNT(*) FROM [Stage].[CERTdboDealers] WITH (NOLOCK) )
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
