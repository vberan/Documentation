Stored Procedure Vault.uspLoadCRMdboEmail {#spVaultuspLoadCRMdboEmail}
-----------------------------------------

Definition of Stored procedure:

``` {.sql}
CREATE PROCEDURE [Vault].[uspLoadCRMdboEmail] 
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
            SET TableInitialRowCount = (SELECT COUNT(*) FROM [Vault].[CRMdboEmail] WITH (NOLOCK))
        WHERE ThreadLogId = @ThreadLogId;

            BEGIN TRANSACTION;

    
        MERGE INTO [Vault].[CRMdboEmail] AS v
        USING [Stage].[CRMdboEmail] AS s
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
        OR v.[attachmentopencount] <> s.[attachmentopencount]
            OR (v.[attachmentopencount] IS NULL AND s.[attachmentopencount] IS NOT NULL)
        OR (v.[attachmentopencount] IS NOT NULL AND s.[attachmentopencount] IS NULL)
        OR v.[baseconversationindexhash] <> s.[baseconversationindexhash]
            OR (v.[baseconversationindexhash] IS NULL AND s.[baseconversationindexhash] IS NOT NULL)
        OR (v.[baseconversationindexhash] IS NOT NULL AND s.[baseconversationindexhash] IS NULL)
        OR v.[bcc] <> s.[bcc]
            OR (v.[bcc] IS NULL AND s.[bcc] IS NOT NULL)
        OR (v.[bcc] IS NOT NULL AND s.[bcc] IS NULL)
        OR v.[category] <> s.[category]
            OR (v.[category] IS NULL AND s.[category] IS NOT NULL)
        OR (v.[category] IS NOT NULL AND s.[category] IS NULL)
        OR v.[cc] <> s.[cc]
            OR (v.[cc] IS NULL AND s.[cc] IS NOT NULL)
        OR (v.[cc] IS NOT NULL AND s.[cc] IS NULL)
        OR v.[compressed] <> s.[compressed]
            OR (v.[compressed] IS NULL AND s.[compressed] IS NOT NULL)
        OR (v.[compressed] IS NOT NULL AND s.[compressed] IS NULL)
        OR v.[conversationindex] <> s.[conversationindex]
            OR (v.[conversationindex] IS NULL AND s.[conversationindex] IS NOT NULL)
        OR (v.[conversationindex] IS NOT NULL AND s.[conversationindex] IS NULL)
        OR v.[conversationtrackingid] <> s.[conversationtrackingid]
            OR (v.[conversationtrackingid] IS NULL AND s.[conversationtrackingid] IS NOT NULL)
        OR (v.[conversationtrackingid] IS NOT NULL AND s.[conversationtrackingid] IS NULL)
        OR v.[correlationmethod] <> s.[correlationmethod]
            OR (v.[correlationmethod] IS NULL AND s.[correlationmethod] IS NOT NULL)
        OR (v.[correlationmethod] IS NOT NULL AND s.[correlationmethod] IS NULL)
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
        OR v.[delayedemailsendtime] <> s.[delayedemailsendtime]
            OR (v.[delayedemailsendtime] IS NULL AND s.[delayedemailsendtime] IS NOT NULL)
        OR (v.[delayedemailsendtime] IS NOT NULL AND s.[delayedemailsendtime] IS NULL)
        OR v.[deliveryattempts] <> s.[deliveryattempts]
            OR (v.[deliveryattempts] IS NULL AND s.[deliveryattempts] IS NOT NULL)
        OR (v.[deliveryattempts] IS NOT NULL AND s.[deliveryattempts] IS NULL)
        OR v.[deliveryprioritycode] <> s.[deliveryprioritycode]
            OR (v.[deliveryprioritycode] IS NULL AND s.[deliveryprioritycode] IS NOT NULL)
        OR (v.[deliveryprioritycode] IS NOT NULL AND s.[deliveryprioritycode] IS NULL)
        OR v.[deliveryreceiptrequested] <> s.[deliveryreceiptrequested]
            OR (v.[deliveryreceiptrequested] IS NULL AND s.[deliveryreceiptrequested] IS NOT NULL)
        OR (v.[deliveryreceiptrequested] IS NOT NULL AND s.[deliveryreceiptrequested] IS NULL)
        OR v.[description] <> s.[description]
            OR (v.[description] IS NULL AND s.[description] IS NOT NULL)
        OR (v.[description] IS NOT NULL AND s.[description] IS NULL)
        OR v.[directioncode] <> s.[directioncode]
            OR (v.[directioncode] IS NULL AND s.[directioncode] IS NOT NULL)
        OR (v.[directioncode] IS NOT NULL AND s.[directioncode] IS NULL)
        OR v.[emailreminderexpirytime] <> s.[emailreminderexpirytime]
            OR (v.[emailreminderexpirytime] IS NULL AND s.[emailreminderexpirytime] IS NOT NULL)
        OR (v.[emailreminderexpirytime] IS NOT NULL AND s.[emailreminderexpirytime] IS NULL)
        OR v.[emailreminderstatus] <> s.[emailreminderstatus]
            OR (v.[emailreminderstatus] IS NULL AND s.[emailreminderstatus] IS NOT NULL)
        OR (v.[emailreminderstatus] IS NOT NULL AND s.[emailreminderstatus] IS NULL)
        OR v.[emailremindertext] <> s.[emailremindertext]
            OR (v.[emailremindertext] IS NULL AND s.[emailremindertext] IS NOT NULL)
        OR (v.[emailremindertext] IS NOT NULL AND s.[emailremindertext] IS NULL)
        OR v.[emailremindertype] <> s.[emailremindertype]
            OR (v.[emailremindertype] IS NULL AND s.[emailremindertype] IS NOT NULL)
        OR (v.[emailremindertype] IS NOT NULL AND s.[emailremindertype] IS NULL)
        OR v.[emailsender] <> s.[emailsender]
            OR (v.[emailsender] IS NULL AND s.[emailsender] IS NOT NULL)
        OR (v.[emailsender] IS NOT NULL AND s.[emailsender] IS NULL)
        OR v.[emailsender_entitytype] <> s.[emailsender_entitytype]
            OR (v.[emailsender_entitytype] IS NULL AND s.[emailsender_entitytype] IS NOT NULL)
        OR (v.[emailsender_entitytype] IS NOT NULL AND s.[emailsender_entitytype] IS NULL)
        OR v.[emailsendername] <> s.[emailsendername]
            OR (v.[emailsendername] IS NULL AND s.[emailsendername] IS NOT NULL)
        OR (v.[emailsendername] IS NOT NULL AND s.[emailsendername] IS NULL)
        OR v.[emailsenderobjecttypecode] <> s.[emailsenderobjecttypecode]
            OR (v.[emailsenderobjecttypecode] IS NULL AND s.[emailsenderobjecttypecode] IS NOT NULL)
        OR (v.[emailsenderobjecttypecode] IS NOT NULL AND s.[emailsenderobjecttypecode] IS NULL)
        OR v.[emailsenderyominame] <> s.[emailsenderyominame]
            OR (v.[emailsenderyominame] IS NULL AND s.[emailsenderyominame] IS NOT NULL)
        OR (v.[emailsenderyominame] IS NOT NULL AND s.[emailsenderyominame] IS NULL)
        OR v.[emailtrackingid] <> s.[emailtrackingid]
            OR (v.[emailtrackingid] IS NULL AND s.[emailtrackingid] IS NOT NULL)
        OR (v.[emailtrackingid] IS NOT NULL AND s.[emailtrackingid] IS NULL)
        OR v.[exchangerate] <> s.[exchangerate]
            OR (v.[exchangerate] IS NULL AND s.[exchangerate] IS NOT NULL)
        OR (v.[exchangerate] IS NOT NULL AND s.[exchangerate] IS NULL)
        OR v.[followemailuserpreference] <> s.[followemailuserpreference]
            OR (v.[followemailuserpreference] IS NULL AND s.[followemailuserpreference] IS NOT NULL)
        OR (v.[followemailuserpreference] IS NOT NULL AND s.[followemailuserpreference] IS NULL)
        OR v.[from] <> s.[from]
            OR (v.[from] IS NULL AND s.[from] IS NOT NULL)
        OR (v.[from] IS NOT NULL AND s.[from] IS NULL)
        OR v.[importsequencenumber] <> s.[importsequencenumber]
            OR (v.[importsequencenumber] IS NULL AND s.[importsequencenumber] IS NOT NULL)
        OR (v.[importsequencenumber] IS NOT NULL AND s.[importsequencenumber] IS NULL)
        OR v.[inreplyto] <> s.[inreplyto]
            OR (v.[inreplyto] IS NULL AND s.[inreplyto] IS NOT NULL)
        OR (v.[inreplyto] IS NOT NULL AND s.[inreplyto] IS NULL)
        OR v.[isbilled] <> s.[isbilled]
            OR (v.[isbilled] IS NULL AND s.[isbilled] IS NOT NULL)
        OR (v.[isbilled] IS NOT NULL AND s.[isbilled] IS NULL)
        OR v.[isemailfollowed] <> s.[isemailfollowed]
            OR (v.[isemailfollowed] IS NULL AND s.[isemailfollowed] IS NOT NULL)
        OR (v.[isemailfollowed] IS NOT NULL AND s.[isemailfollowed] IS NULL)
        OR v.[isemailreminderset] <> s.[isemailreminderset]
            OR (v.[isemailreminderset] IS NULL AND s.[isemailreminderset] IS NOT NULL)
        OR (v.[isemailreminderset] IS NOT NULL AND s.[isemailreminderset] IS NULL)
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
        OR v.[lastopenedtime] <> s.[lastopenedtime]
            OR (v.[lastopenedtime] IS NULL AND s.[lastopenedtime] IS NOT NULL)
        OR (v.[lastopenedtime] IS NOT NULL AND s.[lastopenedtime] IS NULL)
        OR v.[linksclickedcount] <> s.[linksclickedcount]
            OR (v.[linksclickedcount] IS NULL AND s.[linksclickedcount] IS NOT NULL)
        OR (v.[linksclickedcount] IS NOT NULL AND s.[linksclickedcount] IS NULL)
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
        OR v.[messageid] <> s.[messageid]
            OR (v.[messageid] IS NULL AND s.[messageid] IS NOT NULL)
        OR (v.[messageid] IS NOT NULL AND s.[messageid] IS NULL)
        OR v.[messageiddupcheck] <> s.[messageiddupcheck]
            OR (v.[messageiddupcheck] IS NULL AND s.[messageiddupcheck] IS NOT NULL)
        OR (v.[messageiddupcheck] IS NOT NULL AND s.[messageiddupcheck] IS NULL)
        OR v.[mimetype] <> s.[mimetype]
            OR (v.[mimetype] IS NULL AND s.[mimetype] IS NOT NULL)
        OR (v.[mimetype] IS NOT NULL AND s.[mimetype] IS NULL)
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
        OR v.[notifications] <> s.[notifications]
            OR (v.[notifications] IS NULL AND s.[notifications] IS NOT NULL)
        OR (v.[notifications] IS NOT NULL AND s.[notifications] IS NULL)
        OR v.[onholdtime] <> s.[onholdtime]
            OR (v.[onholdtime] IS NULL AND s.[onholdtime] IS NOT NULL)
        OR (v.[onholdtime] IS NOT NULL AND s.[onholdtime] IS NULL)
        OR v.[opencount] <> s.[opencount]
            OR (v.[opencount] IS NULL AND s.[opencount] IS NOT NULL)
        OR (v.[opencount] IS NOT NULL AND s.[opencount] IS NULL)
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
        OR v.[parentactivityid] <> s.[parentactivityid]
            OR (v.[parentactivityid] IS NULL AND s.[parentactivityid] IS NOT NULL)
        OR (v.[parentactivityid] IS NOT NULL AND s.[parentactivityid] IS NULL)
        OR v.[parentactivityid_entitytype] <> s.[parentactivityid_entitytype]
            OR (v.[parentactivityid_entitytype] IS NULL AND s.[parentactivityid_entitytype] IS NOT NULL)
        OR (v.[parentactivityid_entitytype] IS NOT NULL AND s.[parentactivityid_entitytype] IS NULL)
        OR v.[parentactivityidname] <> s.[parentactivityidname]
            OR (v.[parentactivityidname] IS NULL AND s.[parentactivityidname] IS NOT NULL)
        OR (v.[parentactivityidname] IS NOT NULL AND s.[parentactivityidname] IS NULL)
        OR v.[postponeemailprocessinguntil] <> s.[postponeemailprocessinguntil]
            OR (v.[postponeemailprocessinguntil] IS NULL AND s.[postponeemailprocessinguntil] IS NOT NULL)
        OR (v.[postponeemailprocessinguntil] IS NOT NULL AND s.[postponeemailprocessinguntil] IS NULL)
        OR v.[prioritycode] <> s.[prioritycode]
            OR (v.[prioritycode] IS NULL AND s.[prioritycode] IS NOT NULL)
        OR (v.[prioritycode] IS NOT NULL AND s.[prioritycode] IS NULL)
        OR v.[processid] <> s.[processid]
            OR (v.[processid] IS NULL AND s.[processid] IS NOT NULL)
        OR (v.[processid] IS NOT NULL AND s.[processid] IS NULL)
        OR v.[readreceiptrequested] <> s.[readreceiptrequested]
            OR (v.[readreceiptrequested] IS NULL AND s.[readreceiptrequested] IS NOT NULL)
        OR (v.[readreceiptrequested] IS NOT NULL AND s.[readreceiptrequested] IS NULL)
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
        OR v.[reminderactioncardid] <> s.[reminderactioncardid]
            OR (v.[reminderactioncardid] IS NULL AND s.[reminderactioncardid] IS NOT NULL)
        OR (v.[reminderactioncardid] IS NOT NULL AND s.[reminderactioncardid] IS NULL)
        OR v.[replycount] <> s.[replycount]
            OR (v.[replycount] IS NULL AND s.[replycount] IS NOT NULL)
        OR (v.[replycount] IS NOT NULL AND s.[replycount] IS NULL)
        OR v.[resco_contentstatus] <> s.[resco_contentstatus]
            OR (v.[resco_contentstatus] IS NULL AND s.[resco_contentstatus] IS NOT NULL)
        OR (v.[resco_contentstatus] IS NOT NULL AND s.[resco_contentstatus] IS NULL)
        OR v.[resco_createdas] <> s.[resco_createdas]
            OR (v.[resco_createdas] IS NULL AND s.[resco_createdas] IS NOT NULL)
        OR (v.[resco_createdas] IS NOT NULL AND s.[resco_createdas] IS NULL)
        OR v.[resco_createdfrom] <> s.[resco_createdfrom]
            OR (v.[resco_createdfrom] IS NULL AND s.[resco_createdfrom] IS NOT NULL)
        OR (v.[resco_createdfrom] IS NOT NULL AND s.[resco_createdfrom] IS NULL)
        OR v.[resco_emailid] <> s.[resco_emailid]
            OR (v.[resco_emailid] IS NULL AND s.[resco_emailid] IS NOT NULL)
        OR (v.[resco_emailid] IS NOT NULL AND s.[resco_emailid] IS NULL)
        OR v.[resco_eventid] <> s.[resco_eventid]
            OR (v.[resco_eventid] IS NULL AND s.[resco_eventid] IS NOT NULL)
        OR (v.[resco_eventid] IS NOT NULL AND s.[resco_eventid] IS NULL)
        OR v.[resco_islocal] <> s.[resco_islocal]
            OR (v.[resco_islocal] IS NULL AND s.[resco_islocal] IS NOT NULL)
        OR (v.[resco_islocal] IS NOT NULL AND s.[resco_islocal] IS NULL)
        OR v.[resco_snippet] <> s.[resco_snippet]
            OR (v.[resco_snippet] IS NULL AND s.[resco_snippet] IS NOT NULL)
        OR (v.[resco_snippet] IS NOT NULL AND s.[resco_snippet] IS NULL)
        OR v.[resco_source] <> s.[resco_source]
            OR (v.[resco_source] IS NULL AND s.[resco_source] IS NOT NULL)
        OR (v.[resco_source] IS NOT NULL AND s.[resco_source] IS NULL)
        OR v.[resco_statuscode] <> s.[resco_statuscode]
            OR (v.[resco_statuscode] IS NULL AND s.[resco_statuscode] IS NOT NULL)
        OR (v.[resco_statuscode] IS NOT NULL AND s.[resco_statuscode] IS NULL)
        OR v.[resco_threadid] <> s.[resco_threadid]
            OR (v.[resco_threadid] IS NULL AND s.[resco_threadid] IS NOT NULL)
        OR (v.[resco_threadid] IS NOT NULL AND s.[resco_threadid] IS NULL)
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
        OR v.[sender] <> s.[sender]
            OR (v.[sender] IS NULL AND s.[sender] IS NOT NULL)
        OR (v.[sender] IS NOT NULL AND s.[sender] IS NULL)
        OR v.[sendermailboxid] <> s.[sendermailboxid]
            OR (v.[sendermailboxid] IS NULL AND s.[sendermailboxid] IS NOT NULL)
        OR (v.[sendermailboxid] IS NOT NULL AND s.[sendermailboxid] IS NULL)
        OR v.[sendermailboxid_entitytype] <> s.[sendermailboxid_entitytype]
            OR (v.[sendermailboxid_entitytype] IS NULL AND s.[sendermailboxid_entitytype] IS NOT NULL)
        OR (v.[sendermailboxid_entitytype] IS NOT NULL AND s.[sendermailboxid_entitytype] IS NULL)
        OR v.[sendermailboxidname] <> s.[sendermailboxidname]
            OR (v.[sendermailboxidname] IS NULL AND s.[sendermailboxidname] IS NOT NULL)
        OR (v.[sendermailboxidname] IS NOT NULL AND s.[sendermailboxidname] IS NULL)
        OR v.[sendersaccount] <> s.[sendersaccount]
            OR (v.[sendersaccount] IS NULL AND s.[sendersaccount] IS NOT NULL)
        OR (v.[sendersaccount] IS NOT NULL AND s.[sendersaccount] IS NULL)
        OR v.[sendersaccount_entitytype] <> s.[sendersaccount_entitytype]
            OR (v.[sendersaccount_entitytype] IS NULL AND s.[sendersaccount_entitytype] IS NOT NULL)
        OR (v.[sendersaccount_entitytype] IS NOT NULL AND s.[sendersaccount_entitytype] IS NULL)
        OR v.[sendersaccountname] <> s.[sendersaccountname]
            OR (v.[sendersaccountname] IS NULL AND s.[sendersaccountname] IS NOT NULL)
        OR (v.[sendersaccountname] IS NOT NULL AND s.[sendersaccountname] IS NULL)
        OR v.[sendersaccountobjecttypecode] <> s.[sendersaccountobjecttypecode]
            OR (v.[sendersaccountobjecttypecode] IS NULL AND s.[sendersaccountobjecttypecode] IS NOT NULL)
        OR (v.[sendersaccountobjecttypecode] IS NOT NULL AND s.[sendersaccountobjecttypecode] IS NULL)
        OR v.[sendersaccountyominame] <> s.[sendersaccountyominame]
            OR (v.[sendersaccountyominame] IS NULL AND s.[sendersaccountyominame] IS NOT NULL)
        OR (v.[sendersaccountyominame] IS NOT NULL AND s.[sendersaccountyominame] IS NULL)
        OR v.[senton] <> s.[senton]
            OR (v.[senton] IS NULL AND s.[senton] IS NOT NULL)
        OR (v.[senton] IS NOT NULL AND s.[senton] IS NULL)
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
        OR v.[submittedby] <> s.[submittedby]
            OR (v.[submittedby] IS NULL AND s.[submittedby] IS NOT NULL)
        OR (v.[submittedby] IS NOT NULL AND s.[submittedby] IS NULL)
        OR v.[templateid] <> s.[templateid]
            OR (v.[templateid] IS NULL AND s.[templateid] IS NOT NULL)
        OR (v.[templateid] IS NOT NULL AND s.[templateid] IS NULL)
        OR v.[templateid_entitytype] <> s.[templateid_entitytype]
            OR (v.[templateid_entitytype] IS NULL AND s.[templateid_entitytype] IS NOT NULL)
        OR (v.[templateid_entitytype] IS NOT NULL AND s.[templateid_entitytype] IS NULL)
        OR v.[templateidname] <> s.[templateidname]
            OR (v.[templateidname] IS NULL AND s.[templateidname] IS NOT NULL)
        OR (v.[templateidname] IS NOT NULL AND s.[templateidname] IS NULL)
        OR v.[timezoneruleversionnumber] <> s.[timezoneruleversionnumber]
            OR (v.[timezoneruleversionnumber] IS NULL AND s.[timezoneruleversionnumber] IS NOT NULL)
        OR (v.[timezoneruleversionnumber] IS NOT NULL AND s.[timezoneruleversionnumber] IS NULL)
        OR v.[to] <> s.[to]
            OR (v.[to] IS NULL AND s.[to] IS NOT NULL)
        OR (v.[to] IS NOT NULL AND s.[to] IS NULL)
        OR v.[torecipients] <> s.[torecipients]
            OR (v.[torecipients] IS NULL AND s.[torecipients] IS NOT NULL)
        OR (v.[torecipients] IS NOT NULL AND s.[torecipients] IS NULL)
        OR v.[trackingtoken] <> s.[trackingtoken]
            OR (v.[trackingtoken] IS NULL AND s.[trackingtoken] IS NOT NULL)
        OR (v.[trackingtoken] IS NOT NULL AND s.[trackingtoken] IS NULL)
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
            , [attachmentopencount]
            , [baseconversationindexhash]
            , [bcc]
            , [category]
            , [cc]
            , [compressed]
            , [conversationindex]
            , [conversationtrackingid]
            , [correlationmethod]
            , [createdby]
            , [createdby_entitytype]
            , [createdbyname]
            , [createdbyyominame]
            , [createdon]
            , [createdonbehalfby]
            , [createdonbehalfby_entitytype]
            , [createdonbehalfbyname]
            , [createdonbehalfbyyominame]
            , [delayedemailsendtime]
            , [deliveryattempts]
            , [deliveryprioritycode]
            , [deliveryreceiptrequested]
            , [description]
            , [directioncode]
            , [emailreminderexpirytime]
            , [emailreminderstatus]
            , [emailremindertext]
            , [emailremindertype]
            , [emailsender]
            , [emailsender_entitytype]
            , [emailsendername]
            , [emailsenderobjecttypecode]
            , [emailsenderyominame]
            , [emailtrackingid]
            , [exchangerate]
            , [followemailuserpreference]
            , [from]
            , [importsequencenumber]
            , [inreplyto]
            , [isbilled]
            , [isemailfollowed]
            , [isemailreminderset]
            , [isregularactivity]
            , [isunsafe]
            , [isworkflowcreated]
            , [lastonholdtime]
            , [lastopenedtime]
            , [linksclickedcount]
            , [llp_reportingaccountid]
            , [llp_reportingaccountid_entitytype]
            , [llp_reportingaccountidname]
            , [llp_reportingaccountidyominame]
            , [messageid]
            , [messageiddupcheck]
            , [mimetype]
            , [modifiedby]
            , [modifiedby_entitytype]
            , [modifiedbyname]
            , [modifiedbyyominame]
            , [modifiedon]
            , [modifiedonbehalfby]
            , [modifiedonbehalfby_entitytype]
            , [modifiedonbehalfbyname]
            , [modifiedonbehalfbyyominame]
            , [notifications]
            , [onholdtime]
            , [opencount]
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
            , [parentactivityid]
            , [parentactivityid_entitytype]
            , [parentactivityidname]
            , [postponeemailprocessinguntil]
            , [prioritycode]
            , [processid]
            , [readreceiptrequested]
            , [regardingobjectid]
            , [regardingobjectid_entitytype]
            , [regardingobjectidname]
            , [regardingobjectidyominame]
            , [regardingobjecttypecode]
            , [reminderactioncardid]
            , [replycount]
            , [resco_contentstatus]
            , [resco_createdas]
            , [resco_createdfrom]
            , [resco_emailid]
            , [resco_eventid]
            , [resco_islocal]
            , [resco_snippet]
            , [resco_source]
            , [resco_statuscode]
            , [resco_threadid]
            , [safedescription]
            , [scheduleddurationminutes]
            , [scheduledend]
            , [scheduledstart]
            , [sender]
            , [sendermailboxid]
            , [sendermailboxid_entitytype]
            , [sendermailboxidname]
            , [sendersaccount]
            , [sendersaccount_entitytype]
            , [sendersaccountname]
            , [sendersaccountobjecttypecode]
            , [sendersaccountyominame]
            , [senton]
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
            , [submittedby]
            , [templateid]
            , [templateid_entitytype]
            , [templateidname]
            , [timezoneruleversionnumber]
            , [to]
            , [torecipients]
            , [trackingtoken]
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
            , s.[attachmentopencount]
            , s.[baseconversationindexhash]
            , s.[bcc]
            , s.[category]
            , s.[cc]
            , s.[compressed]
            , s.[conversationindex]
            , s.[conversationtrackingid]
            , s.[correlationmethod]
            , s.[createdby]
            , s.[createdby_entitytype]
            , s.[createdbyname]
            , s.[createdbyyominame]
            , s.[createdon]
            , s.[createdonbehalfby]
            , s.[createdonbehalfby_entitytype]
            , s.[createdonbehalfbyname]
            , s.[createdonbehalfbyyominame]
            , s.[delayedemailsendtime]
            , s.[deliveryattempts]
            , s.[deliveryprioritycode]
            , s.[deliveryreceiptrequested]
            , s.[description]
            , s.[directioncode]
            , s.[emailreminderexpirytime]
            , s.[emailreminderstatus]
            , s.[emailremindertext]
            , s.[emailremindertype]
            , s.[emailsender]
            , s.[emailsender_entitytype]
            , s.[emailsendername]
            , s.[emailsenderobjecttypecode]
            , s.[emailsenderyominame]
            , s.[emailtrackingid]
            , s.[exchangerate]
            , s.[followemailuserpreference]
            , s.[from]
            , s.[importsequencenumber]
            , s.[inreplyto]
            , s.[isbilled]
            , s.[isemailfollowed]
            , s.[isemailreminderset]
            , s.[isregularactivity]
            , s.[isunsafe]
            , s.[isworkflowcreated]
            , s.[lastonholdtime]
            , s.[lastopenedtime]
            , s.[linksclickedcount]
            , s.[llp_reportingaccountid]
            , s.[llp_reportingaccountid_entitytype]
            , s.[llp_reportingaccountidname]
            , s.[llp_reportingaccountidyominame]
            , s.[messageid]
            , s.[messageiddupcheck]
            , s.[mimetype]
            , s.[modifiedby]
            , s.[modifiedby_entitytype]
            , s.[modifiedbyname]
            , s.[modifiedbyyominame]
            , s.[modifiedon]
            , s.[modifiedonbehalfby]
            , s.[modifiedonbehalfby_entitytype]
            , s.[modifiedonbehalfbyname]
            , s.[modifiedonbehalfbyyominame]
            , s.[notifications]
            , s.[onholdtime]
            , s.[opencount]
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
            , s.[parentactivityid]
            , s.[parentactivityid_entitytype]
            , s.[parentactivityidname]
            , s.[postponeemailprocessinguntil]
            , s.[prioritycode]
            , s.[processid]
            , s.[readreceiptrequested]
            , s.[regardingobjectid]
            , s.[regardingobjectid_entitytype]
            , s.[regardingobjectidname]
            , s.[regardingobjectidyominame]
            , s.[regardingobjecttypecode]
            , s.[reminderactioncardid]
            , s.[replycount]
            , s.[resco_contentstatus]
            , s.[resco_createdas]
            , s.[resco_createdfrom]
            , s.[resco_emailid]
            , s.[resco_eventid]
            , s.[resco_islocal]
            , s.[resco_snippet]
            , s.[resco_source]
            , s.[resco_statuscode]
            , s.[resco_threadid]
            , s.[safedescription]
            , s.[scheduleddurationminutes]
            , s.[scheduledend]
            , s.[scheduledstart]
            , s.[sender]
            , s.[sendermailboxid]
            , s.[sendermailboxid_entitytype]
            , s.[sendermailboxidname]
            , s.[sendersaccount]
            , s.[sendersaccount_entitytype]
            , s.[sendersaccountname]
            , s.[sendersaccountobjecttypecode]
            , s.[sendersaccountyominame]
            , s.[senton]
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
            , s.[submittedby]
            , s.[templateid]
            , s.[templateid_entitytype]
            , s.[templateidname]
            , s.[timezoneruleversionnumber]
            , s.[to]
            , s.[torecipients]
            , s.[trackingtoken]
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
    
    INSERT INTO [Vault].[CRMdboEmail] (
            [Id]
            , [activityadditionalparams]
            , [activityid]
            , [activitytypecode]
            , [actualdurationminutes]
            , [actualend]
            , [actualstart]
            , [attachmentcount]
            , [attachmentopencount]
            , [baseconversationindexhash]
            , [bcc]
            , [category]
            , [cc]
            , [compressed]
            , [conversationindex]
            , [conversationtrackingid]
            , [correlationmethod]
            , [createdby]
            , [createdby_entitytype]
            , [createdbyname]
            , [createdbyyominame]
            , [createdon]
            , [createdonbehalfby]
            , [createdonbehalfby_entitytype]
            , [createdonbehalfbyname]
            , [createdonbehalfbyyominame]
            , [delayedemailsendtime]
            , [deliveryattempts]
            , [deliveryprioritycode]
            , [deliveryreceiptrequested]
            , [description]
            , [directioncode]
            , [emailreminderexpirytime]
            , [emailreminderstatus]
            , [emailremindertext]
            , [emailremindertype]
            , [emailsender]
            , [emailsender_entitytype]
            , [emailsendername]
            , [emailsenderobjecttypecode]
            , [emailsenderyominame]
            , [emailtrackingid]
            , [exchangerate]
            , [followemailuserpreference]
            , [from]
            , [importsequencenumber]
            , [inreplyto]
            , [isbilled]
            , [isemailfollowed]
            , [isemailreminderset]
            , [isregularactivity]
            , [isunsafe]
            , [isworkflowcreated]
            , [lastonholdtime]
            , [lastopenedtime]
            , [linksclickedcount]
            , [llp_reportingaccountid]
            , [llp_reportingaccountid_entitytype]
            , [llp_reportingaccountidname]
            , [llp_reportingaccountidyominame]
            , [messageid]
            , [messageiddupcheck]
            , [mimetype]
            , [modifiedby]
            , [modifiedby_entitytype]
            , [modifiedbyname]
            , [modifiedbyyominame]
            , [modifiedon]
            , [modifiedonbehalfby]
            , [modifiedonbehalfby_entitytype]
            , [modifiedonbehalfbyname]
            , [modifiedonbehalfbyyominame]
            , [notifications]
            , [onholdtime]
            , [opencount]
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
            , [parentactivityid]
            , [parentactivityid_entitytype]
            , [parentactivityidname]
            , [postponeemailprocessinguntil]
            , [prioritycode]
            , [processid]
            , [readreceiptrequested]
            , [regardingobjectid]
            , [regardingobjectid_entitytype]
            , [regardingobjectidname]
            , [regardingobjectidyominame]
            , [regardingobjecttypecode]
            , [reminderactioncardid]
            , [replycount]
            , [resco_contentstatus]
            , [resco_createdas]
            , [resco_createdfrom]
            , [resco_emailid]
            , [resco_eventid]
            , [resco_islocal]
            , [resco_snippet]
            , [resco_source]
            , [resco_statuscode]
            , [resco_threadid]
            , [safedescription]
            , [scheduleddurationminutes]
            , [scheduledend]
            , [scheduledstart]
            , [sender]
            , [sendermailboxid]
            , [sendermailboxid_entitytype]
            , [sendermailboxidname]
            , [sendersaccount]
            , [sendersaccount_entitytype]
            , [sendersaccountname]
            , [sendersaccountobjecttypecode]
            , [sendersaccountyominame]
            , [senton]
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
            , [submittedby]
            , [templateid]
            , [templateid_entitytype]
            , [templateidname]
            , [timezoneruleversionnumber]
            , [to]
            , [torecipients]
            , [trackingtoken]
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
            , s.[attachmentopencount]
            , s.[baseconversationindexhash]
            , s.[bcc]
            , s.[category]
            , s.[cc]
            , s.[compressed]
            , s.[conversationindex]
            , s.[conversationtrackingid]
            , s.[correlationmethod]
            , s.[createdby]
            , s.[createdby_entitytype]
            , s.[createdbyname]
            , s.[createdbyyominame]
            , s.[createdon]
            , s.[createdonbehalfby]
            , s.[createdonbehalfby_entitytype]
            , s.[createdonbehalfbyname]
            , s.[createdonbehalfbyyominame]
            , s.[delayedemailsendtime]
            , s.[deliveryattempts]
            , s.[deliveryprioritycode]
            , s.[deliveryreceiptrequested]
            , s.[description]
            , s.[directioncode]
            , s.[emailreminderexpirytime]
            , s.[emailreminderstatus]
            , s.[emailremindertext]
            , s.[emailremindertype]
            , s.[emailsender]
            , s.[emailsender_entitytype]
            , s.[emailsendername]
            , s.[emailsenderobjecttypecode]
            , s.[emailsenderyominame]
            , s.[emailtrackingid]
            , s.[exchangerate]
            , s.[followemailuserpreference]
            , s.[from]
            , s.[importsequencenumber]
            , s.[inreplyto]
            , s.[isbilled]
            , s.[isemailfollowed]
            , s.[isemailreminderset]
            , s.[isregularactivity]
            , s.[isunsafe]
            , s.[isworkflowcreated]
            , s.[lastonholdtime]
            , s.[lastopenedtime]
            , s.[linksclickedcount]
            , s.[llp_reportingaccountid]
            , s.[llp_reportingaccountid_entitytype]
            , s.[llp_reportingaccountidname]
            , s.[llp_reportingaccountidyominame]
            , s.[messageid]
            , s.[messageiddupcheck]
            , s.[mimetype]
            , s.[modifiedby]
            , s.[modifiedby_entitytype]
            , s.[modifiedbyname]
            , s.[modifiedbyyominame]
            , s.[modifiedon]
            , s.[modifiedonbehalfby]
            , s.[modifiedonbehalfby_entitytype]
            , s.[modifiedonbehalfbyname]
            , s.[modifiedonbehalfbyyominame]
            , s.[notifications]
            , s.[onholdtime]
            , s.[opencount]
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
            , s.[parentactivityid]
            , s.[parentactivityid_entitytype]
            , s.[parentactivityidname]
            , s.[postponeemailprocessinguntil]
            , s.[prioritycode]
            , s.[processid]
            , s.[readreceiptrequested]
            , s.[regardingobjectid]
            , s.[regardingobjectid_entitytype]
            , s.[regardingobjectidname]
            , s.[regardingobjectidyominame]
            , s.[regardingobjecttypecode]
            , s.[reminderactioncardid]
            , s.[replycount]
            , s.[resco_contentstatus]
            , s.[resco_createdas]
            , s.[resco_createdfrom]
            , s.[resco_emailid]
            , s.[resco_eventid]
            , s.[resco_islocal]
            , s.[resco_snippet]
            , s.[resco_source]
            , s.[resco_statuscode]
            , s.[resco_threadid]
            , s.[safedescription]
            , s.[scheduleddurationminutes]
            , s.[scheduledend]
            , s.[scheduledstart]
            , s.[sender]
            , s.[sendermailboxid]
            , s.[sendermailboxid_entitytype]
            , s.[sendermailboxidname]
            , s.[sendersaccount]
            , s.[sendersaccount_entitytype]
            , s.[sendersaccountname]
            , s.[sendersaccountobjecttypecode]
            , s.[sendersaccountyominame]
            , s.[senton]
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
            , s.[submittedby]
            , s.[templateid]
            , s.[templateid_entitytype]
            , s.[templateidname]
            , s.[timezoneruleversionnumber]
            , s.[to]
            , s.[torecipients]
            , s.[trackingtoken]
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
    FROM Stage.CRMdboEmail AS s
    INNER JOIN Vault.CRMdboEmail AS v
        ON  s.[Id] = v.[Id] AND v.ThreadLogUpdateId = @ThreadLogId
    
    INSERT INTO [Vault].[CRMdboEmail] (
            [Id]
            , [activityadditionalparams]
            , [activityid]
            , [activitytypecode]
            , [actualdurationminutes]
            , [actualend]
            , [actualstart]
            , [attachmentcount]
            , [attachmentopencount]
            , [baseconversationindexhash]
            , [bcc]
            , [category]
            , [cc]
            , [compressed]
            , [conversationindex]
            , [conversationtrackingid]
            , [correlationmethod]
            , [createdby]
            , [createdby_entitytype]
            , [createdbyname]
            , [createdbyyominame]
            , [createdon]
            , [createdonbehalfby]
            , [createdonbehalfby_entitytype]
            , [createdonbehalfbyname]
            , [createdonbehalfbyyominame]
            , [delayedemailsendtime]
            , [deliveryattempts]
            , [deliveryprioritycode]
            , [deliveryreceiptrequested]
            , [description]
            , [directioncode]
            , [emailreminderexpirytime]
            , [emailreminderstatus]
            , [emailremindertext]
            , [emailremindertype]
            , [emailsender]
            , [emailsender_entitytype]
            , [emailsendername]
            , [emailsenderobjecttypecode]
            , [emailsenderyominame]
            , [emailtrackingid]
            , [exchangerate]
            , [followemailuserpreference]
            , [from]
            , [importsequencenumber]
            , [inreplyto]
            , [isbilled]
            , [isemailfollowed]
            , [isemailreminderset]
            , [isregularactivity]
            , [isunsafe]
            , [isworkflowcreated]
            , [lastonholdtime]
            , [lastopenedtime]
            , [linksclickedcount]
            , [llp_reportingaccountid]
            , [llp_reportingaccountid_entitytype]
            , [llp_reportingaccountidname]
            , [llp_reportingaccountidyominame]
            , [messageid]
            , [messageiddupcheck]
            , [mimetype]
            , [modifiedby]
            , [modifiedby_entitytype]
            , [modifiedbyname]
            , [modifiedbyyominame]
            , [modifiedon]
            , [modifiedonbehalfby]
            , [modifiedonbehalfby_entitytype]
            , [modifiedonbehalfbyname]
            , [modifiedonbehalfbyyominame]
            , [notifications]
            , [onholdtime]
            , [opencount]
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
            , [parentactivityid]
            , [parentactivityid_entitytype]
            , [parentactivityidname]
            , [postponeemailprocessinguntil]
            , [prioritycode]
            , [processid]
            , [readreceiptrequested]
            , [regardingobjectid]
            , [regardingobjectid_entitytype]
            , [regardingobjectidname]
            , [regardingobjectidyominame]
            , [regardingobjecttypecode]
            , [reminderactioncardid]
            , [replycount]
            , [resco_contentstatus]
            , [resco_createdas]
            , [resco_createdfrom]
            , [resco_emailid]
            , [resco_eventid]
            , [resco_islocal]
            , [resco_snippet]
            , [resco_source]
            , [resco_statuscode]
            , [resco_threadid]
            , [safedescription]
            , [scheduleddurationminutes]
            , [scheduledend]
            , [scheduledstart]
            , [sender]
            , [sendermailboxid]
            , [sendermailboxid_entitytype]
            , [sendermailboxidname]
            , [sendersaccount]
            , [sendersaccount_entitytype]
            , [sendersaccountname]
            , [sendersaccountobjecttypecode]
            , [sendersaccountyominame]
            , [senton]
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
            , [submittedby]
            , [templateid]
            , [templateid_entitytype]
            , [templateidname]
            , [timezoneruleversionnumber]
            , [to]
            , [torecipients]
            , [trackingtoken]
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
            , v.[attachmentopencount]
            , v.[baseconversationindexhash]
            , v.[bcc]
            , v.[category]
            , v.[cc]
            , v.[compressed]
            , v.[conversationindex]
            , v.[conversationtrackingid]
            , v.[correlationmethod]
            , v.[createdby]
            , v.[createdby_entitytype]
            , v.[createdbyname]
            , v.[createdbyyominame]
            , v.[createdon]
            , v.[createdonbehalfby]
            , v.[createdonbehalfby_entitytype]
            , v.[createdonbehalfbyname]
            , v.[createdonbehalfbyyominame]
            , v.[delayedemailsendtime]
            , v.[deliveryattempts]
            , v.[deliveryprioritycode]
            , v.[deliveryreceiptrequested]
            , v.[description]
            , v.[directioncode]
            , v.[emailreminderexpirytime]
            , v.[emailreminderstatus]
            , v.[emailremindertext]
            , v.[emailremindertype]
            , v.[emailsender]
            , v.[emailsender_entitytype]
            , v.[emailsendername]
            , v.[emailsenderobjecttypecode]
            , v.[emailsenderyominame]
            , v.[emailtrackingid]
            , v.[exchangerate]
            , v.[followemailuserpreference]
            , v.[from]
            , v.[importsequencenumber]
            , v.[inreplyto]
            , v.[isbilled]
            , v.[isemailfollowed]
            , v.[isemailreminderset]
            , v.[isregularactivity]
            , v.[isunsafe]
            , v.[isworkflowcreated]
            , v.[lastonholdtime]
            , v.[lastopenedtime]
            , v.[linksclickedcount]
            , v.[llp_reportingaccountid]
            , v.[llp_reportingaccountid_entitytype]
            , v.[llp_reportingaccountidname]
            , v.[llp_reportingaccountidyominame]
            , v.[messageid]
            , v.[messageiddupcheck]
            , v.[mimetype]
            , v.[modifiedby]
            , v.[modifiedby_entitytype]
            , v.[modifiedbyname]
            , v.[modifiedbyyominame]
            , v.[modifiedon]
            , v.[modifiedonbehalfby]
            , v.[modifiedonbehalfby_entitytype]
            , v.[modifiedonbehalfbyname]
            , v.[modifiedonbehalfbyyominame]
            , v.[notifications]
            , v.[onholdtime]
            , v.[opencount]
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
            , v.[parentactivityid]
            , v.[parentactivityid_entitytype]
            , v.[parentactivityidname]
            , v.[postponeemailprocessinguntil]
            , v.[prioritycode]
            , v.[processid]
            , v.[readreceiptrequested]
            , v.[regardingobjectid]
            , v.[regardingobjectid_entitytype]
            , v.[regardingobjectidname]
            , v.[regardingobjectidyominame]
            , v.[regardingobjecttypecode]
            , v.[reminderactioncardid]
            , v.[replycount]
            , v.[resco_contentstatus]
            , v.[resco_createdas]
            , v.[resco_createdfrom]
            , v.[resco_emailid]
            , v.[resco_eventid]
            , v.[resco_islocal]
            , v.[resco_snippet]
            , v.[resco_source]
            , v.[resco_statuscode]
            , v.[resco_threadid]
            , v.[safedescription]
            , v.[scheduleddurationminutes]
            , v.[scheduledend]
            , v.[scheduledstart]
            , v.[sender]
            , v.[sendermailboxid]
            , v.[sendermailboxid_entitytype]
            , v.[sendermailboxidname]
            , v.[sendersaccount]
            , v.[sendersaccount_entitytype]
            , v.[sendersaccountname]
            , v.[sendersaccountobjecttypecode]
            , v.[sendersaccountyominame]
            , v.[senton]
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
            , v.[submittedby]
            , v.[templateid]
            , v.[templateid_entitytype]
            , v.[templateidname]
            , v.[timezoneruleversionnumber]
            , v.[to]
            , v.[torecipients]
            , v.[trackingtoken]
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
    FROM Vault.CRMdboEmail AS v
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
                , TableFinalRowCount = (SELECT COUNT(*) FROM [Vault].[CRMdboEmail] WITH (NOLOCK))
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
