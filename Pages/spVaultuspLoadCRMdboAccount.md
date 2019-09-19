Stored Procedure Vault.uspLoadCRMdboAccount {#spVaultuspLoadCRMdboAccount}
-------------------------------------------

Definition of Stored procedure:

``` {.sql}
CREATE PROCEDURE [Vault].[uspLoadCRMdboAccount] 
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
            SET TableInitialRowCount = (SELECT COUNT(*) FROM [Vault].[CRMdboAccount] WITH (NOLOCK))
        WHERE ThreadLogId = @ThreadLogId;

            BEGIN TRANSACTION;

    
        MERGE INTO [Vault].[CRMdboAccount] AS v
        USING [Stage].[CRMdboAccount] AS s
            ON ( s.[Id] = v.[Id]AND s.[DataSourceId] = v.[DataSourceId]
     AND v.[ThreadLogDeleteId] = -1 AND v.[ThreadLogUpdateId] = -1 AND v.[ChangeOperation] <> N'D'
    )

        WHEN MATCHED AND
            (
            v.[accountcategorycode] <> s.[accountcategorycode]
            OR (v.[accountcategorycode] IS NULL AND s.[accountcategorycode] IS NOT NULL)
        OR (v.[accountcategorycode] IS NOT NULL AND s.[accountcategorycode] IS NULL)
        OR v.[accountid] <> s.[accountid]
            OR (v.[accountid] IS NULL AND s.[accountid] IS NOT NULL)
        OR (v.[accountid] IS NOT NULL AND s.[accountid] IS NULL)
        OR v.[address1_city] <> s.[address1_city]
            OR (v.[address1_city] IS NULL AND s.[address1_city] IS NOT NULL)
        OR (v.[address1_city] IS NOT NULL AND s.[address1_city] IS NULL)
        OR v.[address2_city] <> s.[address2_city]
            OR (v.[address2_city] IS NULL AND s.[address2_city] IS NOT NULL)
        OR (v.[address2_city] IS NOT NULL AND s.[address2_city] IS NULL)
        OR v.[llp_cantonid] <> s.[llp_cantonid]
            OR (v.[llp_cantonid] IS NULL AND s.[llp_cantonid] IS NOT NULL)
        OR (v.[llp_cantonid] IS NOT NULL AND s.[llp_cantonid] IS NULL)
        OR v.[llp_cantondid] <> s.[llp_cantondid]
            OR (v.[llp_cantondid] IS NULL AND s.[llp_cantondid] IS NOT NULL)
        OR (v.[llp_cantondid] IS NOT NULL AND s.[llp_cantondid] IS NULL)
        OR v.[llp_promisingas] <> s.[llp_promisingas]
            OR (v.[llp_promisingas] IS NULL AND s.[llp_promisingas] IS NOT NULL)
        OR (v.[llp_promisingas] IS NOT NULL AND s.[llp_promisingas] IS NULL)
        OR v.[llp_promisingnv] <> s.[llp_promisingnv]
            OR (v.[llp_promisingnv] IS NULL AND s.[llp_promisingnv] IS NOT NULL)
        OR (v.[llp_promisingnv] IS NOT NULL AND s.[llp_promisingnv] IS NULL)
        OR v.[llp_respactivesalesid] <> s.[llp_respactivesalesid]
            OR (v.[llp_respactivesalesid] IS NULL AND s.[llp_respactivesalesid] IS NOT NULL)
        OR (v.[llp_respactivesalesid] IS NOT NULL AND s.[llp_respactivesalesid] IS NULL)
        OR v.[llp_respnewvehiclesid] <> s.[llp_respnewvehiclesid]
            OR (v.[llp_respnewvehiclesid] IS NULL AND s.[llp_respnewvehiclesid] IS NOT NULL)
        OR (v.[llp_respnewvehiclesid] IS NOT NULL AND s.[llp_respnewvehiclesid] IS NULL)
        OR v.[llp_vatnumber] <> s.[llp_vatnumber]
            OR (v.[llp_vatnumber] IS NULL AND s.[llp_vatnumber] IS NOT NULL)
        OR (v.[llp_vatnumber] IS NOT NULL AND s.[llp_vatnumber] IS NULL)
        OR v.[name] <> s.[name]
            OR (v.[name] IS NULL AND s.[name] IS NOT NULL)
        OR (v.[name] IS NOT NULL AND s.[name] IS NULL)
        OR v.[ownerid] <> s.[ownerid]
            OR (v.[ownerid] IS NULL AND s.[ownerid] IS NOT NULL)
        OR (v.[ownerid] IS NOT NULL AND s.[ownerid] IS NULL)
        OR v.[owningbusinessunit] <> s.[owningbusinessunit]
            OR (v.[owningbusinessunit] IS NULL AND s.[owningbusinessunit] IS NOT NULL)
        OR (v.[owningbusinessunit] IS NOT NULL AND s.[owningbusinessunit] IS NULL)
        OR v.[statecode] <> s.[statecode]
            OR (v.[statecode] IS NULL AND s.[statecode] IS NOT NULL)
        OR (v.[statecode] IS NOT NULL AND s.[statecode] IS NULL)
        OR v.[wa_registrationnumber] <> s.[wa_registrationnumber]
            OR (v.[wa_registrationnumber] IS NULL AND s.[wa_registrationnumber] IS NOT NULL)
        OR (v.[wa_registrationnumber] IS NOT NULL AND s.[wa_registrationnumber] IS NULL)
        )
        THEN 
            UPDATE SET
                [ThreadLogUpdateId] = @ThreadLogId
            

                
        WHEN NOT MATCHED BY TARGET 
            THEN INSERT
            ( 
            [Id]
            , [accountcategorycode]
            , [accountid]
            , [address1_city]
            , [address2_city]
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
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
            
    ) VALUES (
            s.[Id]
            , s.[accountcategorycode]
            , s.[accountid]
            , s.[address1_city]
            , s.[address2_city]
            , s.[llp_cantonid]
            , s.[llp_cantondid]
            , s.[llp_promisingas]
            , s.[llp_promisingnv]
            , s.[llp_respactivesalesid]
            , s.[llp_respnewvehiclesid]
            , s.[llp_vatnumber]
            , s.[name]
            , s.[ownerid]
            , s.[owningbusinessunit]
            , s.[statecode]
            , s.[wa_registrationnumber]
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
    
    INSERT INTO [Vault].[CRMdboAccount] (
            [Id]
            , [accountcategorycode]
            , [accountid]
            , [address1_city]
            , [address2_city]
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
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
        
    ) 
    OUTPUT Inserted.ThreadLogUpdateId INTO @UpdateRowCounts
    SELECT

            s.[Id]
            , s.[accountcategorycode]
            , s.[accountid]
            , s.[address1_city]
            , s.[address2_city]
            , s.[llp_cantonid]
            , s.[llp_cantondid]
            , s.[llp_promisingas]
            , s.[llp_promisingnv]
            , s.[llp_respactivesalesid]
            , s.[llp_respnewvehiclesid]
            , s.[llp_vatnumber]
            , s.[name]
            , s.[ownerid]
            , s.[owningbusinessunit]
            , s.[statecode]
            , s.[wa_registrationnumber]
            , s.[DataSourceId]
            , @ThreadLogId
            , -1
            , -1
            , N'U' -- update
    FROM Stage.CRMdboAccount AS s
    INNER JOIN Vault.CRMdboAccount AS v
        ON  s.[Id] = v.[Id] AND v.ThreadLogUpdateId = @ThreadLogId
    
    INSERT INTO [Vault].[CRMdboAccount] (
            [Id]
            , [accountcategorycode]
            , [accountid]
            , [address1_city]
            , [address2_city]
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
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
            
    ) 
    OUTPUT Inserted.ThreadLogDeleteId INTO @DeleteRowCounts
    SELECT
            v.[Id]
            , v.[accountcategorycode]
            , v.[accountid]
            , v.[address1_city]
            , v.[address2_city]
            , v.[llp_cantonid]
            , v.[llp_cantondid]
            , v.[llp_promisingas]
            , v.[llp_promisingnv]
            , v.[llp_respactivesalesid]
            , v.[llp_respnewvehiclesid]
            , v.[llp_vatnumber]
            , v.[name]
            , v.[ownerid]
            , v.[owningbusinessunit]
            , v.[statecode]
            , v.[wa_registrationnumber]
            , v.[DataSourceId]
            , @ThreadLogId
            , -1
            , -1
            , N'D' -- update
    FROM Vault.CRMdboAccount AS v
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
                , TableFinalRowCount = (SELECT COUNT(*) FROM [Vault].[CRMdboAccount] WITH (NOLOCK))
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
