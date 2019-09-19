Stored Procedure Vault.uspLoadCRMdboLlp\_canton {#spVaultuspLoadCRMdboLlpcanton}
-----------------------------------------------

Definition of Stored procedure:

``` {.sql}
CREATE PROCEDURE [Vault].[uspLoadCRMdboLlp_canton] 
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
            SET TableInitialRowCount = (SELECT COUNT(*) FROM [Vault].[CRMdboLlp_canton] WITH (NOLOCK))
        WHERE ThreadLogId = @ThreadLogId;

            BEGIN TRANSACTION;

    
        MERGE INTO [Vault].[CRMdboLlp_canton] AS v
        USING [Stage].[CRMdboLlp_canton] AS s
            ON ( s.[Id] = v.[Id]AND s.[DataSourceId] = v.[DataSourceId]
     AND v.[ThreadLogDeleteId] = -1 AND v.[ThreadLogUpdateId] = -1 AND v.[ChangeOperation] <> N'D'
    )

        WHEN MATCHED AND
            (
            v.[createdby] <> s.[createdby]
            OR (v.[createdby] IS NULL AND s.[createdby] IS NOT NULL)
        OR (v.[createdby] IS NOT NULL AND s.[createdby] IS NULL)
        OR v.[createdby_entitytype] <> s.[createdby_entitytype]
            OR (v.[createdby_entitytype] IS NULL AND s.[createdby_entitytype] IS NOT NULL)
        OR (v.[createdby_entitytype] IS NOT NULL AND s.[createdby_entitytype] IS NULL)
        OR v.[createdbyname] <> s.[createdbyname]
            OR (v.[createdbyname] IS NULL AND s.[createdbyname] IS NOT NULL)
        OR (v.[createdbyname] IS NOT NULL AND s.[createdbyname] IS NULL)
        OR v.[createdbyyominame] <> s.[createdbyyominame]
            OR (v.[createdbyyominame] IS NULL AND s.[createdbyyominame] IS NOT NULL)
        OR (v.[createdbyyominame] IS NOT NULL AND s.[createdbyyominame] IS NULL)
        OR v.[createdon] <> s.[createdon]
            OR (v.[createdon] IS NULL AND s.[createdon] IS NOT NULL)
        OR (v.[createdon] IS NOT NULL AND s.[createdon] IS NULL)
        OR v.[createdonbehalfby] <> s.[createdonbehalfby]
            OR (v.[createdonbehalfby] IS NULL AND s.[createdonbehalfby] IS NOT NULL)
        OR (v.[createdonbehalfby] IS NOT NULL AND s.[createdonbehalfby] IS NULL)
        OR v.[createdonbehalfby_entitytype] <> s.[createdonbehalfby_entitytype]
            OR (v.[createdonbehalfby_entitytype] IS NULL AND s.[createdonbehalfby_entitytype] IS NOT NULL)
        OR (v.[createdonbehalfby_entitytype] IS NOT NULL AND s.[createdonbehalfby_entitytype] IS NULL)
        OR v.[createdonbehalfbyname] <> s.[createdonbehalfbyname]
            OR (v.[createdonbehalfbyname] IS NULL AND s.[createdonbehalfbyname] IS NOT NULL)
        OR (v.[createdonbehalfbyname] IS NOT NULL AND s.[createdonbehalfbyname] IS NULL)
        OR v.[createdonbehalfbyyominame] <> s.[createdonbehalfbyyominame]
            OR (v.[createdonbehalfbyyominame] IS NULL AND s.[createdonbehalfbyyominame] IS NOT NULL)
        OR (v.[createdonbehalfbyyominame] IS NOT NULL AND s.[createdonbehalfbyyominame] IS NULL)
        OR v.[importsequencenumber] <> s.[importsequencenumber]
            OR (v.[importsequencenumber] IS NULL AND s.[importsequencenumber] IS NOT NULL)
        OR (v.[importsequencenumber] IS NOT NULL AND s.[importsequencenumber] IS NULL)
        OR v.[llp_assignedntsalesmanid] <> s.[llp_assignedntsalesmanid]
            OR (v.[llp_assignedntsalesmanid] IS NULL AND s.[llp_assignedntsalesmanid] IS NOT NULL)
        OR (v.[llp_assignedntsalesmanid] IS NOT NULL AND s.[llp_assignedntsalesmanid] IS NULL)
        OR v.[llp_assignedntsalesmanid_entitytype] <> s.[llp_assignedntsalesmanid_entitytype]
            OR (v.[llp_assignedntsalesmanid_entitytype] IS NULL AND s.[llp_assignedntsalesmanid_entitytype] IS NOT NULL)
        OR (v.[llp_assignedntsalesmanid_entitytype] IS NOT NULL AND s.[llp_assignedntsalesmanid_entitytype] IS NULL)
        OR v.[llp_assignedntsalesmanidname] <> s.[llp_assignedntsalesmanidname]
            OR (v.[llp_assignedntsalesmanidname] IS NULL AND s.[llp_assignedntsalesmanidname] IS NOT NULL)
        OR (v.[llp_assignedntsalesmanidname] IS NOT NULL AND s.[llp_assignedntsalesmanidname] IS NULL)
        OR v.[llp_assignedntsalesmanidyominame] <> s.[llp_assignedntsalesmanidyominame]
            OR (v.[llp_assignedntsalesmanidyominame] IS NULL AND s.[llp_assignedntsalesmanidyominame] IS NOT NULL)
        OR (v.[llp_assignedntsalesmanidyominame] IS NOT NULL AND s.[llp_assignedntsalesmanidyominame] IS NULL)
        OR v.[llp_cantonid] <> s.[llp_cantonid]
            OR (v.[llp_cantonid] IS NULL AND s.[llp_cantonid] IS NOT NULL)
        OR (v.[llp_cantonid] IS NOT NULL AND s.[llp_cantonid] IS NULL)
        OR v.[llp_certdisctrict] <> s.[llp_certdisctrict]
            OR (v.[llp_certdisctrict] IS NULL AND s.[llp_certdisctrict] IS NOT NULL)
        OR (v.[llp_certdisctrict] IS NOT NULL AND s.[llp_certdisctrict] IS NULL)
        OR v.[llp_codeofcanton] <> s.[llp_codeofcanton]
            OR (v.[llp_codeofcanton] IS NULL AND s.[llp_codeofcanton] IS NOT NULL)
        OR (v.[llp_codeofcanton] IS NOT NULL AND s.[llp_codeofcanton] IS NULL)
        OR v.[llp_country] <> s.[llp_country]
            OR (v.[llp_country] IS NULL AND s.[llp_country] IS NOT NULL)
        OR (v.[llp_country] IS NOT NULL AND s.[llp_country] IS NULL)
        OR v.[llp_name] <> s.[llp_name]
            OR (v.[llp_name] IS NULL AND s.[llp_name] IS NOT NULL)
        OR (v.[llp_name] IS NOT NULL AND s.[llp_name] IS NULL)
        OR v.[llp_regionid] <> s.[llp_regionid]
            OR (v.[llp_regionid] IS NULL AND s.[llp_regionid] IS NOT NULL)
        OR (v.[llp_regionid] IS NOT NULL AND s.[llp_regionid] IS NULL)
        OR v.[llp_regionid_entitytype] <> s.[llp_regionid_entitytype]
            OR (v.[llp_regionid_entitytype] IS NULL AND s.[llp_regionid_entitytype] IS NOT NULL)
        OR (v.[llp_regionid_entitytype] IS NOT NULL AND s.[llp_regionid_entitytype] IS NULL)
        OR v.[llp_regionidname] <> s.[llp_regionidname]
            OR (v.[llp_regionidname] IS NULL AND s.[llp_regionidname] IS NOT NULL)
        OR (v.[llp_regionidname] IS NOT NULL AND s.[llp_regionidname] IS NULL)
        OR v.[llp_shortofcanton] <> s.[llp_shortofcanton]
            OR (v.[llp_shortofcanton] IS NULL AND s.[llp_shortofcanton] IS NOT NULL)
        OR (v.[llp_shortofcanton] IS NOT NULL AND s.[llp_shortofcanton] IS NULL)
        OR v.[modifiedby] <> s.[modifiedby]
            OR (v.[modifiedby] IS NULL AND s.[modifiedby] IS NOT NULL)
        OR (v.[modifiedby] IS NOT NULL AND s.[modifiedby] IS NULL)
        OR v.[modifiedby_entitytype] <> s.[modifiedby_entitytype]
            OR (v.[modifiedby_entitytype] IS NULL AND s.[modifiedby_entitytype] IS NOT NULL)
        OR (v.[modifiedby_entitytype] IS NOT NULL AND s.[modifiedby_entitytype] IS NULL)
        OR v.[modifiedbyname] <> s.[modifiedbyname]
            OR (v.[modifiedbyname] IS NULL AND s.[modifiedbyname] IS NOT NULL)
        OR (v.[modifiedbyname] IS NOT NULL AND s.[modifiedbyname] IS NULL)
        OR v.[modifiedbyyominame] <> s.[modifiedbyyominame]
            OR (v.[modifiedbyyominame] IS NULL AND s.[modifiedbyyominame] IS NOT NULL)
        OR (v.[modifiedbyyominame] IS NOT NULL AND s.[modifiedbyyominame] IS NULL)
        OR v.[modifiedon] <> s.[modifiedon]
            OR (v.[modifiedon] IS NULL AND s.[modifiedon] IS NOT NULL)
        OR (v.[modifiedon] IS NOT NULL AND s.[modifiedon] IS NULL)
        OR v.[modifiedonbehalfby] <> s.[modifiedonbehalfby]
            OR (v.[modifiedonbehalfby] IS NULL AND s.[modifiedonbehalfby] IS NOT NULL)
        OR (v.[modifiedonbehalfby] IS NOT NULL AND s.[modifiedonbehalfby] IS NULL)
        OR v.[modifiedonbehalfby_entitytype] <> s.[modifiedonbehalfby_entitytype]
            OR (v.[modifiedonbehalfby_entitytype] IS NULL AND s.[modifiedonbehalfby_entitytype] IS NOT NULL)
        OR (v.[modifiedonbehalfby_entitytype] IS NOT NULL AND s.[modifiedonbehalfby_entitytype] IS NULL)
        OR v.[modifiedonbehalfbyname] <> s.[modifiedonbehalfbyname]
            OR (v.[modifiedonbehalfbyname] IS NULL AND s.[modifiedonbehalfbyname] IS NOT NULL)
        OR (v.[modifiedonbehalfbyname] IS NOT NULL AND s.[modifiedonbehalfbyname] IS NULL)
        OR v.[modifiedonbehalfbyyominame] <> s.[modifiedonbehalfbyyominame]
            OR (v.[modifiedonbehalfbyyominame] IS NULL AND s.[modifiedonbehalfbyyominame] IS NOT NULL)
        OR (v.[modifiedonbehalfbyyominame] IS NOT NULL AND s.[modifiedonbehalfbyyominame] IS NULL)
        OR v.[organizationid] <> s.[organizationid]
            OR (v.[organizationid] IS NULL AND s.[organizationid] IS NOT NULL)
        OR (v.[organizationid] IS NOT NULL AND s.[organizationid] IS NULL)
        OR v.[organizationid_entitytype] <> s.[organizationid_entitytype]
            OR (v.[organizationid_entitytype] IS NULL AND s.[organizationid_entitytype] IS NOT NULL)
        OR (v.[organizationid_entitytype] IS NOT NULL AND s.[organizationid_entitytype] IS NULL)
        OR v.[organizationidname] <> s.[organizationidname]
            OR (v.[organizationidname] IS NULL AND s.[organizationidname] IS NOT NULL)
        OR (v.[organizationidname] IS NOT NULL AND s.[organizationidname] IS NULL)
        OR v.[overriddencreatedon] <> s.[overriddencreatedon]
            OR (v.[overriddencreatedon] IS NULL AND s.[overriddencreatedon] IS NOT NULL)
        OR (v.[overriddencreatedon] IS NOT NULL AND s.[overriddencreatedon] IS NULL)
        OR v.[SinkCreatedOn] <> s.[SinkCreatedOn]
            OR (v.[SinkCreatedOn] IS NULL AND s.[SinkCreatedOn] IS NOT NULL)
        OR (v.[SinkCreatedOn] IS NOT NULL AND s.[SinkCreatedOn] IS NULL)
        OR v.[SinkModifiedOn] <> s.[SinkModifiedOn]
            OR (v.[SinkModifiedOn] IS NULL AND s.[SinkModifiedOn] IS NOT NULL)
        OR (v.[SinkModifiedOn] IS NOT NULL AND s.[SinkModifiedOn] IS NULL)
        OR v.[statecode] <> s.[statecode]
            OR (v.[statecode] IS NULL AND s.[statecode] IS NOT NULL)
        OR (v.[statecode] IS NOT NULL AND s.[statecode] IS NULL)
        OR v.[statuscode] <> s.[statuscode]
            OR (v.[statuscode] IS NULL AND s.[statuscode] IS NOT NULL)
        OR (v.[statuscode] IS NOT NULL AND s.[statuscode] IS NULL)
        OR v.[timezoneruleversionnumber] <> s.[timezoneruleversionnumber]
            OR (v.[timezoneruleversionnumber] IS NULL AND s.[timezoneruleversionnumber] IS NOT NULL)
        OR (v.[timezoneruleversionnumber] IS NOT NULL AND s.[timezoneruleversionnumber] IS NULL)
        OR v.[utcconversiontimezonecode] <> s.[utcconversiontimezonecode]
            OR (v.[utcconversiontimezonecode] IS NULL AND s.[utcconversiontimezonecode] IS NOT NULL)
        OR (v.[utcconversiontimezonecode] IS NOT NULL AND s.[utcconversiontimezonecode] IS NULL)
        OR v.[versionnumber] <> s.[versionnumber]
            OR (v.[versionnumber] IS NULL AND s.[versionnumber] IS NOT NULL)
        OR (v.[versionnumber] IS NOT NULL AND s.[versionnumber] IS NULL)
        )
        THEN 
            UPDATE SET
                [ThreadLogUpdateId] = @ThreadLogId
            

                
        WHEN NOT MATCHED BY TARGET 
            THEN INSERT
            ( 
            [Id]
            , [createdby]
            , [createdby_entitytype]
            , [createdbyname]
            , [createdbyyominame]
            , [createdon]
            , [createdonbehalfby]
            , [createdonbehalfby_entitytype]
            , [createdonbehalfbyname]
            , [createdonbehalfbyyominame]
            , [importsequencenumber]
            , [llp_assignedntsalesmanid]
            , [llp_assignedntsalesmanid_entitytype]
            , [llp_assignedntsalesmanidname]
            , [llp_assignedntsalesmanidyominame]
            , [llp_cantonid]
            , [llp_certdisctrict]
            , [llp_codeofcanton]
            , [llp_country]
            , [llp_name]
            , [llp_regionid]
            , [llp_regionid_entitytype]
            , [llp_regionidname]
            , [llp_shortofcanton]
            , [modifiedby]
            , [modifiedby_entitytype]
            , [modifiedbyname]
            , [modifiedbyyominame]
            , [modifiedon]
            , [modifiedonbehalfby]
            , [modifiedonbehalfby_entitytype]
            , [modifiedonbehalfbyname]
            , [modifiedonbehalfbyyominame]
            , [organizationid]
            , [organizationid_entitytype]
            , [organizationidname]
            , [overriddencreatedon]
            , [SinkCreatedOn]
            , [SinkModifiedOn]
            , [statecode]
            , [statuscode]
            , [timezoneruleversionnumber]
            , [utcconversiontimezonecode]
            , [versionnumber]
            , [DataSourceId]
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
            
    ) VALUES (
            s.[Id]
            , s.[createdby]
            , s.[createdby_entitytype]
            , s.[createdbyname]
            , s.[createdbyyominame]
            , s.[createdon]
            , s.[createdonbehalfby]
            , s.[createdonbehalfby_entitytype]
            , s.[createdonbehalfbyname]
            , s.[createdonbehalfbyyominame]
            , s.[importsequencenumber]
            , s.[llp_assignedntsalesmanid]
            , s.[llp_assignedntsalesmanid_entitytype]
            , s.[llp_assignedntsalesmanidname]
            , s.[llp_assignedntsalesmanidyominame]
            , s.[llp_cantonid]
            , s.[llp_certdisctrict]
            , s.[llp_codeofcanton]
            , s.[llp_country]
            , s.[llp_name]
            , s.[llp_regionid]
            , s.[llp_regionid_entitytype]
            , s.[llp_regionidname]
            , s.[llp_shortofcanton]
            , s.[modifiedby]
            , s.[modifiedby_entitytype]
            , s.[modifiedbyname]
            , s.[modifiedbyyominame]
            , s.[modifiedon]
            , s.[modifiedonbehalfby]
            , s.[modifiedonbehalfby_entitytype]
            , s.[modifiedonbehalfbyname]
            , s.[modifiedonbehalfbyyominame]
            , s.[organizationid]
            , s.[organizationid_entitytype]
            , s.[organizationidname]
            , s.[overriddencreatedon]
            , s.[SinkCreatedOn]
            , s.[SinkModifiedOn]
            , s.[statecode]
            , s.[statuscode]
            , s.[timezoneruleversionnumber]
            , s.[utcconversiontimezonecode]
            , s.[versionnumber]
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
    
    INSERT INTO [Vault].[CRMdboLlp_canton] (
            [Id]
            , [createdby]
            , [createdby_entitytype]
            , [createdbyname]
            , [createdbyyominame]
            , [createdon]
            , [createdonbehalfby]
            , [createdonbehalfby_entitytype]
            , [createdonbehalfbyname]
            , [createdonbehalfbyyominame]
            , [importsequencenumber]
            , [llp_assignedntsalesmanid]
            , [llp_assignedntsalesmanid_entitytype]
            , [llp_assignedntsalesmanidname]
            , [llp_assignedntsalesmanidyominame]
            , [llp_cantonid]
            , [llp_certdisctrict]
            , [llp_codeofcanton]
            , [llp_country]
            , [llp_name]
            , [llp_regionid]
            , [llp_regionid_entitytype]
            , [llp_regionidname]
            , [llp_shortofcanton]
            , [modifiedby]
            , [modifiedby_entitytype]
            , [modifiedbyname]
            , [modifiedbyyominame]
            , [modifiedon]
            , [modifiedonbehalfby]
            , [modifiedonbehalfby_entitytype]
            , [modifiedonbehalfbyname]
            , [modifiedonbehalfbyyominame]
            , [organizationid]
            , [organizationid_entitytype]
            , [organizationidname]
            , [overriddencreatedon]
            , [SinkCreatedOn]
            , [SinkModifiedOn]
            , [statecode]
            , [statuscode]
            , [timezoneruleversionnumber]
            , [utcconversiontimezonecode]
            , [versionnumber]
            , [DataSourceId]
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
        
    ) 
    OUTPUT Inserted.ThreadLogUpdateId INTO @UpdateRowCounts
    SELECT

            s.[Id]
            , s.[createdby]
            , s.[createdby_entitytype]
            , s.[createdbyname]
            , s.[createdbyyominame]
            , s.[createdon]
            , s.[createdonbehalfby]
            , s.[createdonbehalfby_entitytype]
            , s.[createdonbehalfbyname]
            , s.[createdonbehalfbyyominame]
            , s.[importsequencenumber]
            , s.[llp_assignedntsalesmanid]
            , s.[llp_assignedntsalesmanid_entitytype]
            , s.[llp_assignedntsalesmanidname]
            , s.[llp_assignedntsalesmanidyominame]
            , s.[llp_cantonid]
            , s.[llp_certdisctrict]
            , s.[llp_codeofcanton]
            , s.[llp_country]
            , s.[llp_name]
            , s.[llp_regionid]
            , s.[llp_regionid_entitytype]
            , s.[llp_regionidname]
            , s.[llp_shortofcanton]
            , s.[modifiedby]
            , s.[modifiedby_entitytype]
            , s.[modifiedbyname]
            , s.[modifiedbyyominame]
            , s.[modifiedon]
            , s.[modifiedonbehalfby]
            , s.[modifiedonbehalfby_entitytype]
            , s.[modifiedonbehalfbyname]
            , s.[modifiedonbehalfbyyominame]
            , s.[organizationid]
            , s.[organizationid_entitytype]
            , s.[organizationidname]
            , s.[overriddencreatedon]
            , s.[SinkCreatedOn]
            , s.[SinkModifiedOn]
            , s.[statecode]
            , s.[statuscode]
            , s.[timezoneruleversionnumber]
            , s.[utcconversiontimezonecode]
            , s.[versionnumber]
            , s.[DataSourceId]
            , @ThreadLogId
            , -1
            , -1
            , N'U' -- update
    FROM Stage.CRMdboLlp_canton AS s
    INNER JOIN Vault.CRMdboLlp_canton AS v
        ON  s.[Id] = v.[Id] AND v.ThreadLogUpdateId = @ThreadLogId
    
    INSERT INTO [Vault].[CRMdboLlp_canton] (
            [Id]
            , [createdby]
            , [createdby_entitytype]
            , [createdbyname]
            , [createdbyyominame]
            , [createdon]
            , [createdonbehalfby]
            , [createdonbehalfby_entitytype]
            , [createdonbehalfbyname]
            , [createdonbehalfbyyominame]
            , [importsequencenumber]
            , [llp_assignedntsalesmanid]
            , [llp_assignedntsalesmanid_entitytype]
            , [llp_assignedntsalesmanidname]
            , [llp_assignedntsalesmanidyominame]
            , [llp_cantonid]
            , [llp_certdisctrict]
            , [llp_codeofcanton]
            , [llp_country]
            , [llp_name]
            , [llp_regionid]
            , [llp_regionid_entitytype]
            , [llp_regionidname]
            , [llp_shortofcanton]
            , [modifiedby]
            , [modifiedby_entitytype]
            , [modifiedbyname]
            , [modifiedbyyominame]
            , [modifiedon]
            , [modifiedonbehalfby]
            , [modifiedonbehalfby_entitytype]
            , [modifiedonbehalfbyname]
            , [modifiedonbehalfbyyominame]
            , [organizationid]
            , [organizationid_entitytype]
            , [organizationidname]
            , [overriddencreatedon]
            , [SinkCreatedOn]
            , [SinkModifiedOn]
            , [statecode]
            , [statuscode]
            , [timezoneruleversionnumber]
            , [utcconversiontimezonecode]
            , [versionnumber]
            , [DataSourceId]
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
            
    ) 
    OUTPUT Inserted.ThreadLogDeleteId INTO @DeleteRowCounts
    SELECT
            v.[Id]
            , v.[createdby]
            , v.[createdby_entitytype]
            , v.[createdbyname]
            , v.[createdbyyominame]
            , v.[createdon]
            , v.[createdonbehalfby]
            , v.[createdonbehalfby_entitytype]
            , v.[createdonbehalfbyname]
            , v.[createdonbehalfbyyominame]
            , v.[importsequencenumber]
            , v.[llp_assignedntsalesmanid]
            , v.[llp_assignedntsalesmanid_entitytype]
            , v.[llp_assignedntsalesmanidname]
            , v.[llp_assignedntsalesmanidyominame]
            , v.[llp_cantonid]
            , v.[llp_certdisctrict]
            , v.[llp_codeofcanton]
            , v.[llp_country]
            , v.[llp_name]
            , v.[llp_regionid]
            , v.[llp_regionid_entitytype]
            , v.[llp_regionidname]
            , v.[llp_shortofcanton]
            , v.[modifiedby]
            , v.[modifiedby_entitytype]
            , v.[modifiedbyname]
            , v.[modifiedbyyominame]
            , v.[modifiedon]
            , v.[modifiedonbehalfby]
            , v.[modifiedonbehalfby_entitytype]
            , v.[modifiedonbehalfbyname]
            , v.[modifiedonbehalfbyyominame]
            , v.[organizationid]
            , v.[organizationid_entitytype]
            , v.[organizationidname]
            , v.[overriddencreatedon]
            , v.[SinkCreatedOn]
            , v.[SinkModifiedOn]
            , v.[statecode]
            , v.[statuscode]
            , v.[timezoneruleversionnumber]
            , v.[utcconversiontimezonecode]
            , v.[versionnumber]
            , v.[DataSourceId]
            , @ThreadLogId
            , -1
            , -1
            , N'D' -- update
    FROM Vault.CRMdboLlp_canton AS v
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
                , TableFinalRowCount = (SELECT COUNT(*) FROM [Vault].[CRMdboLlp_canton] WITH (NOLOCK))
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
