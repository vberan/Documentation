Stored Procedure Vault.uspLoadCRMdboStatusMetadata {#spVaultuspLoadCRMdboStatusMetadata}
--------------------------------------------------

Definition of Stored procedure:

``` {.sql}
CREATE PROCEDURE [Vault].[uspLoadCRMdboStatusMetadata] 
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
            SET TableInitialRowCount = (SELECT COUNT(*) FROM [Vault].[CRMdboStatusMetadata] WITH (NOLOCK))
        WHERE ThreadLogId = @ThreadLogId;

            BEGIN TRANSACTION;

    
        MERGE INTO [Vault].[CRMdboStatusMetadata] AS v
        USING [Stage].[CRMdboStatusMetadata] AS s
            ON ( s.[EntityName] = v.[EntityName] AND s.[IsUserLocalizedLabel] = v.[IsUserLocalizedLabel] AND s.[LocalizedLabelLanguageCode] = v.[LocalizedLabelLanguageCode] AND s.[State] = v.[State] AND s.[Status] = v.[Status]AND s.[DataSourceId] = v.[DataSourceId]
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
            [EntityName]
            , [IsUserLocalizedLabel]
            , [LocalizedLabelLanguageCode]
            , [State]
            , [Status]
            , [LocalizedLabel]
            , [DataSourceId]
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
            
    ) VALUES (
            s.[EntityName]
            , s.[IsUserLocalizedLabel]
            , s.[LocalizedLabelLanguageCode]
            , s.[State]
            , s.[Status]
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
    
    INSERT INTO [Vault].[CRMdboStatusMetadata] (
            [EntityName]
            , [IsUserLocalizedLabel]
            , [LocalizedLabelLanguageCode]
            , [State]
            , [Status]
            , [LocalizedLabel]
            , [DataSourceId]
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
        
    ) 
    OUTPUT Inserted.ThreadLogUpdateId INTO @UpdateRowCounts
    SELECT

            s.[EntityName]
            , s.[IsUserLocalizedLabel]
            , s.[LocalizedLabelLanguageCode]
            , s.[State]
            , s.[Status]
            , s.[LocalizedLabel]
            , s.[DataSourceId]
            , @ThreadLogId
            , -1
            , -1
            , N'U' -- update
    FROM Stage.CRMdboStatusMetadata AS s
    INNER JOIN Vault.CRMdboStatusMetadata AS v
        ON  s.[EntityName] = v.[EntityName] AND s.[IsUserLocalizedLabel] = v.[IsUserLocalizedLabel] AND s.[LocalizedLabelLanguageCode] = v.[LocalizedLabelLanguageCode] AND s.[State] = v.[State] AND s.[Status] = v.[Status] AND v.ThreadLogUpdateId = @ThreadLogId
    
    INSERT INTO [Vault].[CRMdboStatusMetadata] (
            [EntityName]
            , [IsUserLocalizedLabel]
            , [LocalizedLabelLanguageCode]
            , [State]
            , [Status]
            , [LocalizedLabel]
            , [DataSourceId]
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
            
    ) 
    OUTPUT Inserted.ThreadLogDeleteId INTO @DeleteRowCounts
    SELECT
            v.[EntityName]
            , v.[IsUserLocalizedLabel]
            , v.[LocalizedLabelLanguageCode]
            , v.[State]
            , v.[Status]
            , v.[LocalizedLabel]
            , v.[DataSourceId]
            , @ThreadLogId
            , -1
            , -1
            , N'D' -- update
    FROM Vault.CRMdboStatusMetadata AS v
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
                , TableFinalRowCount = (SELECT COUNT(*) FROM [Vault].[CRMdboStatusMetadata] WITH (NOLOCK))
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
