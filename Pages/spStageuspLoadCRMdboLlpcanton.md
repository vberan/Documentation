Stored Procedure Stage.uspLoadCRMdboLlp\_canton {#spStageuspLoadCRMdboLlpcanton}
-----------------------------------------------

Definition of Stored procedure:

``` {.sql}
CREATE PROCEDURE [Stage].[uspLoadCRMdboLlp_canton] 
    @ThreadLogId int
        , @DataSourceId int
    AS
    BEGIN TRY
        -- set up the enviroment
        SET NOCOUNT ON;
    

        TRUNCATE TABLE [Stage].[CRMdboLlp_canton]; 

        -- log the initial table state
        UPDATE Etl.ThreadLog
            SET TableInitialRowCount = (SELECT COUNT(*) FROM [Stage].[CRMdboLlp_canton] WITH (NOLOCK))
        WHERE ThreadLogId = @ThreadLogId;

        DECLARE @loadDateFrom datetime2;
        SELECT @loadDateFrom = '1901-01-01';

        INSERT INTO [Stage].[CRMdboLlp_canton]
            ( 
                [createdby]
                , [createdby_entitytype]
                , [createdbyname]
                , [createdbyyominame]
                , [createdon]
                , [createdonbehalfby]
                , [createdonbehalfby_entitytype]
                , [createdonbehalfbyname]
                , [createdonbehalfbyyominame]
                , [Id]
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
                , [ThreadLogId]
    )

        SELECT 
                [createdby] = s.[createdby]
                , [createdby_entitytype] = s.[createdby_entitytype]
                , [createdbyname] = s.[createdbyname]
                , [createdbyyominame] = s.[createdbyyominame]
                , [createdon] = s.[createdon]
                , [createdonbehalfby] = s.[createdonbehalfby]
                , [createdonbehalfby_entitytype] = s.[createdonbehalfby_entitytype]
                , [createdonbehalfbyname] = s.[createdonbehalfbyname]
                , [createdonbehalfbyyominame] = s.[createdonbehalfbyyominame]
                , [Id] = s.[Id]
                , [importsequencenumber] = s.[importsequencenumber]
                , [llp_assignedntsalesmanid] = s.[llp_assignedntsalesmanid]
                , [llp_assignedntsalesmanid_entitytype] = s.[llp_assignedntsalesmanid_entitytype]
                , [llp_assignedntsalesmanidname] = s.[llp_assignedntsalesmanidname]
                , [llp_assignedntsalesmanidyominame] = s.[llp_assignedntsalesmanidyominame]
                , [llp_cantonid] = s.[llp_cantonid]
                , [llp_certdisctrict] = s.[llp_certdisctrict]
                , [llp_codeofcanton] = s.[llp_codeofcanton]
                , [llp_country] = s.[llp_country]
                , [llp_name] = s.[llp_name]
                , [llp_regionid] = s.[llp_regionid]
                , [llp_regionid_entitytype] = s.[llp_regionid_entitytype]
                , [llp_regionidname] = s.[llp_regionidname]
                , [llp_shortofcanton] = s.[llp_shortofcanton]
                , [modifiedby] = s.[modifiedby]
                , [modifiedby_entitytype] = s.[modifiedby_entitytype]
                , [modifiedbyname] = s.[modifiedbyname]
                , [modifiedbyyominame] = s.[modifiedbyyominame]
                , [modifiedon] = s.[modifiedon]
                , [modifiedonbehalfby] = s.[modifiedonbehalfby]
                , [modifiedonbehalfby_entitytype] = s.[modifiedonbehalfby_entitytype]
                , [modifiedonbehalfbyname] = s.[modifiedonbehalfbyname]
                , [modifiedonbehalfbyyominame] = s.[modifiedonbehalfbyyominame]
                , [organizationid] = s.[organizationid]
                , [organizationid_entitytype] = s.[organizationid_entitytype]
                , [organizationidname] = s.[organizationidname]
                , [overriddencreatedon] = s.[overriddencreatedon]
                , [SinkCreatedOn] = s.[SinkCreatedOn]
                , [SinkModifiedOn] = s.[SinkModifiedOn]
                , [statecode] = s.[statecode]
                , [statuscode] = s.[statuscode]
                , [timezoneruleversionnumber] = s.[timezoneruleversionnumber]
                , [utcconversiontimezonecode] = s.[utcconversiontimezonecode]
                , [versionnumber] = s.[versionnumber]
                , [DataSourceId] = @DataSourceId
                , [ThreadLogId] = @ThreadLogId
    
        FROM [scaniacrmexport.database.windows.net].[ScaniaCRMExport].[dbo].[llp_canton] AS s WITH (NOLOCK)

        --Log ThreadLog Success
        UPDATE Etl.ThreadLog
        SET ExtractRowCount = (SELECT COUNT(*) FROM [Stage].[CRMdboLlp_canton] WITH (NOLOCK) WHERE ThreadLogId = @ThreadLogId)
            , InsertRowCount = (SELECT COUNT(*) FROM [Stage].[CRMdboLlp_canton] WITH (NOLOCK) WHERE ThreadLogId = @ThreadLogId)
            , TableFinalRowCount = (SELECT COUNT(*) FROM [Stage].[CRMdboLlp_canton] WITH (NOLOCK) )
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
