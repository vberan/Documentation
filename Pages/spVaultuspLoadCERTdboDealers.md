Stored Procedure Vault.uspLoadCERTdboDealers {#spVaultuspLoadCERTdboDealers}
--------------------------------------------

Definition of Stored procedure:

``` {.sql}
CREATE PROCEDURE [Vault].[uspLoadCERTdboDealers] 
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
            SET TableInitialRowCount = (SELECT COUNT(*) FROM [Vault].[CERTdboDealers] WITH (NOLOCK))
        WHERE ThreadLogId = @ThreadLogId;

            BEGIN TRANSACTION;

    
        MERGE INTO [Vault].[CERTdboDealers] AS v
        USING [Stage].[CERTdboDealers] AS s
            ON ( s.[ID_DealerNr] = v.[ID_DealerNr]AND s.[DataSourceId] = v.[DataSourceId]
     AND v.[ThreadLogDeleteId] = -1 AND v.[ThreadLogUpdateId] = -1 AND v.[ChangeOperation] <> N'D'
    )

        WHEN MATCHED AND
            (
            v.[DealerActive] <> s.[DealerActive]
            OR v.[DealerCity] <> s.[DealerCity]
            OR (v.[DealerCity] IS NULL AND s.[DealerCity] IS NOT NULL)
        OR (v.[DealerCity] IS NOT NULL AND s.[DealerCity] IS NULL)
        OR v.[DealerCode] <> s.[DealerCode]
            OR (v.[DealerCode] IS NULL AND s.[DealerCode] IS NOT NULL)
        OR (v.[DealerCode] IS NOT NULL AND s.[DealerCode] IS NULL)
        OR v.[DealerFactCode] <> s.[DealerFactCode]
            OR (v.[DealerFactCode] IS NULL AND s.[DealerFactCode] IS NOT NULL)
        OR (v.[DealerFactCode] IS NOT NULL AND s.[DealerFactCode] IS NULL)
        OR v.[DealerName] <> s.[DealerName]
            OR (v.[DealerName] IS NULL AND s.[DealerName] IS NOT NULL)
        OR (v.[DealerName] IS NOT NULL AND s.[DealerName] IS NULL)
        OR v.[ID_Country] <> s.[ID_Country]
            OR (v.[ID_Country] IS NULL AND s.[ID_Country] IS NOT NULL)
        OR (v.[ID_Country] IS NOT NULL AND s.[ID_Country] IS NULL)
        OR v.[ID_DLRtyp] <> s.[ID_DLRtyp]
            OR (v.[ID_DLRtyp] IS NULL AND s.[ID_DLRtyp] IS NOT NULL)
        OR (v.[ID_DLRtyp] IS NOT NULL AND s.[ID_DLRtyp] IS NULL)
        OR v.[MailTO] <> s.[MailTO]
            OR (v.[MailTO] IS NULL AND s.[MailTO] IS NOT NULL)
        OR (v.[MailTO] IS NOT NULL AND s.[MailTO] IS NULL)
        )
        THEN 
            UPDATE SET
                [ThreadLogUpdateId] = @ThreadLogId
            

                
        WHEN NOT MATCHED BY TARGET 
            THEN INSERT
            ( 
            [ID_DealerNr]
            , [DealerActive]
            , [DealerCity]
            , [DealerCode]
            , [DealerFactCode]
            , [DealerName]
            , [ID_Country]
            , [ID_DLRtyp]
            , [MailTO]
            , [DataSourceId]
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
            
    ) VALUES (
            s.[ID_DealerNr]
            , s.[DealerActive]
            , s.[DealerCity]
            , s.[DealerCode]
            , s.[DealerFactCode]
            , s.[DealerName]
            , s.[ID_Country]
            , s.[ID_DLRtyp]
            , s.[MailTO]
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
    
    INSERT INTO [Vault].[CERTdboDealers] (
            [ID_DealerNr]
            , [DealerActive]
            , [DealerCity]
            , [DealerCode]
            , [DealerFactCode]
            , [DealerName]
            , [ID_Country]
            , [ID_DLRtyp]
            , [MailTO]
            , [DataSourceId]
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
        
    ) 
    OUTPUT Inserted.ThreadLogUpdateId INTO @UpdateRowCounts
    SELECT

            s.[ID_DealerNr]
            , s.[DealerActive]
            , s.[DealerCity]
            , s.[DealerCode]
            , s.[DealerFactCode]
            , s.[DealerName]
            , s.[ID_Country]
            , s.[ID_DLRtyp]
            , s.[MailTO]
            , s.[DataSourceId]
            , @ThreadLogId
            , -1
            , -1
            , N'U' -- update
    FROM Stage.CERTdboDealers AS s
    INNER JOIN Vault.CERTdboDealers AS v
        ON  s.[ID_DealerNr] = v.[ID_DealerNr] AND v.ThreadLogUpdateId = @ThreadLogId
    
    INSERT INTO [Vault].[CERTdboDealers] (
            [ID_DealerNr]
            , [DealerActive]
            , [DealerCity]
            , [DealerCode]
            , [DealerFactCode]
            , [DealerName]
            , [ID_Country]
            , [ID_DLRtyp]
            , [MailTO]
            , [DataSourceId]
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
            
    ) 
    OUTPUT Inserted.ThreadLogDeleteId INTO @DeleteRowCounts
    SELECT
            v.[ID_DealerNr]
            , v.[DealerActive]
            , v.[DealerCity]
            , v.[DealerCode]
            , v.[DealerFactCode]
            , v.[DealerName]
            , v.[ID_Country]
            , v.[ID_DLRtyp]
            , v.[MailTO]
            , v.[DataSourceId]
            , @ThreadLogId
            , -1
            , -1
            , N'D' -- update
    FROM Vault.CERTdboDealers AS v
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
                , TableFinalRowCount = (SELECT COUNT(*) FROM [Vault].[CERTdboDealers] WITH (NOLOCK))
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
