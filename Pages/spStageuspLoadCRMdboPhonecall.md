Stored Procedure Stage.uspLoadCRMdboPhonecall {#spStageuspLoadCRMdboPhonecall}
---------------------------------------------

Definition of Stored procedure:

``` {.sql}
CREATE PROCEDURE [Stage].[uspLoadCRMdboPhonecall] 
    @ThreadLogId int
        , @DataSourceId int
    AS
    BEGIN TRY
        -- set up the enviroment
        SET NOCOUNT ON;
    

        TRUNCATE TABLE [Stage].[CRMdboPhonecall]; 

        -- log the initial table state
        UPDATE Etl.ThreadLog
            SET TableInitialRowCount = (SELECT COUNT(*) FROM [Stage].[CRMdboPhonecall] WITH (NOLOCK))
        WHERE ThreadLogId = @ThreadLogId;

        DECLARE @loadDateFrom datetime2;
        SELECT @loadDateFrom = '1901-01-01';

        INSERT INTO [Stage].[CRMdboPhonecall]
            ( 
                [activityadditionalparams]
                , [activityid]
                , [activitytypecode]
                , [actualdurationminutes]
                , [actualend]
                , [actualstart]
                , [category]
                , [createdby]
                , [createdby_entitytype]
                , [createdbyname]
                , [createdbyyominame]
                , [createdon]
                , [createdonbehalfby]
                , [createdonbehalfby_entitytype]
                , [createdonbehalfbyname]
                , [createdonbehalfbyyominame]
                , [description]
                , [directioncode]
                , [exchangerate]
                , [from]
                , [Id]
                , [importsequencenumber]
                , [isbilled]
                , [isregularactivity]
                , [isworkflowcreated]
                , [lastonholdtime]
                , [leftvoicemail]
                , [llp_reportingaccountid]
                , [llp_reportingaccountid_entitytype]
                , [llp_reportingaccountidname]
                , [llp_reportingaccountidyominame]
                , [modifiedby]
                , [modifiedby_entitytype]
                , [modifiedbyname]
                , [modifiedbyyominame]
                , [modifiedon]
                , [modifiedonbehalfby]
                , [modifiedonbehalfby_entitytype]
                , [modifiedonbehalfbyname]
                , [modifiedonbehalfbyyominame]
                , [onholdtime]
                , [overriddencreatedon]
                , [ownerid]
                , [ownerid_entitytype]
                , [owneridname]
                , [owneridtype]
                , [owneridyominame]
                , [owningbusinessunit]
                , [owningbusinessunit_entitytype]
                , [owningteam]
                , [owningteam_entitytype]
                , [owninguser]
                , [owninguser_entitytype]
                , [phonenumber]
                , [prioritycode]
                , [processid]
                , [regardingobjectid]
                , [regardingobjectid_entitytype]
                , [regardingobjectidname]
                , [regardingobjectidyominame]
                , [regardingobjecttypecode]
                , [scheduleddurationminutes]
                , [scheduledend]
                , [scheduledstart]
                , [serviceid]
                , [serviceid_entitytype]
                , [SinkCreatedOn]
                , [SinkModifiedOn]
                , [slaid]
                , [slaid_entitytype]
                , [slainvokedid]
                , [slainvokedid_entitytype]
                , [slainvokedidname]
                , [slaname]
                , [sortdate]
                , [stageid]
                , [statecode]
                , [statuscode]
                , [subcategory]
                , [subject]
                , [subscriptionid]
                , [timezoneruleversionnumber]
                , [to]
                , [transactioncurrencyid]
                , [transactioncurrencyid_entitytype]
                , [transactioncurrencyidname]
                , [traversedpath]
                , [utcconversiontimezonecode]
                , [versionnumber]
                , [DataSourceId]
                , [ThreadLogId]
    )

        SELECT 
                [activityadditionalparams] = s.[activityadditionalparams]
                , [activityid] = s.[activityid]
                , [activitytypecode] = s.[activitytypecode]
                , [actualdurationminutes] = s.[actualdurationminutes]
                , [actualend] = s.[actualend]
                , [actualstart] = s.[actualstart]
                , [category] = s.[category]
                , [createdby] = s.[createdby]
                , [createdby_entitytype] = s.[createdby_entitytype]
                , [createdbyname] = s.[createdbyname]
                , [createdbyyominame] = s.[createdbyyominame]
                , [createdon] = s.[createdon]
                , [createdonbehalfby] = s.[createdonbehalfby]
                , [createdonbehalfby_entitytype] = s.[createdonbehalfby_entitytype]
                , [createdonbehalfbyname] = s.[createdonbehalfbyname]
                , [createdonbehalfbyyominame] = s.[createdonbehalfbyyominame]
                , [description] = s.[description]
                , [directioncode] = s.[directioncode]
                , [exchangerate] = s.[exchangerate]
                , [from] = s.[from]
                , [Id] = s.[Id]
                , [importsequencenumber] = s.[importsequencenumber]
                , [isbilled] = s.[isbilled]
                , [isregularactivity] = s.[isregularactivity]
                , [isworkflowcreated] = s.[isworkflowcreated]
                , [lastonholdtime] = s.[lastonholdtime]
                , [leftvoicemail] = s.[leftvoicemail]
                , [llp_reportingaccountid] = s.[llp_reportingaccountid]
                , [llp_reportingaccountid_entitytype] = s.[llp_reportingaccountid_entitytype]
                , [llp_reportingaccountidname] = s.[llp_reportingaccountidname]
                , [llp_reportingaccountidyominame] = s.[llp_reportingaccountidyominame]
                , [modifiedby] = s.[modifiedby]
                , [modifiedby_entitytype] = s.[modifiedby_entitytype]
                , [modifiedbyname] = s.[modifiedbyname]
                , [modifiedbyyominame] = s.[modifiedbyyominame]
                , [modifiedon] = s.[modifiedon]
                , [modifiedonbehalfby] = s.[modifiedonbehalfby]
                , [modifiedonbehalfby_entitytype] = s.[modifiedonbehalfby_entitytype]
                , [modifiedonbehalfbyname] = s.[modifiedonbehalfbyname]
                , [modifiedonbehalfbyyominame] = s.[modifiedonbehalfbyyominame]
                , [onholdtime] = s.[onholdtime]
                , [overriddencreatedon] = s.[overriddencreatedon]
                , [ownerid] = s.[ownerid]
                , [ownerid_entitytype] = s.[ownerid_entitytype]
                , [owneridname] = s.[owneridname]
                , [owneridtype] = s.[owneridtype]
                , [owneridyominame] = s.[owneridyominame]
                , [owningbusinessunit] = s.[owningbusinessunit]
                , [owningbusinessunit_entitytype] = s.[owningbusinessunit_entitytype]
                , [owningteam] = s.[owningteam]
                , [owningteam_entitytype] = s.[owningteam_entitytype]
                , [owninguser] = s.[owninguser]
                , [owninguser_entitytype] = s.[owninguser_entitytype]
                , [phonenumber] = s.[phonenumber]
                , [prioritycode] = s.[prioritycode]
                , [processid] = s.[processid]
                , [regardingobjectid] = s.[regardingobjectid]
                , [regardingobjectid_entitytype] = s.[regardingobjectid_entitytype]
                , [regardingobjectidname] = s.[regardingobjectidname]
                , [regardingobjectidyominame] = s.[regardingobjectidyominame]
                , [regardingobjecttypecode] = s.[regardingobjecttypecode]
                , [scheduleddurationminutes] = s.[scheduleddurationminutes]
                , [scheduledend] = s.[scheduledend]
                , [scheduledstart] = s.[scheduledstart]
                , [serviceid] = s.[serviceid]
                , [serviceid_entitytype] = s.[serviceid_entitytype]
                , [SinkCreatedOn] = s.[SinkCreatedOn]
                , [SinkModifiedOn] = s.[SinkModifiedOn]
                , [slaid] = s.[slaid]
                , [slaid_entitytype] = s.[slaid_entitytype]
                , [slainvokedid] = s.[slainvokedid]
                , [slainvokedid_entitytype] = s.[slainvokedid_entitytype]
                , [slainvokedidname] = s.[slainvokedidname]
                , [slaname] = s.[slaname]
                , [sortdate] = s.[sortdate]
                , [stageid] = s.[stageid]
                , [statecode] = s.[statecode]
                , [statuscode] = s.[statuscode]
                , [subcategory] = s.[subcategory]
                , [subject] = s.[subject]
                , [subscriptionid] = s.[subscriptionid]
                , [timezoneruleversionnumber] = s.[timezoneruleversionnumber]
                , [to] = s.[to]
                , [transactioncurrencyid] = s.[transactioncurrencyid]
                , [transactioncurrencyid_entitytype] = s.[transactioncurrencyid_entitytype]
                , [transactioncurrencyidname] = s.[transactioncurrencyidname]
                , [traversedpath] = s.[traversedpath]
                , [utcconversiontimezonecode] = s.[utcconversiontimezonecode]
                , [versionnumber] = s.[versionnumber]
                , [DataSourceId] = @DataSourceId
                , [ThreadLogId] = @ThreadLogId
    
        FROM [scaniacrmexport.database.windows.net].[ScaniaCRMExport].[dbo].[phonecall] AS s WITH (NOLOCK)

        --Log ThreadLog Success
        UPDATE Etl.ThreadLog
        SET ExtractRowCount = (SELECT COUNT(*) FROM [Stage].[CRMdboPhonecall] WITH (NOLOCK) WHERE ThreadLogId = @ThreadLogId)
            , InsertRowCount = (SELECT COUNT(*) FROM [Stage].[CRMdboPhonecall] WITH (NOLOCK) WHERE ThreadLogId = @ThreadLogId)
            , TableFinalRowCount = (SELECT COUNT(*) FROM [Stage].[CRMdboPhonecall] WITH (NOLOCK) )
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
