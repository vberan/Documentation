Stored Procedure Vault.uspLoadCRMdboAppointment {#spVaultuspLoadCRMdboAppointment}
-----------------------------------------------

Definition of Stored procedure:

``` {.sql}
CREATE PROCEDURE [Vault].[uspLoadCRMdboAppointment] 
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
            SET TableInitialRowCount = (SELECT COUNT(*) FROM [Vault].[CRMdboAppointment] WITH (NOLOCK))
        WHERE ThreadLogId = @ThreadLogId;

            BEGIN TRANSACTION;

    
        MERGE INTO [Vault].[CRMdboAppointment] AS v
        USING [Stage].[CRMdboAppointment] AS s
            ON ( s.[Id] = v.[Id]AND s.[DataSourceId] = v.[DataSourceId]
     AND v.[ThreadLogDeleteId] = -1 AND v.[ThreadLogUpdateId] = -1 AND v.[ChangeOperation] <> N'D'
    )

        WHEN MATCHED AND
            (
            v.[activityadditionalparams] <> s.[activityadditionalparams]
            OR (v.[activityadditionalparams] IS NULL AND s.[activityadditionalparams] IS NOT NULL)
        OR (v.[activityadditionalparams] IS NOT NULL AND s.[activityadditionalparams] IS NULL)
        OR v.[activityid] <> s.[activityid]
            OR (v.[activityid] IS NULL AND s.[activityid] IS NOT NULL)
        OR (v.[activityid] IS NOT NULL AND s.[activityid] IS NULL)
        OR v.[activitytypecode] <> s.[activitytypecode]
            OR (v.[activitytypecode] IS NULL AND s.[activitytypecode] IS NOT NULL)
        OR (v.[activitytypecode] IS NOT NULL AND s.[activitytypecode] IS NULL)
        OR v.[actualdurationminutes] <> s.[actualdurationminutes]
            OR (v.[actualdurationminutes] IS NULL AND s.[actualdurationminutes] IS NOT NULL)
        OR (v.[actualdurationminutes] IS NOT NULL AND s.[actualdurationminutes] IS NULL)
        OR v.[actualend] <> s.[actualend]
            OR (v.[actualend] IS NULL AND s.[actualend] IS NOT NULL)
        OR (v.[actualend] IS NOT NULL AND s.[actualend] IS NULL)
        OR v.[actualstart] <> s.[actualstart]
            OR (v.[actualstart] IS NULL AND s.[actualstart] IS NOT NULL)
        OR (v.[actualstart] IS NOT NULL AND s.[actualstart] IS NULL)
        OR v.[attachmentcount] <> s.[attachmentcount]
            OR (v.[attachmentcount] IS NULL AND s.[attachmentcount] IS NOT NULL)
        OR (v.[attachmentcount] IS NOT NULL AND s.[attachmentcount] IS NULL)
        OR v.[attachmenterrors] <> s.[attachmenterrors]
            OR (v.[attachmenterrors] IS NULL AND s.[attachmenterrors] IS NOT NULL)
        OR (v.[attachmenterrors] IS NOT NULL AND s.[attachmenterrors] IS NULL)
        OR v.[category] <> s.[category]
            OR (v.[category] IS NULL AND s.[category] IS NOT NULL)
        OR (v.[category] IS NOT NULL AND s.[category] IS NULL)
        OR v.[createdby] <> s.[createdby]
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
        OR v.[description] <> s.[description]
            OR (v.[description] IS NULL AND s.[description] IS NOT NULL)
        OR (v.[description] IS NOT NULL AND s.[description] IS NULL)
        OR v.[exchangerate] <> s.[exchangerate]
            OR (v.[exchangerate] IS NULL AND s.[exchangerate] IS NOT NULL)
        OR (v.[exchangerate] IS NOT NULL AND s.[exchangerate] IS NULL)
        OR v.[globalobjectid] <> s.[globalobjectid]
            OR (v.[globalobjectid] IS NULL AND s.[globalobjectid] IS NOT NULL)
        OR (v.[globalobjectid] IS NOT NULL AND s.[globalobjectid] IS NULL)
        OR v.[importsequencenumber] <> s.[importsequencenumber]
            OR (v.[importsequencenumber] IS NULL AND s.[importsequencenumber] IS NOT NULL)
        OR (v.[importsequencenumber] IS NOT NULL AND s.[importsequencenumber] IS NULL)
        OR v.[instancetypecode] <> s.[instancetypecode]
            OR (v.[instancetypecode] IS NULL AND s.[instancetypecode] IS NOT NULL)
        OR (v.[instancetypecode] IS NOT NULL AND s.[instancetypecode] IS NULL)
        OR v.[isalldayevent] <> s.[isalldayevent]
            OR (v.[isalldayevent] IS NULL AND s.[isalldayevent] IS NOT NULL)
        OR (v.[isalldayevent] IS NOT NULL AND s.[isalldayevent] IS NULL)
        OR v.[isbilled] <> s.[isbilled]
            OR (v.[isbilled] IS NULL AND s.[isbilled] IS NOT NULL)
        OR (v.[isbilled] IS NOT NULL AND s.[isbilled] IS NULL)
        OR v.[isdraft] <> s.[isdraft]
            OR (v.[isdraft] IS NULL AND s.[isdraft] IS NOT NULL)
        OR (v.[isdraft] IS NOT NULL AND s.[isdraft] IS NULL)
        OR v.[ismapiprivate] <> s.[ismapiprivate]
            OR (v.[ismapiprivate] IS NULL AND s.[ismapiprivate] IS NOT NULL)
        OR (v.[ismapiprivate] IS NOT NULL AND s.[ismapiprivate] IS NULL)
        OR v.[isregularactivity] <> s.[isregularactivity]
            OR (v.[isregularactivity] IS NULL AND s.[isregularactivity] IS NOT NULL)
        OR (v.[isregularactivity] IS NOT NULL AND s.[isregularactivity] IS NULL)
        OR v.[isunsafe] <> s.[isunsafe]
            OR (v.[isunsafe] IS NULL AND s.[isunsafe] IS NOT NULL)
        OR (v.[isunsafe] IS NOT NULL AND s.[isunsafe] IS NULL)
        OR v.[isworkflowcreated] <> s.[isworkflowcreated]
            OR (v.[isworkflowcreated] IS NULL AND s.[isworkflowcreated] IS NOT NULL)
        OR (v.[isworkflowcreated] IS NOT NULL AND s.[isworkflowcreated] IS NULL)
        OR v.[lastonholdtime] <> s.[lastonholdtime]
            OR (v.[lastonholdtime] IS NULL AND s.[lastonholdtime] IS NOT NULL)
        OR (v.[lastonholdtime] IS NOT NULL AND s.[lastonholdtime] IS NULL)
        OR v.[llp_importbatch] <> s.[llp_importbatch]
            OR (v.[llp_importbatch] IS NULL AND s.[llp_importbatch] IS NOT NULL)
        OR (v.[llp_importbatch] IS NOT NULL AND s.[llp_importbatch] IS NULL)
        OR v.[llp_reportingaccountid] <> s.[llp_reportingaccountid]
            OR (v.[llp_reportingaccountid] IS NULL AND s.[llp_reportingaccountid] IS NOT NULL)
        OR (v.[llp_reportingaccountid] IS NOT NULL AND s.[llp_reportingaccountid] IS NULL)
        OR v.[llp_reportingaccountid_entitytype] <> s.[llp_reportingaccountid_entitytype]
            OR (v.[llp_reportingaccountid_entitytype] IS NULL AND s.[llp_reportingaccountid_entitytype] IS NOT NULL)
        OR (v.[llp_reportingaccountid_entitytype] IS NOT NULL AND s.[llp_reportingaccountid_entitytype] IS NULL)
        OR v.[llp_reportingaccountidname] <> s.[llp_reportingaccountidname]
            OR (v.[llp_reportingaccountidname] IS NULL AND s.[llp_reportingaccountidname] IS NOT NULL)
        OR (v.[llp_reportingaccountidname] IS NOT NULL AND s.[llp_reportingaccountidname] IS NULL)
        OR v.[llp_reportingaccountidyominame] <> s.[llp_reportingaccountidyominame]
            OR (v.[llp_reportingaccountidyominame] IS NULL AND s.[llp_reportingaccountidyominame] IS NOT NULL)
        OR (v.[llp_reportingaccountidyominame] IS NOT NULL AND s.[llp_reportingaccountidyominame] IS NULL)
        OR v.[location] <> s.[location]
            OR (v.[location] IS NULL AND s.[location] IS NOT NULL)
        OR (v.[location] IS NOT NULL AND s.[location] IS NULL)
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
        OR v.[modifiedfieldsmask] <> s.[modifiedfieldsmask]
            OR (v.[modifiedfieldsmask] IS NULL AND s.[modifiedfieldsmask] IS NOT NULL)
        OR (v.[modifiedfieldsmask] IS NOT NULL AND s.[modifiedfieldsmask] IS NULL)
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
        OR v.[onholdtime] <> s.[onholdtime]
            OR (v.[onholdtime] IS NULL AND s.[onholdtime] IS NOT NULL)
        OR (v.[onholdtime] IS NOT NULL AND s.[onholdtime] IS NULL)
        OR v.[optionalattendees] <> s.[optionalattendees]
            OR (v.[optionalattendees] IS NULL AND s.[optionalattendees] IS NOT NULL)
        OR (v.[optionalattendees] IS NOT NULL AND s.[optionalattendees] IS NULL)
        OR v.[organizer] <> s.[organizer]
            OR (v.[organizer] IS NULL AND s.[organizer] IS NOT NULL)
        OR (v.[organizer] IS NOT NULL AND s.[organizer] IS NULL)
        OR v.[originalstartdate] <> s.[originalstartdate]
            OR (v.[originalstartdate] IS NULL AND s.[originalstartdate] IS NOT NULL)
        OR (v.[originalstartdate] IS NOT NULL AND s.[originalstartdate] IS NULL)
        OR v.[outlookownerapptid] <> s.[outlookownerapptid]
            OR (v.[outlookownerapptid] IS NULL AND s.[outlookownerapptid] IS NOT NULL)
        OR (v.[outlookownerapptid] IS NOT NULL AND s.[outlookownerapptid] IS NULL)
        OR v.[overriddencreatedon] <> s.[overriddencreatedon]
            OR (v.[overriddencreatedon] IS NULL AND s.[overriddencreatedon] IS NOT NULL)
        OR (v.[overriddencreatedon] IS NOT NULL AND s.[overriddencreatedon] IS NULL)
        OR v.[ownerid] <> s.[ownerid]
            OR (v.[ownerid] IS NULL AND s.[ownerid] IS NOT NULL)
        OR (v.[ownerid] IS NOT NULL AND s.[ownerid] IS NULL)
        OR v.[ownerid_entitytype] <> s.[ownerid_entitytype]
            OR (v.[ownerid_entitytype] IS NULL AND s.[ownerid_entitytype] IS NOT NULL)
        OR (v.[ownerid_entitytype] IS NOT NULL AND s.[ownerid_entitytype] IS NULL)
        OR v.[owneridname] <> s.[owneridname]
            OR (v.[owneridname] IS NULL AND s.[owneridname] IS NOT NULL)
        OR (v.[owneridname] IS NOT NULL AND s.[owneridname] IS NULL)
        OR v.[owneridtype] <> s.[owneridtype]
            OR (v.[owneridtype] IS NULL AND s.[owneridtype] IS NOT NULL)
        OR (v.[owneridtype] IS NOT NULL AND s.[owneridtype] IS NULL)
        OR v.[owneridyominame] <> s.[owneridyominame]
            OR (v.[owneridyominame] IS NULL AND s.[owneridyominame] IS NOT NULL)
        OR (v.[owneridyominame] IS NOT NULL AND s.[owneridyominame] IS NULL)
        OR v.[owningbusinessunit] <> s.[owningbusinessunit]
            OR (v.[owningbusinessunit] IS NULL AND s.[owningbusinessunit] IS NOT NULL)
        OR (v.[owningbusinessunit] IS NOT NULL AND s.[owningbusinessunit] IS NULL)
        OR v.[owningbusinessunit_entitytype] <> s.[owningbusinessunit_entitytype]
            OR (v.[owningbusinessunit_entitytype] IS NULL AND s.[owningbusinessunit_entitytype] IS NOT NULL)
        OR (v.[owningbusinessunit_entitytype] IS NOT NULL AND s.[owningbusinessunit_entitytype] IS NULL)
        OR v.[owningteam] <> s.[owningteam]
            OR (v.[owningteam] IS NULL AND s.[owningteam] IS NOT NULL)
        OR (v.[owningteam] IS NOT NULL AND s.[owningteam] IS NULL)
        OR v.[owningteam_entitytype] <> s.[owningteam_entitytype]
            OR (v.[owningteam_entitytype] IS NULL AND s.[owningteam_entitytype] IS NOT NULL)
        OR (v.[owningteam_entitytype] IS NOT NULL AND s.[owningteam_entitytype] IS NULL)
        OR v.[owninguser] <> s.[owninguser]
            OR (v.[owninguser] IS NULL AND s.[owninguser] IS NOT NULL)
        OR (v.[owninguser] IS NOT NULL AND s.[owninguser] IS NULL)
        OR v.[owninguser_entitytype] <> s.[owninguser_entitytype]
            OR (v.[owninguser_entitytype] IS NULL AND s.[owninguser_entitytype] IS NOT NULL)
        OR (v.[owninguser_entitytype] IS NOT NULL AND s.[owninguser_entitytype] IS NULL)
        OR v.[prioritycode] <> s.[prioritycode]
            OR (v.[prioritycode] IS NULL AND s.[prioritycode] IS NOT NULL)
        OR (v.[prioritycode] IS NOT NULL AND s.[prioritycode] IS NULL)
        OR v.[processid] <> s.[processid]
            OR (v.[processid] IS NULL AND s.[processid] IS NOT NULL)
        OR (v.[processid] IS NOT NULL AND s.[processid] IS NULL)
        OR v.[regardingobjectid] <> s.[regardingobjectid]
            OR (v.[regardingobjectid] IS NULL AND s.[regardingobjectid] IS NOT NULL)
        OR (v.[regardingobjectid] IS NOT NULL AND s.[regardingobjectid] IS NULL)
        OR v.[regardingobjectid_entitytype] <> s.[regardingobjectid_entitytype]
            OR (v.[regardingobjectid_entitytype] IS NULL AND s.[regardingobjectid_entitytype] IS NOT NULL)
        OR (v.[regardingobjectid_entitytype] IS NOT NULL AND s.[regardingobjectid_entitytype] IS NULL)
        OR v.[regardingobjectidname] <> s.[regardingobjectidname]
            OR (v.[regardingobjectidname] IS NULL AND s.[regardingobjectidname] IS NOT NULL)
        OR (v.[regardingobjectidname] IS NOT NULL AND s.[regardingobjectidname] IS NULL)
        OR v.[regardingobjectidyominame] <> s.[regardingobjectidyominame]
            OR (v.[regardingobjectidyominame] IS NULL AND s.[regardingobjectidyominame] IS NOT NULL)
        OR (v.[regardingobjectidyominame] IS NOT NULL AND s.[regardingobjectidyominame] IS NULL)
        OR v.[regardingobjecttypecode] <> s.[regardingobjecttypecode]
            OR (v.[regardingobjecttypecode] IS NULL AND s.[regardingobjecttypecode] IS NOT NULL)
        OR (v.[regardingobjecttypecode] IS NOT NULL AND s.[regardingobjecttypecode] IS NULL)
        OR v.[requiredattendees] <> s.[requiredattendees]
            OR (v.[requiredattendees] IS NULL AND s.[requiredattendees] IS NOT NULL)
        OR (v.[requiredattendees] IS NOT NULL AND s.[requiredattendees] IS NULL)
        OR v.[resco_eventid] <> s.[resco_eventid]
            OR (v.[resco_eventid] IS NULL AND s.[resco_eventid] IS NOT NULL)
        OR (v.[resco_eventid] IS NOT NULL AND s.[resco_eventid] IS NULL)
        OR v.[resco_externalid] <> s.[resco_externalid]
            OR (v.[resco_externalid] IS NULL AND s.[resco_externalid] IS NOT NULL)
        OR (v.[resco_externalid] IS NOT NULL AND s.[resco_externalid] IS NULL)
        OR v.[resco_islocal] <> s.[resco_islocal]
            OR (v.[resco_islocal] IS NULL AND s.[resco_islocal] IS NOT NULL)
        OR (v.[resco_islocal] IS NOT NULL AND s.[resco_islocal] IS NULL)
        OR v.[resco_source] <> s.[resco_source]
            OR (v.[resco_source] IS NULL AND s.[resco_source] IS NOT NULL)
        OR (v.[resco_source] IS NOT NULL AND s.[resco_source] IS NULL)
        OR v.[safedescription] <> s.[safedescription]
            OR (v.[safedescription] IS NULL AND s.[safedescription] IS NOT NULL)
        OR (v.[safedescription] IS NOT NULL AND s.[safedescription] IS NULL)
        OR v.[scheduleddurationminutes] <> s.[scheduleddurationminutes]
            OR (v.[scheduleddurationminutes] IS NULL AND s.[scheduleddurationminutes] IS NOT NULL)
        OR (v.[scheduleddurationminutes] IS NOT NULL AND s.[scheduleddurationminutes] IS NULL)
        OR v.[scheduledend] <> s.[scheduledend]
            OR (v.[scheduledend] IS NULL AND s.[scheduledend] IS NOT NULL)
        OR (v.[scheduledend] IS NOT NULL AND s.[scheduledend] IS NULL)
        OR v.[scheduledstart] <> s.[scheduledstart]
            OR (v.[scheduledstart] IS NULL AND s.[scheduledstart] IS NOT NULL)
        OR (v.[scheduledstart] IS NOT NULL AND s.[scheduledstart] IS NULL)
        OR v.[seriesid] <> s.[seriesid]
            OR (v.[seriesid] IS NULL AND s.[seriesid] IS NOT NULL)
        OR (v.[seriesid] IS NOT NULL AND s.[seriesid] IS NULL)
        OR v.[serviceid] <> s.[serviceid]
            OR (v.[serviceid] IS NULL AND s.[serviceid] IS NOT NULL)
        OR (v.[serviceid] IS NOT NULL AND s.[serviceid] IS NULL)
        OR v.[serviceid_entitytype] <> s.[serviceid_entitytype]
            OR (v.[serviceid_entitytype] IS NULL AND s.[serviceid_entitytype] IS NOT NULL)
        OR (v.[serviceid_entitytype] IS NOT NULL AND s.[serviceid_entitytype] IS NULL)
        OR v.[SinkCreatedOn] <> s.[SinkCreatedOn]
            OR (v.[SinkCreatedOn] IS NULL AND s.[SinkCreatedOn] IS NOT NULL)
        OR (v.[SinkCreatedOn] IS NOT NULL AND s.[SinkCreatedOn] IS NULL)
        OR v.[SinkModifiedOn] <> s.[SinkModifiedOn]
            OR (v.[SinkModifiedOn] IS NULL AND s.[SinkModifiedOn] IS NOT NULL)
        OR (v.[SinkModifiedOn] IS NOT NULL AND s.[SinkModifiedOn] IS NULL)
        OR v.[slaid] <> s.[slaid]
            OR (v.[slaid] IS NULL AND s.[slaid] IS NOT NULL)
        OR (v.[slaid] IS NOT NULL AND s.[slaid] IS NULL)
        OR v.[slaid_entitytype] <> s.[slaid_entitytype]
            OR (v.[slaid_entitytype] IS NULL AND s.[slaid_entitytype] IS NOT NULL)
        OR (v.[slaid_entitytype] IS NOT NULL AND s.[slaid_entitytype] IS NULL)
        OR v.[slainvokedid] <> s.[slainvokedid]
            OR (v.[slainvokedid] IS NULL AND s.[slainvokedid] IS NOT NULL)
        OR (v.[slainvokedid] IS NOT NULL AND s.[slainvokedid] IS NULL)
        OR v.[slainvokedid_entitytype] <> s.[slainvokedid_entitytype]
            OR (v.[slainvokedid_entitytype] IS NULL AND s.[slainvokedid_entitytype] IS NOT NULL)
        OR (v.[slainvokedid_entitytype] IS NOT NULL AND s.[slainvokedid_entitytype] IS NULL)
        OR v.[slainvokedidname] <> s.[slainvokedidname]
            OR (v.[slainvokedidname] IS NULL AND s.[slainvokedidname] IS NOT NULL)
        OR (v.[slainvokedidname] IS NOT NULL AND s.[slainvokedidname] IS NULL)
        OR v.[slaname] <> s.[slaname]
            OR (v.[slaname] IS NULL AND s.[slaname] IS NOT NULL)
        OR (v.[slaname] IS NOT NULL AND s.[slaname] IS NULL)
        OR v.[sortdate] <> s.[sortdate]
            OR (v.[sortdate] IS NULL AND s.[sortdate] IS NOT NULL)
        OR (v.[sortdate] IS NOT NULL AND s.[sortdate] IS NULL)
        OR v.[stageid] <> s.[stageid]
            OR (v.[stageid] IS NULL AND s.[stageid] IS NOT NULL)
        OR (v.[stageid] IS NOT NULL AND s.[stageid] IS NULL)
        OR v.[statecode] <> s.[statecode]
            OR (v.[statecode] IS NULL AND s.[statecode] IS NOT NULL)
        OR (v.[statecode] IS NOT NULL AND s.[statecode] IS NULL)
        OR v.[statuscode] <> s.[statuscode]
            OR (v.[statuscode] IS NULL AND s.[statuscode] IS NOT NULL)
        OR (v.[statuscode] IS NOT NULL AND s.[statuscode] IS NULL)
        OR v.[subcategory] <> s.[subcategory]
            OR (v.[subcategory] IS NULL AND s.[subcategory] IS NOT NULL)
        OR (v.[subcategory] IS NOT NULL AND s.[subcategory] IS NULL)
        OR v.[subject] <> s.[subject]
            OR (v.[subject] IS NULL AND s.[subject] IS NOT NULL)
        OR (v.[subject] IS NOT NULL AND s.[subject] IS NULL)
        OR v.[subscriptionid] <> s.[subscriptionid]
            OR (v.[subscriptionid] IS NULL AND s.[subscriptionid] IS NOT NULL)
        OR (v.[subscriptionid] IS NOT NULL AND s.[subscriptionid] IS NULL)
        OR v.[timezoneruleversionnumber] <> s.[timezoneruleversionnumber]
            OR (v.[timezoneruleversionnumber] IS NULL AND s.[timezoneruleversionnumber] IS NOT NULL)
        OR (v.[timezoneruleversionnumber] IS NOT NULL AND s.[timezoneruleversionnumber] IS NULL)
        OR v.[transactioncurrencyid] <> s.[transactioncurrencyid]
            OR (v.[transactioncurrencyid] IS NULL AND s.[transactioncurrencyid] IS NOT NULL)
        OR (v.[transactioncurrencyid] IS NOT NULL AND s.[transactioncurrencyid] IS NULL)
        OR v.[transactioncurrencyid_entitytype] <> s.[transactioncurrencyid_entitytype]
            OR (v.[transactioncurrencyid_entitytype] IS NULL AND s.[transactioncurrencyid_entitytype] IS NOT NULL)
        OR (v.[transactioncurrencyid_entitytype] IS NOT NULL AND s.[transactioncurrencyid_entitytype] IS NULL)
        OR v.[transactioncurrencyidname] <> s.[transactioncurrencyidname]
            OR (v.[transactioncurrencyidname] IS NULL AND s.[transactioncurrencyidname] IS NOT NULL)
        OR (v.[transactioncurrencyidname] IS NOT NULL AND s.[transactioncurrencyidname] IS NULL)
        OR v.[traversedpath] <> s.[traversedpath]
            OR (v.[traversedpath] IS NULL AND s.[traversedpath] IS NOT NULL)
        OR (v.[traversedpath] IS NOT NULL AND s.[traversedpath] IS NULL)
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
            , [activityadditionalparams]
            , [activityid]
            , [activitytypecode]
            , [actualdurationminutes]
            , [actualend]
            , [actualstart]
            , [attachmentcount]
            , [attachmenterrors]
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
            , [exchangerate]
            , [globalobjectid]
            , [importsequencenumber]
            , [instancetypecode]
            , [isalldayevent]
            , [isbilled]
            , [isdraft]
            , [ismapiprivate]
            , [isregularactivity]
            , [isunsafe]
            , [isworkflowcreated]
            , [lastonholdtime]
            , [llp_importbatch]
            , [llp_reportingaccountid]
            , [llp_reportingaccountid_entitytype]
            , [llp_reportingaccountidname]
            , [llp_reportingaccountidyominame]
            , [location]
            , [modifiedby]
            , [modifiedby_entitytype]
            , [modifiedbyname]
            , [modifiedbyyominame]
            , [modifiedfieldsmask]
            , [modifiedon]
            , [modifiedonbehalfby]
            , [modifiedonbehalfby_entitytype]
            , [modifiedonbehalfbyname]
            , [modifiedonbehalfbyyominame]
            , [onholdtime]
            , [optionalattendees]
            , [organizer]
            , [originalstartdate]
            , [outlookownerapptid]
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
            , [prioritycode]
            , [processid]
            , [regardingobjectid]
            , [regardingobjectid_entitytype]
            , [regardingobjectidname]
            , [regardingobjectidyominame]
            , [regardingobjecttypecode]
            , [requiredattendees]
            , [resco_eventid]
            , [resco_externalid]
            , [resco_islocal]
            , [resco_source]
            , [safedescription]
            , [scheduleddurationminutes]
            , [scheduledend]
            , [scheduledstart]
            , [seriesid]
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
            , [transactioncurrencyid]
            , [transactioncurrencyid_entitytype]
            , [transactioncurrencyidname]
            , [traversedpath]
            , [utcconversiontimezonecode]
            , [versionnumber]
            , [DataSourceId]
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
            
    ) VALUES (
            s.[Id]
            , s.[activityadditionalparams]
            , s.[activityid]
            , s.[activitytypecode]
            , s.[actualdurationminutes]
            , s.[actualend]
            , s.[actualstart]
            , s.[attachmentcount]
            , s.[attachmenterrors]
            , s.[category]
            , s.[createdby]
            , s.[createdby_entitytype]
            , s.[createdbyname]
            , s.[createdbyyominame]
            , s.[createdon]
            , s.[createdonbehalfby]
            , s.[createdonbehalfby_entitytype]
            , s.[createdonbehalfbyname]
            , s.[createdonbehalfbyyominame]
            , s.[description]
            , s.[exchangerate]
            , s.[globalobjectid]
            , s.[importsequencenumber]
            , s.[instancetypecode]
            , s.[isalldayevent]
            , s.[isbilled]
            , s.[isdraft]
            , s.[ismapiprivate]
            , s.[isregularactivity]
            , s.[isunsafe]
            , s.[isworkflowcreated]
            , s.[lastonholdtime]
            , s.[llp_importbatch]
            , s.[llp_reportingaccountid]
            , s.[llp_reportingaccountid_entitytype]
            , s.[llp_reportingaccountidname]
            , s.[llp_reportingaccountidyominame]
            , s.[location]
            , s.[modifiedby]
            , s.[modifiedby_entitytype]
            , s.[modifiedbyname]
            , s.[modifiedbyyominame]
            , s.[modifiedfieldsmask]
            , s.[modifiedon]
            , s.[modifiedonbehalfby]
            , s.[modifiedonbehalfby_entitytype]
            , s.[modifiedonbehalfbyname]
            , s.[modifiedonbehalfbyyominame]
            , s.[onholdtime]
            , s.[optionalattendees]
            , s.[organizer]
            , s.[originalstartdate]
            , s.[outlookownerapptid]
            , s.[overriddencreatedon]
            , s.[ownerid]
            , s.[ownerid_entitytype]
            , s.[owneridname]
            , s.[owneridtype]
            , s.[owneridyominame]
            , s.[owningbusinessunit]
            , s.[owningbusinessunit_entitytype]
            , s.[owningteam]
            , s.[owningteam_entitytype]
            , s.[owninguser]
            , s.[owninguser_entitytype]
            , s.[prioritycode]
            , s.[processid]
            , s.[regardingobjectid]
            , s.[regardingobjectid_entitytype]
            , s.[regardingobjectidname]
            , s.[regardingobjectidyominame]
            , s.[regardingobjecttypecode]
            , s.[requiredattendees]
            , s.[resco_eventid]
            , s.[resco_externalid]
            , s.[resco_islocal]
            , s.[resco_source]
            , s.[safedescription]
            , s.[scheduleddurationminutes]
            , s.[scheduledend]
            , s.[scheduledstart]
            , s.[seriesid]
            , s.[serviceid]
            , s.[serviceid_entitytype]
            , s.[SinkCreatedOn]
            , s.[SinkModifiedOn]
            , s.[slaid]
            , s.[slaid_entitytype]
            , s.[slainvokedid]
            , s.[slainvokedid_entitytype]
            , s.[slainvokedidname]
            , s.[slaname]
            , s.[sortdate]
            , s.[stageid]
            , s.[statecode]
            , s.[statuscode]
            , s.[subcategory]
            , s.[subject]
            , s.[subscriptionid]
            , s.[timezoneruleversionnumber]
            , s.[transactioncurrencyid]
            , s.[transactioncurrencyid_entitytype]
            , s.[transactioncurrencyidname]
            , s.[traversedpath]
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
    
    INSERT INTO [Vault].[CRMdboAppointment] (
            [Id]
            , [activityadditionalparams]
            , [activityid]
            , [activitytypecode]
            , [actualdurationminutes]
            , [actualend]
            , [actualstart]
            , [attachmentcount]
            , [attachmenterrors]
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
            , [exchangerate]
            , [globalobjectid]
            , [importsequencenumber]
            , [instancetypecode]
            , [isalldayevent]
            , [isbilled]
            , [isdraft]
            , [ismapiprivate]
            , [isregularactivity]
            , [isunsafe]
            , [isworkflowcreated]
            , [lastonholdtime]
            , [llp_importbatch]
            , [llp_reportingaccountid]
            , [llp_reportingaccountid_entitytype]
            , [llp_reportingaccountidname]
            , [llp_reportingaccountidyominame]
            , [location]
            , [modifiedby]
            , [modifiedby_entitytype]
            , [modifiedbyname]
            , [modifiedbyyominame]
            , [modifiedfieldsmask]
            , [modifiedon]
            , [modifiedonbehalfby]
            , [modifiedonbehalfby_entitytype]
            , [modifiedonbehalfbyname]
            , [modifiedonbehalfbyyominame]
            , [onholdtime]
            , [optionalattendees]
            , [organizer]
            , [originalstartdate]
            , [outlookownerapptid]
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
            , [prioritycode]
            , [processid]
            , [regardingobjectid]
            , [regardingobjectid_entitytype]
            , [regardingobjectidname]
            , [regardingobjectidyominame]
            , [regardingobjecttypecode]
            , [requiredattendees]
            , [resco_eventid]
            , [resco_externalid]
            , [resco_islocal]
            , [resco_source]
            , [safedescription]
            , [scheduleddurationminutes]
            , [scheduledend]
            , [scheduledstart]
            , [seriesid]
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
            , [transactioncurrencyid]
            , [transactioncurrencyid_entitytype]
            , [transactioncurrencyidname]
            , [traversedpath]
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
            , s.[activityadditionalparams]
            , s.[activityid]
            , s.[activitytypecode]
            , s.[actualdurationminutes]
            , s.[actualend]
            , s.[actualstart]
            , s.[attachmentcount]
            , s.[attachmenterrors]
            , s.[category]
            , s.[createdby]
            , s.[createdby_entitytype]
            , s.[createdbyname]
            , s.[createdbyyominame]
            , s.[createdon]
            , s.[createdonbehalfby]
            , s.[createdonbehalfby_entitytype]
            , s.[createdonbehalfbyname]
            , s.[createdonbehalfbyyominame]
            , s.[description]
            , s.[exchangerate]
            , s.[globalobjectid]
            , s.[importsequencenumber]
            , s.[instancetypecode]
            , s.[isalldayevent]
            , s.[isbilled]
            , s.[isdraft]
            , s.[ismapiprivate]
            , s.[isregularactivity]
            , s.[isunsafe]
            , s.[isworkflowcreated]
            , s.[lastonholdtime]
            , s.[llp_importbatch]
            , s.[llp_reportingaccountid]
            , s.[llp_reportingaccountid_entitytype]
            , s.[llp_reportingaccountidname]
            , s.[llp_reportingaccountidyominame]
            , s.[location]
            , s.[modifiedby]
            , s.[modifiedby_entitytype]
            , s.[modifiedbyname]
            , s.[modifiedbyyominame]
            , s.[modifiedfieldsmask]
            , s.[modifiedon]
            , s.[modifiedonbehalfby]
            , s.[modifiedonbehalfby_entitytype]
            , s.[modifiedonbehalfbyname]
            , s.[modifiedonbehalfbyyominame]
            , s.[onholdtime]
            , s.[optionalattendees]
            , s.[organizer]
            , s.[originalstartdate]
            , s.[outlookownerapptid]
            , s.[overriddencreatedon]
            , s.[ownerid]
            , s.[ownerid_entitytype]
            , s.[owneridname]
            , s.[owneridtype]
            , s.[owneridyominame]
            , s.[owningbusinessunit]
            , s.[owningbusinessunit_entitytype]
            , s.[owningteam]
            , s.[owningteam_entitytype]
            , s.[owninguser]
            , s.[owninguser_entitytype]
            , s.[prioritycode]
            , s.[processid]
            , s.[regardingobjectid]
            , s.[regardingobjectid_entitytype]
            , s.[regardingobjectidname]
            , s.[regardingobjectidyominame]
            , s.[regardingobjecttypecode]
            , s.[requiredattendees]
            , s.[resco_eventid]
            , s.[resco_externalid]
            , s.[resco_islocal]
            , s.[resco_source]
            , s.[safedescription]
            , s.[scheduleddurationminutes]
            , s.[scheduledend]
            , s.[scheduledstart]
            , s.[seriesid]
            , s.[serviceid]
            , s.[serviceid_entitytype]
            , s.[SinkCreatedOn]
            , s.[SinkModifiedOn]
            , s.[slaid]
            , s.[slaid_entitytype]
            , s.[slainvokedid]
            , s.[slainvokedid_entitytype]
            , s.[slainvokedidname]
            , s.[slaname]
            , s.[sortdate]
            , s.[stageid]
            , s.[statecode]
            , s.[statuscode]
            , s.[subcategory]
            , s.[subject]
            , s.[subscriptionid]
            , s.[timezoneruleversionnumber]
            , s.[transactioncurrencyid]
            , s.[transactioncurrencyid_entitytype]
            , s.[transactioncurrencyidname]
            , s.[traversedpath]
            , s.[utcconversiontimezonecode]
            , s.[versionnumber]
            , s.[DataSourceId]
            , @ThreadLogId
            , -1
            , -1
            , N'U' -- update
    FROM Stage.CRMdboAppointment AS s
    INNER JOIN Vault.CRMdboAppointment AS v
        ON  s.[Id] = v.[Id] AND v.ThreadLogUpdateId = @ThreadLogId
    
    INSERT INTO [Vault].[CRMdboAppointment] (
            [Id]
            , [activityadditionalparams]
            , [activityid]
            , [activitytypecode]
            , [actualdurationminutes]
            , [actualend]
            , [actualstart]
            , [attachmentcount]
            , [attachmenterrors]
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
            , [exchangerate]
            , [globalobjectid]
            , [importsequencenumber]
            , [instancetypecode]
            , [isalldayevent]
            , [isbilled]
            , [isdraft]
            , [ismapiprivate]
            , [isregularactivity]
            , [isunsafe]
            , [isworkflowcreated]
            , [lastonholdtime]
            , [llp_importbatch]
            , [llp_reportingaccountid]
            , [llp_reportingaccountid_entitytype]
            , [llp_reportingaccountidname]
            , [llp_reportingaccountidyominame]
            , [location]
            , [modifiedby]
            , [modifiedby_entitytype]
            , [modifiedbyname]
            , [modifiedbyyominame]
            , [modifiedfieldsmask]
            , [modifiedon]
            , [modifiedonbehalfby]
            , [modifiedonbehalfby_entitytype]
            , [modifiedonbehalfbyname]
            , [modifiedonbehalfbyyominame]
            , [onholdtime]
            , [optionalattendees]
            , [organizer]
            , [originalstartdate]
            , [outlookownerapptid]
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
            , [prioritycode]
            , [processid]
            , [regardingobjectid]
            , [regardingobjectid_entitytype]
            , [regardingobjectidname]
            , [regardingobjectidyominame]
            , [regardingobjecttypecode]
            , [requiredattendees]
            , [resco_eventid]
            , [resco_externalid]
            , [resco_islocal]
            , [resco_source]
            , [safedescription]
            , [scheduleddurationminutes]
            , [scheduledend]
            , [scheduledstart]
            , [seriesid]
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
            , [transactioncurrencyid]
            , [transactioncurrencyid_entitytype]
            , [transactioncurrencyidname]
            , [traversedpath]
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
            , v.[activityadditionalparams]
            , v.[activityid]
            , v.[activitytypecode]
            , v.[actualdurationminutes]
            , v.[actualend]
            , v.[actualstart]
            , v.[attachmentcount]
            , v.[attachmenterrors]
            , v.[category]
            , v.[createdby]
            , v.[createdby_entitytype]
            , v.[createdbyname]
            , v.[createdbyyominame]
            , v.[createdon]
            , v.[createdonbehalfby]
            , v.[createdonbehalfby_entitytype]
            , v.[createdonbehalfbyname]
            , v.[createdonbehalfbyyominame]
            , v.[description]
            , v.[exchangerate]
            , v.[globalobjectid]
            , v.[importsequencenumber]
            , v.[instancetypecode]
            , v.[isalldayevent]
            , v.[isbilled]
            , v.[isdraft]
            , v.[ismapiprivate]
            , v.[isregularactivity]
            , v.[isunsafe]
            , v.[isworkflowcreated]
            , v.[lastonholdtime]
            , v.[llp_importbatch]
            , v.[llp_reportingaccountid]
            , v.[llp_reportingaccountid_entitytype]
            , v.[llp_reportingaccountidname]
            , v.[llp_reportingaccountidyominame]
            , v.[location]
            , v.[modifiedby]
            , v.[modifiedby_entitytype]
            , v.[modifiedbyname]
            , v.[modifiedbyyominame]
            , v.[modifiedfieldsmask]
            , v.[modifiedon]
            , v.[modifiedonbehalfby]
            , v.[modifiedonbehalfby_entitytype]
            , v.[modifiedonbehalfbyname]
            , v.[modifiedonbehalfbyyominame]
            , v.[onholdtime]
            , v.[optionalattendees]
            , v.[organizer]
            , v.[originalstartdate]
            , v.[outlookownerapptid]
            , v.[overriddencreatedon]
            , v.[ownerid]
            , v.[ownerid_entitytype]
            , v.[owneridname]
            , v.[owneridtype]
            , v.[owneridyominame]
            , v.[owningbusinessunit]
            , v.[owningbusinessunit_entitytype]
            , v.[owningteam]
            , v.[owningteam_entitytype]
            , v.[owninguser]
            , v.[owninguser_entitytype]
            , v.[prioritycode]
            , v.[processid]
            , v.[regardingobjectid]
            , v.[regardingobjectid_entitytype]
            , v.[regardingobjectidname]
            , v.[regardingobjectidyominame]
            , v.[regardingobjecttypecode]
            , v.[requiredattendees]
            , v.[resco_eventid]
            , v.[resco_externalid]
            , v.[resco_islocal]
            , v.[resco_source]
            , v.[safedescription]
            , v.[scheduleddurationminutes]
            , v.[scheduledend]
            , v.[scheduledstart]
            , v.[seriesid]
            , v.[serviceid]
            , v.[serviceid_entitytype]
            , v.[SinkCreatedOn]
            , v.[SinkModifiedOn]
            , v.[slaid]
            , v.[slaid_entitytype]
            , v.[slainvokedid]
            , v.[slainvokedid_entitytype]
            , v.[slainvokedidname]
            , v.[slaname]
            , v.[sortdate]
            , v.[stageid]
            , v.[statecode]
            , v.[statuscode]
            , v.[subcategory]
            , v.[subject]
            , v.[subscriptionid]
            , v.[timezoneruleversionnumber]
            , v.[transactioncurrencyid]
            , v.[transactioncurrencyid_entitytype]
            , v.[transactioncurrencyidname]
            , v.[traversedpath]
            , v.[utcconversiontimezonecode]
            , v.[versionnumber]
            , v.[DataSourceId]
            , @ThreadLogId
            , -1
            , -1
            , N'D' -- update
    FROM Vault.CRMdboAppointment AS v
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
                , TableFinalRowCount = (SELECT COUNT(*) FROM [Vault].[CRMdboAppointment] WITH (NOLOCK))
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
