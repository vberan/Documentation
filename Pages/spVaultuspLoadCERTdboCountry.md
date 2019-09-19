Stored Procedure Vault.uspLoadCERTdboCountry {#spVaultuspLoadCERTdboCountry}
--------------------------------------------

Definition of Stored procedure:

``` {.sql}
CREATE PROCEDURE [Vault].[uspLoadCERTdboCountry] 
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
            SET TableInitialRowCount = (SELECT COUNT(*) FROM [Vault].[CERTdboCountry] WITH (NOLOCK))
        WHERE ThreadLogId = @ThreadLogId;

            BEGIN TRANSACTION;

    
        MERGE INTO [Vault].[CERTdboCountry] AS v
        USING [Stage].[CERTdboCountry] AS s
            ON ( s.[ID_Country] = v.[ID_Country]AND s.[DataSourceId] = v.[DataSourceId]
     AND v.[ThreadLogDeleteId] = -1 AND v.[ThreadLogUpdateId] = -1 AND v.[ChangeOperation] <> N'D'
    )

        WHEN MATCHED AND
            (
            v.[Country] <> s.[Country]
            OR (v.[Country] IS NULL AND s.[Country] IS NOT NULL)
        OR (v.[Country] IS NOT NULL AND s.[Country] IS NULL)
        OR v.[CountryCode] <> s.[CountryCode]
            OR (v.[CountryCode] IS NULL AND s.[CountryCode] IS NOT NULL)
        OR (v.[CountryCode] IS NOT NULL AND s.[CountryCode] IS NULL)
        )
        THEN 
            UPDATE SET
                [ThreadLogUpdateId] = @ThreadLogId
            

                
        WHEN NOT MATCHED BY TARGET 
            THEN INSERT
            ( 
            [ID_Country]
            , [Country]
            , [CountryCode]
            , [Flag]
            , [DataSourceId]
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
            
    ) VALUES (
            s.[ID_Country]
            , s.[Country]
            , s.[CountryCode]
            , s.[Flag]
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
    
    INSERT INTO [Vault].[CERTdboCountry] (
            [ID_Country]
            , [Country]
            , [CountryCode]
            , [Flag]
            , [DataSourceId]
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
        
    ) 
    OUTPUT Inserted.ThreadLogUpdateId INTO @UpdateRowCounts
    SELECT

            s.[ID_Country]
            , s.[Country]
            , s.[CountryCode]
            , s.[Flag]
            , s.[DataSourceId]
            , @ThreadLogId
            , -1
            , -1
            , N'U' -- update
    FROM Stage.CERTdboCountry AS s
    INNER JOIN Vault.CERTdboCountry AS v
        ON  s.[ID_Country] = v.[ID_Country] AND v.ThreadLogUpdateId = @ThreadLogId
    
    INSERT INTO [Vault].[CERTdboCountry] (
            [ID_Country]
            , [Country]
            , [CountryCode]
            , [Flag]
            , [DataSourceId]
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
            
    ) 
    OUTPUT Inserted.ThreadLogDeleteId INTO @DeleteRowCounts
    SELECT
            v.[ID_Country]
            , v.[Country]
            , v.[CountryCode]
            , v.[Flag]
            , v.[DataSourceId]
            , @ThreadLogId
            , -1
            , -1
            , N'D' -- update
    FROM Vault.CERTdboCountry AS v
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
                , TableFinalRowCount = (SELECT COUNT(*) FROM [Vault].[CERTdboCountry] WITH (NOLOCK))
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
