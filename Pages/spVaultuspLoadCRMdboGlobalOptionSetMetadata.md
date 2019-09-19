Stored Procedure Vault.uspLoadCRMdboGlobalOptionSetMetadata {#spVaultuspLoadCRMdboGlobalOptionSetMetadata}
-----------------------------------------------------------

Definition of Stored procedure:

``` {.sql}
CREATE PROCEDURE [Vault].[uspLoadCRMdboGlobalOptionSetMetadata] 
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
            SET TableInitialRowCount = (SELECT COUNT(*) FROM [Vault].[CRMdboGlobalOptionSetMetadata] WITH (NOLOCK))
        WHERE ThreadLogId = @ThreadLogId;

            BEGIN TRANSACTION;

    
        MERGE INTO [Vault].[CRMdboGlobalOptionSetMetadata] AS v
        USING [Stage].[CRMdboGlobalOptionSetMetadata] AS s
            ON ( s.[IsUserLocalizedLabel] = v.[IsUserLocalizedLabel] AND s.[LocalizedLabelLanguageCode] = v.[LocalizedLabelLanguageCode] AND s.[Option] = v.[Option] AND s.[OptionSetName] = v.[OptionSetName]AND s.[DataSourceId] = v.[DataSourceId]
     AND v.[ThreadLogDeleteId] = -1 AND v.[ThreadLogUpdateId] = -1 AND v.[ChangeOperation] <> N'D'
    )

        WHEN MATCHED AND
            (
            v.[LocalizedLabel] <> s.[LocalizedLabel]
            OR (v.[LocalizedLabel] IS NULL AND s.[LocalizedLabel] IS NOT NULL)
        OR (v.[LocalizedLabel] IS NOT NULL AND s.[LocalizedLabel] IS NULL)
        )
        THEN 
            UPDATE SET
                [ThreadLogUpdateId] = @ThreadLogId
            

                
        WHEN NOT MATCHED BY TARGET 
            THEN INSERT
            ( 
            [IsUserLocalizedLabel]
            , [LocalizedLabelLanguageCode]
            , [Option]
            , [OptionSetName]
            , [LocalizedLabel]
            , [DataSourceId]
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
            
    ) VALUES (
            s.[IsUserLocalizedLabel]
            , s.[LocalizedLabelLanguageCode]
            , s.[Option]
            , s.[OptionSetName]
            , s.[LocalizedLabel]
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
    
    INSERT INTO [Vault].[CRMdboGlobalOptionSetMetadata] (
            [IsUserLocalizedLabel]
            , [LocalizedLabelLanguageCode]
            , [Option]
            , [OptionSetName]
            , [LocalizedLabel]
            , [DataSourceId]
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
        
    ) 
    OUTPUT Inserted.ThreadLogUpdateId INTO @UpdateRowCounts
    SELECT

            s.[IsUserLocalizedLabel]
            , s.[LocalizedLabelLanguageCode]
            , s.[Option]
            , s.[OptionSetName]
            , s.[LocalizedLabel]
            , s.[DataSourceId]
            , @ThreadLogId
            , -1
            , -1
            , N'U' -- update
    FROM Stage.CRMdboGlobalOptionSetMetadata AS s
    INNER JOIN Vault.CRMdboGlobalOptionSetMetadata AS v
        ON  s.[IsUserLocalizedLabel] = v.[IsUserLocalizedLabel] AND s.[LocalizedLabelLanguageCode] = v.[LocalizedLabelLanguageCode] AND s.[Option] = v.[Option] AND s.[OptionSetName] = v.[OptionSetName] AND v.ThreadLogUpdateId = @ThreadLogId
    
    INSERT INTO [Vault].[CRMdboGlobalOptionSetMetadata] (
            [IsUserLocalizedLabel]
            , [LocalizedLabelLanguageCode]
            , [Option]
            , [OptionSetName]
            , [LocalizedLabel]
            , [DataSourceId]
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
            
    ) 
    OUTPUT Inserted.ThreadLogDeleteId INTO @DeleteRowCounts
    SELECT
            v.[IsUserLocalizedLabel]
            , v.[LocalizedLabelLanguageCode]
            , v.[Option]
            , v.[OptionSetName]
            , v.[LocalizedLabel]
            , v.[DataSourceId]
            , @ThreadLogId
            , -1
            , -1
            , N'D' -- update
    FROM Vault.CRMdboGlobalOptionSetMetadata AS v
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
                , TableFinalRowCount = (SELECT COUNT(*) FROM [Vault].[CRMdboGlobalOptionSetMetadata] WITH (NOLOCK))
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
