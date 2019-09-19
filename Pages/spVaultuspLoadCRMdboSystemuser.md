Stored Procedure Vault.uspLoadCRMdboSystemuser {#spVaultuspLoadCRMdboSystemuser}
----------------------------------------------

Definition of Stored procedure:

``` {.sql}
CREATE PROCEDURE [Vault].[uspLoadCRMdboSystemuser] 
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
            SET TableInitialRowCount = (SELECT COUNT(*) FROM [Vault].[CRMdboSystemuser] WITH (NOLOCK))
        WHERE ThreadLogId = @ThreadLogId;

            BEGIN TRANSACTION;

    
        MERGE INTO [Vault].[CRMdboSystemuser] AS v
        USING [Stage].[CRMdboSystemuser] AS s
            ON ( s.[Id] = v.[Id]AND s.[DataSourceId] = v.[DataSourceId]
     AND v.[ThreadLogDeleteId] = -1 AND v.[ThreadLogUpdateId] = -1 AND v.[ChangeOperation] <> N'D'
    )

        WHEN MATCHED AND
            (
            v.[accessmode] <> s.[accessmode]
            OR (v.[accessmode] IS NULL AND s.[accessmode] IS NOT NULL)
        OR (v.[accessmode] IS NOT NULL AND s.[accessmode] IS NULL)
        OR v.[activedirectoryguid] <> s.[activedirectoryguid]
            OR (v.[activedirectoryguid] IS NULL AND s.[activedirectoryguid] IS NOT NULL)
        OR (v.[activedirectoryguid] IS NOT NULL AND s.[activedirectoryguid] IS NULL)
        OR v.[address1_addressid] <> s.[address1_addressid]
            OR (v.[address1_addressid] IS NULL AND s.[address1_addressid] IS NOT NULL)
        OR (v.[address1_addressid] IS NOT NULL AND s.[address1_addressid] IS NULL)
        OR v.[address1_addresstypecode] <> s.[address1_addresstypecode]
            OR (v.[address1_addresstypecode] IS NULL AND s.[address1_addresstypecode] IS NOT NULL)
        OR (v.[address1_addresstypecode] IS NOT NULL AND s.[address1_addresstypecode] IS NULL)
        OR v.[address1_city] <> s.[address1_city]
            OR (v.[address1_city] IS NULL AND s.[address1_city] IS NOT NULL)
        OR (v.[address1_city] IS NOT NULL AND s.[address1_city] IS NULL)
        OR v.[address1_composite] <> s.[address1_composite]
            OR (v.[address1_composite] IS NULL AND s.[address1_composite] IS NOT NULL)
        OR (v.[address1_composite] IS NOT NULL AND s.[address1_composite] IS NULL)
        OR v.[address1_country] <> s.[address1_country]
            OR (v.[address1_country] IS NULL AND s.[address1_country] IS NOT NULL)
        OR (v.[address1_country] IS NOT NULL AND s.[address1_country] IS NULL)
        OR v.[address1_county] <> s.[address1_county]
            OR (v.[address1_county] IS NULL AND s.[address1_county] IS NOT NULL)
        OR (v.[address1_county] IS NOT NULL AND s.[address1_county] IS NULL)
        OR v.[address1_fax] <> s.[address1_fax]
            OR (v.[address1_fax] IS NULL AND s.[address1_fax] IS NOT NULL)
        OR (v.[address1_fax] IS NOT NULL AND s.[address1_fax] IS NULL)
        OR v.[address1_latitude] <> s.[address1_latitude]
            OR (v.[address1_latitude] IS NULL AND s.[address1_latitude] IS NOT NULL)
        OR (v.[address1_latitude] IS NOT NULL AND s.[address1_latitude] IS NULL)
        OR v.[address1_line1] <> s.[address1_line1]
            OR (v.[address1_line1] IS NULL AND s.[address1_line1] IS NOT NULL)
        OR (v.[address1_line1] IS NOT NULL AND s.[address1_line1] IS NULL)
        OR v.[address1_line2] <> s.[address1_line2]
            OR (v.[address1_line2] IS NULL AND s.[address1_line2] IS NOT NULL)
        OR (v.[address1_line2] IS NOT NULL AND s.[address1_line2] IS NULL)
        OR v.[address1_line3] <> s.[address1_line3]
            OR (v.[address1_line3] IS NULL AND s.[address1_line3] IS NOT NULL)
        OR (v.[address1_line3] IS NOT NULL AND s.[address1_line3] IS NULL)
        OR v.[address1_longitude] <> s.[address1_longitude]
            OR (v.[address1_longitude] IS NULL AND s.[address1_longitude] IS NOT NULL)
        OR (v.[address1_longitude] IS NOT NULL AND s.[address1_longitude] IS NULL)
        OR v.[address1_name] <> s.[address1_name]
            OR (v.[address1_name] IS NULL AND s.[address1_name] IS NOT NULL)
        OR (v.[address1_name] IS NOT NULL AND s.[address1_name] IS NULL)
        OR v.[address1_postalcode] <> s.[address1_postalcode]
            OR (v.[address1_postalcode] IS NULL AND s.[address1_postalcode] IS NOT NULL)
        OR (v.[address1_postalcode] IS NOT NULL AND s.[address1_postalcode] IS NULL)
        OR v.[address1_postofficebox] <> s.[address1_postofficebox]
            OR (v.[address1_postofficebox] IS NULL AND s.[address1_postofficebox] IS NOT NULL)
        OR (v.[address1_postofficebox] IS NOT NULL AND s.[address1_postofficebox] IS NULL)
        OR v.[address1_shippingmethodcode] <> s.[address1_shippingmethodcode]
            OR (v.[address1_shippingmethodcode] IS NULL AND s.[address1_shippingmethodcode] IS NOT NULL)
        OR (v.[address1_shippingmethodcode] IS NOT NULL AND s.[address1_shippingmethodcode] IS NULL)
        OR v.[address1_stateorprovince] <> s.[address1_stateorprovince]
            OR (v.[address1_stateorprovince] IS NULL AND s.[address1_stateorprovince] IS NOT NULL)
        OR (v.[address1_stateorprovince] IS NOT NULL AND s.[address1_stateorprovince] IS NULL)
        OR v.[address1_telephone1] <> s.[address1_telephone1]
            OR (v.[address1_telephone1] IS NULL AND s.[address1_telephone1] IS NOT NULL)
        OR (v.[address1_telephone1] IS NOT NULL AND s.[address1_telephone1] IS NULL)
        OR v.[address1_telephone2] <> s.[address1_telephone2]
            OR (v.[address1_telephone2] IS NULL AND s.[address1_telephone2] IS NOT NULL)
        OR (v.[address1_telephone2] IS NOT NULL AND s.[address1_telephone2] IS NULL)
        OR v.[address1_telephone3] <> s.[address1_telephone3]
            OR (v.[address1_telephone3] IS NULL AND s.[address1_telephone3] IS NOT NULL)
        OR (v.[address1_telephone3] IS NOT NULL AND s.[address1_telephone3] IS NULL)
        OR v.[address1_upszone] <> s.[address1_upszone]
            OR (v.[address1_upszone] IS NULL AND s.[address1_upszone] IS NOT NULL)
        OR (v.[address1_upszone] IS NOT NULL AND s.[address1_upszone] IS NULL)
        OR v.[address1_utcoffset] <> s.[address1_utcoffset]
            OR (v.[address1_utcoffset] IS NULL AND s.[address1_utcoffset] IS NOT NULL)
        OR (v.[address1_utcoffset] IS NOT NULL AND s.[address1_utcoffset] IS NULL)
        OR v.[address2_addressid] <> s.[address2_addressid]
            OR (v.[address2_addressid] IS NULL AND s.[address2_addressid] IS NOT NULL)
        OR (v.[address2_addressid] IS NOT NULL AND s.[address2_addressid] IS NULL)
        OR v.[address2_addresstypecode] <> s.[address2_addresstypecode]
            OR (v.[address2_addresstypecode] IS NULL AND s.[address2_addresstypecode] IS NOT NULL)
        OR (v.[address2_addresstypecode] IS NOT NULL AND s.[address2_addresstypecode] IS NULL)
        OR v.[address2_city] <> s.[address2_city]
            OR (v.[address2_city] IS NULL AND s.[address2_city] IS NOT NULL)
        OR (v.[address2_city] IS NOT NULL AND s.[address2_city] IS NULL)
        OR v.[address2_composite] <> s.[address2_composite]
            OR (v.[address2_composite] IS NULL AND s.[address2_composite] IS NOT NULL)
        OR (v.[address2_composite] IS NOT NULL AND s.[address2_composite] IS NULL)
        OR v.[address2_country] <> s.[address2_country]
            OR (v.[address2_country] IS NULL AND s.[address2_country] IS NOT NULL)
        OR (v.[address2_country] IS NOT NULL AND s.[address2_country] IS NULL)
        OR v.[address2_county] <> s.[address2_county]
            OR (v.[address2_county] IS NULL AND s.[address2_county] IS NOT NULL)
        OR (v.[address2_county] IS NOT NULL AND s.[address2_county] IS NULL)
        OR v.[address2_fax] <> s.[address2_fax]
            OR (v.[address2_fax] IS NULL AND s.[address2_fax] IS NOT NULL)
        OR (v.[address2_fax] IS NOT NULL AND s.[address2_fax] IS NULL)
        OR v.[address2_latitude] <> s.[address2_latitude]
            OR (v.[address2_latitude] IS NULL AND s.[address2_latitude] IS NOT NULL)
        OR (v.[address2_latitude] IS NOT NULL AND s.[address2_latitude] IS NULL)
        OR v.[address2_line1] <> s.[address2_line1]
            OR (v.[address2_line1] IS NULL AND s.[address2_line1] IS NOT NULL)
        OR (v.[address2_line1] IS NOT NULL AND s.[address2_line1] IS NULL)
        OR v.[address2_line2] <> s.[address2_line2]
            OR (v.[address2_line2] IS NULL AND s.[address2_line2] IS NOT NULL)
        OR (v.[address2_line2] IS NOT NULL AND s.[address2_line2] IS NULL)
        OR v.[address2_line3] <> s.[address2_line3]
            OR (v.[address2_line3] IS NULL AND s.[address2_line3] IS NOT NULL)
        OR (v.[address2_line3] IS NOT NULL AND s.[address2_line3] IS NULL)
        OR v.[address2_longitude] <> s.[address2_longitude]
            OR (v.[address2_longitude] IS NULL AND s.[address2_longitude] IS NOT NULL)
        OR (v.[address2_longitude] IS NOT NULL AND s.[address2_longitude] IS NULL)
        OR v.[address2_name] <> s.[address2_name]
            OR (v.[address2_name] IS NULL AND s.[address2_name] IS NOT NULL)
        OR (v.[address2_name] IS NOT NULL AND s.[address2_name] IS NULL)
        OR v.[address2_postalcode] <> s.[address2_postalcode]
            OR (v.[address2_postalcode] IS NULL AND s.[address2_postalcode] IS NOT NULL)
        OR (v.[address2_postalcode] IS NOT NULL AND s.[address2_postalcode] IS NULL)
        OR v.[address2_postofficebox] <> s.[address2_postofficebox]
            OR (v.[address2_postofficebox] IS NULL AND s.[address2_postofficebox] IS NOT NULL)
        OR (v.[address2_postofficebox] IS NOT NULL AND s.[address2_postofficebox] IS NULL)
        OR v.[address2_shippingmethodcode] <> s.[address2_shippingmethodcode]
            OR (v.[address2_shippingmethodcode] IS NULL AND s.[address2_shippingmethodcode] IS NOT NULL)
        OR (v.[address2_shippingmethodcode] IS NOT NULL AND s.[address2_shippingmethodcode] IS NULL)
        OR v.[address2_stateorprovince] <> s.[address2_stateorprovince]
            OR (v.[address2_stateorprovince] IS NULL AND s.[address2_stateorprovince] IS NOT NULL)
        OR (v.[address2_stateorprovince] IS NOT NULL AND s.[address2_stateorprovince] IS NULL)
        OR v.[address2_telephone1] <> s.[address2_telephone1]
            OR (v.[address2_telephone1] IS NULL AND s.[address2_telephone1] IS NOT NULL)
        OR (v.[address2_telephone1] IS NOT NULL AND s.[address2_telephone1] IS NULL)
        OR v.[address2_telephone2] <> s.[address2_telephone2]
            OR (v.[address2_telephone2] IS NULL AND s.[address2_telephone2] IS NOT NULL)
        OR (v.[address2_telephone2] IS NOT NULL AND s.[address2_telephone2] IS NULL)
        OR v.[address2_telephone3] <> s.[address2_telephone3]
            OR (v.[address2_telephone3] IS NULL AND s.[address2_telephone3] IS NOT NULL)
        OR (v.[address2_telephone3] IS NOT NULL AND s.[address2_telephone3] IS NULL)
        OR v.[address2_upszone] <> s.[address2_upszone]
            OR (v.[address2_upszone] IS NULL AND s.[address2_upszone] IS NOT NULL)
        OR (v.[address2_upszone] IS NOT NULL AND s.[address2_upszone] IS NULL)
        OR v.[address2_utcoffset] <> s.[address2_utcoffset]
            OR (v.[address2_utcoffset] IS NULL AND s.[address2_utcoffset] IS NOT NULL)
        OR (v.[address2_utcoffset] IS NOT NULL AND s.[address2_utcoffset] IS NULL)
        OR v.[applicationid] <> s.[applicationid]
            OR (v.[applicationid] IS NULL AND s.[applicationid] IS NOT NULL)
        OR (v.[applicationid] IS NOT NULL AND s.[applicationid] IS NULL)
        OR v.[applicationiduri] <> s.[applicationiduri]
            OR (v.[applicationiduri] IS NULL AND s.[applicationiduri] IS NOT NULL)
        OR (v.[applicationiduri] IS NOT NULL AND s.[applicationiduri] IS NULL)
        OR v.[azureactivedirectoryobjectid] <> s.[azureactivedirectoryobjectid]
            OR (v.[azureactivedirectoryobjectid] IS NULL AND s.[azureactivedirectoryobjectid] IS NOT NULL)
        OR (v.[azureactivedirectoryobjectid] IS NOT NULL AND s.[azureactivedirectoryobjectid] IS NULL)
        OR v.[businessunitid] <> s.[businessunitid]
            OR (v.[businessunitid] IS NULL AND s.[businessunitid] IS NOT NULL)
        OR (v.[businessunitid] IS NOT NULL AND s.[businessunitid] IS NULL)
        OR v.[businessunitid_entitytype] <> s.[businessunitid_entitytype]
            OR (v.[businessunitid_entitytype] IS NULL AND s.[businessunitid_entitytype] IS NOT NULL)
        OR (v.[businessunitid_entitytype] IS NOT NULL AND s.[businessunitid_entitytype] IS NULL)
        OR v.[businessunitidname] <> s.[businessunitidname]
            OR (v.[businessunitidname] IS NULL AND s.[businessunitidname] IS NOT NULL)
        OR (v.[businessunitidname] IS NOT NULL AND s.[businessunitidname] IS NULL)
        OR v.[calendarid] <> s.[calendarid]
            OR (v.[calendarid] IS NULL AND s.[calendarid] IS NOT NULL)
        OR (v.[calendarid] IS NOT NULL AND s.[calendarid] IS NULL)
        OR v.[calendarid_entitytype] <> s.[calendarid_entitytype]
            OR (v.[calendarid_entitytype] IS NULL AND s.[calendarid_entitytype] IS NOT NULL)
        OR (v.[calendarid_entitytype] IS NOT NULL AND s.[calendarid_entitytype] IS NULL)
        OR v.[caltype] <> s.[caltype]
            OR (v.[caltype] IS NULL AND s.[caltype] IS NOT NULL)
        OR (v.[caltype] IS NOT NULL AND s.[caltype] IS NULL)
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
        OR v.[defaultfilterspopulated] <> s.[defaultfilterspopulated]
            OR (v.[defaultfilterspopulated] IS NULL AND s.[defaultfilterspopulated] IS NOT NULL)
        OR (v.[defaultfilterspopulated] IS NOT NULL AND s.[defaultfilterspopulated] IS NULL)
        OR v.[defaultmailbox] <> s.[defaultmailbox]
            OR (v.[defaultmailbox] IS NULL AND s.[defaultmailbox] IS NOT NULL)
        OR (v.[defaultmailbox] IS NOT NULL AND s.[defaultmailbox] IS NULL)
        OR v.[defaultmailbox_entitytype] <> s.[defaultmailbox_entitytype]
            OR (v.[defaultmailbox_entitytype] IS NULL AND s.[defaultmailbox_entitytype] IS NOT NULL)
        OR (v.[defaultmailbox_entitytype] IS NOT NULL AND s.[defaultmailbox_entitytype] IS NULL)
        OR v.[defaultmailboxname] <> s.[defaultmailboxname]
            OR (v.[defaultmailboxname] IS NULL AND s.[defaultmailboxname] IS NOT NULL)
        OR (v.[defaultmailboxname] IS NOT NULL AND s.[defaultmailboxname] IS NULL)
        OR v.[defaultodbfoldername] <> s.[defaultodbfoldername]
            OR (v.[defaultodbfoldername] IS NULL AND s.[defaultodbfoldername] IS NOT NULL)
        OR (v.[defaultodbfoldername] IS NOT NULL AND s.[defaultodbfoldername] IS NULL)
        OR v.[disabledreason] <> s.[disabledreason]
            OR (v.[disabledreason] IS NULL AND s.[disabledreason] IS NOT NULL)
        OR (v.[disabledreason] IS NOT NULL AND s.[disabledreason] IS NULL)
        OR v.[displayinserviceviews] <> s.[displayinserviceviews]
            OR (v.[displayinserviceviews] IS NULL AND s.[displayinserviceviews] IS NOT NULL)
        OR (v.[displayinserviceviews] IS NOT NULL AND s.[displayinserviceviews] IS NULL)
        OR v.[domainname] <> s.[domainname]
            OR (v.[domainname] IS NULL AND s.[domainname] IS NOT NULL)
        OR (v.[domainname] IS NOT NULL AND s.[domainname] IS NULL)
        OR v.[emailrouteraccessapproval] <> s.[emailrouteraccessapproval]
            OR (v.[emailrouteraccessapproval] IS NULL AND s.[emailrouteraccessapproval] IS NOT NULL)
        OR (v.[emailrouteraccessapproval] IS NOT NULL AND s.[emailrouteraccessapproval] IS NULL)
        OR v.[employeeid] <> s.[employeeid]
            OR (v.[employeeid] IS NULL AND s.[employeeid] IS NOT NULL)
        OR (v.[employeeid] IS NOT NULL AND s.[employeeid] IS NULL)
        OR v.[entityimage_timestamp] <> s.[entityimage_timestamp]
            OR (v.[entityimage_timestamp] IS NULL AND s.[entityimage_timestamp] IS NOT NULL)
        OR (v.[entityimage_timestamp] IS NOT NULL AND s.[entityimage_timestamp] IS NULL)
        OR v.[entityimage_url] <> s.[entityimage_url]
            OR (v.[entityimage_url] IS NULL AND s.[entityimage_url] IS NOT NULL)
        OR (v.[entityimage_url] IS NOT NULL AND s.[entityimage_url] IS NULL)
        OR v.[entityimageid] <> s.[entityimageid]
            OR (v.[entityimageid] IS NULL AND s.[entityimageid] IS NOT NULL)
        OR (v.[entityimageid] IS NOT NULL AND s.[entityimageid] IS NULL)
        OR v.[exchangerate] <> s.[exchangerate]
            OR (v.[exchangerate] IS NULL AND s.[exchangerate] IS NOT NULL)
        OR (v.[exchangerate] IS NOT NULL AND s.[exchangerate] IS NULL)
        OR v.[firstname] <> s.[firstname]
            OR (v.[firstname] IS NULL AND s.[firstname] IS NOT NULL)
        OR (v.[firstname] IS NOT NULL AND s.[firstname] IS NULL)
        OR v.[fullname] <> s.[fullname]
            OR (v.[fullname] IS NULL AND s.[fullname] IS NOT NULL)
        OR (v.[fullname] IS NOT NULL AND s.[fullname] IS NULL)
        OR v.[governmentid] <> s.[governmentid]
            OR (v.[governmentid] IS NULL AND s.[governmentid] IS NOT NULL)
        OR (v.[governmentid] IS NOT NULL AND s.[governmentid] IS NULL)
        OR v.[homephone] <> s.[homephone]
            OR (v.[homephone] IS NULL AND s.[homephone] IS NOT NULL)
        OR (v.[homephone] IS NOT NULL AND s.[homephone] IS NULL)
        OR v.[identityid] <> s.[identityid]
            OR (v.[identityid] IS NULL AND s.[identityid] IS NOT NULL)
        OR (v.[identityid] IS NOT NULL AND s.[identityid] IS NULL)
        OR v.[importsequencenumber] <> s.[importsequencenumber]
            OR (v.[importsequencenumber] IS NULL AND s.[importsequencenumber] IS NOT NULL)
        OR (v.[importsequencenumber] IS NOT NULL AND s.[importsequencenumber] IS NULL)
        OR v.[incomingemaildeliverymethod] <> s.[incomingemaildeliverymethod]
            OR (v.[incomingemaildeliverymethod] IS NULL AND s.[incomingemaildeliverymethod] IS NOT NULL)
        OR (v.[incomingemaildeliverymethod] IS NOT NULL AND s.[incomingemaildeliverymethod] IS NULL)
        OR v.[internalemailaddress] <> s.[internalemailaddress]
            OR (v.[internalemailaddress] IS NULL AND s.[internalemailaddress] IS NOT NULL)
        OR (v.[internalemailaddress] IS NOT NULL AND s.[internalemailaddress] IS NULL)
        OR v.[invitestatuscode] <> s.[invitestatuscode]
            OR (v.[invitestatuscode] IS NULL AND s.[invitestatuscode] IS NOT NULL)
        OR (v.[invitestatuscode] IS NOT NULL AND s.[invitestatuscode] IS NULL)
        OR v.[isactivedirectoryuser] <> s.[isactivedirectoryuser]
            OR (v.[isactivedirectoryuser] IS NULL AND s.[isactivedirectoryuser] IS NOT NULL)
        OR (v.[isactivedirectoryuser] IS NOT NULL AND s.[isactivedirectoryuser] IS NULL)
        OR v.[isdisabled] <> s.[isdisabled]
            OR (v.[isdisabled] IS NULL AND s.[isdisabled] IS NOT NULL)
        OR (v.[isdisabled] IS NOT NULL AND s.[isdisabled] IS NULL)
        OR v.[isemailaddressapprovedbyo365admin] <> s.[isemailaddressapprovedbyo365admin]
            OR (v.[isemailaddressapprovedbyo365admin] IS NULL AND s.[isemailaddressapprovedbyo365admin] IS NOT NULL)
        OR (v.[isemailaddressapprovedbyo365admin] IS NOT NULL AND s.[isemailaddressapprovedbyo365admin] IS NULL)
        OR v.[isintegrationuser] <> s.[isintegrationuser]
            OR (v.[isintegrationuser] IS NULL AND s.[isintegrationuser] IS NOT NULL)
        OR (v.[isintegrationuser] IS NOT NULL AND s.[isintegrationuser] IS NULL)
        OR v.[islicensed] <> s.[islicensed]
            OR (v.[islicensed] IS NULL AND s.[islicensed] IS NOT NULL)
        OR (v.[islicensed] IS NOT NULL AND s.[islicensed] IS NULL)
        OR v.[issyncwithdirectory] <> s.[issyncwithdirectory]
            OR (v.[issyncwithdirectory] IS NULL AND s.[issyncwithdirectory] IS NOT NULL)
        OR (v.[issyncwithdirectory] IS NOT NULL AND s.[issyncwithdirectory] IS NULL)
        OR v.[jobtitle] <> s.[jobtitle]
            OR (v.[jobtitle] IS NULL AND s.[jobtitle] IS NOT NULL)
        OR (v.[jobtitle] IS NOT NULL AND s.[jobtitle] IS NULL)
        OR v.[lastname] <> s.[lastname]
            OR (v.[lastname] IS NULL AND s.[lastname] IS NOT NULL)
        OR (v.[lastname] IS NOT NULL AND s.[lastname] IS NULL)
        OR v.[latestupdatetime] <> s.[latestupdatetime]
            OR (v.[latestupdatetime] IS NULL AND s.[latestupdatetime] IS NOT NULL)
        OR (v.[latestupdatetime] IS NOT NULL AND s.[latestupdatetime] IS NULL)
        OR v.[llp_arbesdbname] <> s.[llp_arbesdbname]
            OR (v.[llp_arbesdbname] IS NULL AND s.[llp_arbesdbname] IS NOT NULL)
        OR (v.[llp_arbesdbname] IS NOT NULL AND s.[llp_arbesdbname] IS NULL)
        OR v.[llp_arbessyncallowed] <> s.[llp_arbessyncallowed]
            OR (v.[llp_arbessyncallowed] IS NULL AND s.[llp_arbessyncallowed] IS NOT NULL)
        OR (v.[llp_arbessyncallowed] IS NOT NULL AND s.[llp_arbessyncallowed] IS NULL)
        OR v.[llp_automastersyncallowed] <> s.[llp_automastersyncallowed]
            OR (v.[llp_automastersyncallowed] IS NULL AND s.[llp_automastersyncallowed] IS NOT NULL)
        OR (v.[llp_automastersyncallowed] IS NOT NULL AND s.[llp_automastersyncallowed] IS NULL)
        OR v.[llp_automastersyncdbname] <> s.[llp_automastersyncdbname]
            OR (v.[llp_automastersyncdbname] IS NULL AND s.[llp_automastersyncdbname] IS NOT NULL)
        OR (v.[llp_automastersyncdbname] IS NOT NULL AND s.[llp_automastersyncdbname] IS NULL)
        OR v.[llp_automaticallysendtoautomaster] <> s.[llp_automaticallysendtoautomaster]
            OR (v.[llp_automaticallysendtoautomaster] IS NULL AND s.[llp_automaticallysendtoautomaster] IS NOT NULL)
        OR (v.[llp_automaticallysendtoautomaster] IS NOT NULL AND s.[llp_automaticallysendtoautomaster] IS NULL)
        OR v.[llp_certsyncallowed] <> s.[llp_certsyncallowed]
            OR (v.[llp_certsyncallowed] IS NULL AND s.[llp_certsyncallowed] IS NOT NULL)
        OR (v.[llp_certsyncallowed] IS NOT NULL AND s.[llp_certsyncallowed] IS NULL)
        OR v.[llp_certsyncdbname] <> s.[llp_certsyncdbname]
            OR (v.[llp_certsyncdbname] IS NULL AND s.[llp_certsyncdbname] IS NOT NULL)
        OR (v.[llp_certsyncdbname] IS NOT NULL AND s.[llp_certsyncdbname] IS NULL)
        OR v.[llp_defaultopportunitytype] <> s.[llp_defaultopportunitytype]
            OR (v.[llp_defaultopportunitytype] IS NULL AND s.[llp_defaultopportunitytype] IS NOT NULL)
        OR (v.[llp_defaultopportunitytype] IS NOT NULL AND s.[llp_defaultopportunitytype] IS NULL)
        OR v.[llp_idnetsuite] <> s.[llp_idnetsuite]
            OR (v.[llp_idnetsuite] IS NULL AND s.[llp_idnetsuite] IS NOT NULL)
        OR (v.[llp_idnetsuite] IS NOT NULL AND s.[llp_idnetsuite] IS NULL)
        OR v.[llp_sfinsuranceid] <> s.[llp_sfinsuranceid]
            OR (v.[llp_sfinsuranceid] IS NULL AND s.[llp_sfinsuranceid] IS NOT NULL)
        OR (v.[llp_sfinsuranceid] IS NOT NULL AND s.[llp_sfinsuranceid] IS NULL)
        OR v.[llp_sfinsuranceid_entitytype] <> s.[llp_sfinsuranceid_entitytype]
            OR (v.[llp_sfinsuranceid_entitytype] IS NULL AND s.[llp_sfinsuranceid_entitytype] IS NOT NULL)
        OR (v.[llp_sfinsuranceid_entitytype] IS NOT NULL AND s.[llp_sfinsuranceid_entitytype] IS NULL)
        OR v.[llp_sfinsuranceidname] <> s.[llp_sfinsuranceidname]
            OR (v.[llp_sfinsuranceidname] IS NULL AND s.[llp_sfinsuranceidname] IS NOT NULL)
        OR (v.[llp_sfinsuranceidname] IS NOT NULL AND s.[llp_sfinsuranceidname] IS NULL)
        OR v.[llp_sfinsuranceidyominame] <> s.[llp_sfinsuranceidyominame]
            OR (v.[llp_sfinsuranceidyominame] IS NULL AND s.[llp_sfinsuranceidyominame] IS NOT NULL)
        OR (v.[llp_sfinsuranceidyominame] IS NOT NULL AND s.[llp_sfinsuranceidyominame] IS NULL)
        OR v.[llp_sfsalespersonid] <> s.[llp_sfsalespersonid]
            OR (v.[llp_sfsalespersonid] IS NULL AND s.[llp_sfsalespersonid] IS NOT NULL)
        OR (v.[llp_sfsalespersonid] IS NOT NULL AND s.[llp_sfsalespersonid] IS NULL)
        OR v.[llp_sfsalespersonid_entitytype] <> s.[llp_sfsalespersonid_entitytype]
            OR (v.[llp_sfsalespersonid_entitytype] IS NULL AND s.[llp_sfsalespersonid_entitytype] IS NOT NULL)
        OR (v.[llp_sfsalespersonid_entitytype] IS NOT NULL AND s.[llp_sfsalespersonid_entitytype] IS NULL)
        OR v.[llp_sfsalespersonidname] <> s.[llp_sfsalespersonidname]
            OR (v.[llp_sfsalespersonidname] IS NULL AND s.[llp_sfsalespersonidname] IS NOT NULL)
        OR (v.[llp_sfsalespersonidname] IS NOT NULL AND s.[llp_sfsalespersonidname] IS NULL)
        OR v.[llp_sfsalespersonidyominame] <> s.[llp_sfsalespersonidyominame]
            OR (v.[llp_sfsalespersonidyominame] IS NULL AND s.[llp_sfsalespersonidyominame] IS NOT NULL)
        OR (v.[llp_sfsalespersonidyominame] IS NOT NULL AND s.[llp_sfsalespersonidyominame] IS NULL)
        OR v.[llp_sportlanguage] <> s.[llp_sportlanguage]
            OR (v.[llp_sportlanguage] IS NULL AND s.[llp_sportlanguage] IS NOT NULL)
        OR (v.[llp_sportlanguage] IS NOT NULL AND s.[llp_sportlanguage] IS NULL)
        OR v.[llp_sportsellergroup] <> s.[llp_sportsellergroup]
            OR (v.[llp_sportsellergroup] IS NULL AND s.[llp_sportsellergroup] IS NOT NULL)
        OR (v.[llp_sportsellergroup] IS NOT NULL AND s.[llp_sportsellergroup] IS NULL)
        OR v.[llp_sportsellerorganization] <> s.[llp_sportsellerorganization]
            OR (v.[llp_sportsellerorganization] IS NULL AND s.[llp_sportsellerorganization] IS NOT NULL)
        OR (v.[llp_sportsellerorganization] IS NOT NULL AND s.[llp_sportsellerorganization] IS NULL)
        OR v.[llp_utsalespersonid] <> s.[llp_utsalespersonid]
            OR (v.[llp_utsalespersonid] IS NULL AND s.[llp_utsalespersonid] IS NOT NULL)
        OR (v.[llp_utsalespersonid] IS NOT NULL AND s.[llp_utsalespersonid] IS NULL)
        OR v.[llp_utsalespersonid_entitytype] <> s.[llp_utsalespersonid_entitytype]
            OR (v.[llp_utsalespersonid_entitytype] IS NULL AND s.[llp_utsalespersonid_entitytype] IS NOT NULL)
        OR (v.[llp_utsalespersonid_entitytype] IS NOT NULL AND s.[llp_utsalespersonid_entitytype] IS NULL)
        OR v.[llp_utsalespersonidname] <> s.[llp_utsalespersonidname]
            OR (v.[llp_utsalespersonidname] IS NULL AND s.[llp_utsalespersonidname] IS NOT NULL)
        OR (v.[llp_utsalespersonidname] IS NOT NULL AND s.[llp_utsalespersonidname] IS NULL)
        OR v.[llp_utsalespersonidyominame] <> s.[llp_utsalespersonidyominame]
            OR (v.[llp_utsalespersonidyominame] IS NULL AND s.[llp_utsalespersonidyominame] IS NOT NULL)
        OR (v.[llp_utsalespersonidyominame] IS NOT NULL AND s.[llp_utsalespersonidyominame] IS NULL)
        OR v.[llp_xdslogin] <> s.[llp_xdslogin]
            OR (v.[llp_xdslogin] IS NULL AND s.[llp_xdslogin] IS NOT NULL)
        OR (v.[llp_xdslogin] IS NOT NULL AND s.[llp_xdslogin] IS NULL)
        OR v.[middlename] <> s.[middlename]
            OR (v.[middlename] IS NULL AND s.[middlename] IS NOT NULL)
        OR (v.[middlename] IS NOT NULL AND s.[middlename] IS NULL)
        OR v.[mobilealertemail] <> s.[mobilealertemail]
            OR (v.[mobilealertemail] IS NULL AND s.[mobilealertemail] IS NOT NULL)
        OR (v.[mobilealertemail] IS NOT NULL AND s.[mobilealertemail] IS NULL)
        OR v.[mobileofflineprofileid] <> s.[mobileofflineprofileid]
            OR (v.[mobileofflineprofileid] IS NULL AND s.[mobileofflineprofileid] IS NOT NULL)
        OR (v.[mobileofflineprofileid] IS NOT NULL AND s.[mobileofflineprofileid] IS NULL)
        OR v.[mobileofflineprofileid_entitytype] <> s.[mobileofflineprofileid_entitytype]
            OR (v.[mobileofflineprofileid_entitytype] IS NULL AND s.[mobileofflineprofileid_entitytype] IS NOT NULL)
        OR (v.[mobileofflineprofileid_entitytype] IS NOT NULL AND s.[mobileofflineprofileid_entitytype] IS NULL)
        OR v.[mobileofflineprofileidname] <> s.[mobileofflineprofileidname]
            OR (v.[mobileofflineprofileidname] IS NULL AND s.[mobileofflineprofileidname] IS NOT NULL)
        OR (v.[mobileofflineprofileidname] IS NOT NULL AND s.[mobileofflineprofileidname] IS NULL)
        OR v.[mobilephone] <> s.[mobilephone]
            OR (v.[mobilephone] IS NULL AND s.[mobilephone] IS NOT NULL)
        OR (v.[mobilephone] IS NOT NULL AND s.[mobilephone] IS NULL)
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
        OR v.[msdyn_gdproptout] <> s.[msdyn_gdproptout]
            OR (v.[msdyn_gdproptout] IS NULL AND s.[msdyn_gdproptout] IS NOT NULL)
        OR (v.[msdyn_gdproptout] IS NOT NULL AND s.[msdyn_gdproptout] IS NULL)
        OR v.[nickname] <> s.[nickname]
            OR (v.[nickname] IS NULL AND s.[nickname] IS NOT NULL)
        OR (v.[nickname] IS NOT NULL AND s.[nickname] IS NULL)
        OR v.[organizationid] <> s.[organizationid]
            OR (v.[organizationid] IS NULL AND s.[organizationid] IS NOT NULL)
        OR (v.[organizationid] IS NOT NULL AND s.[organizationid] IS NULL)
        OR v.[organizationidname] <> s.[organizationidname]
            OR (v.[organizationidname] IS NULL AND s.[organizationidname] IS NOT NULL)
        OR (v.[organizationidname] IS NOT NULL AND s.[organizationidname] IS NULL)
        OR v.[outgoingemaildeliverymethod] <> s.[outgoingemaildeliverymethod]
            OR (v.[outgoingemaildeliverymethod] IS NULL AND s.[outgoingemaildeliverymethod] IS NOT NULL)
        OR (v.[outgoingemaildeliverymethod] IS NOT NULL AND s.[outgoingemaildeliverymethod] IS NULL)
        OR v.[overriddencreatedon] <> s.[overriddencreatedon]
            OR (v.[overriddencreatedon] IS NULL AND s.[overriddencreatedon] IS NOT NULL)
        OR (v.[overriddencreatedon] IS NOT NULL AND s.[overriddencreatedon] IS NULL)
        OR v.[parentsystemuserid] <> s.[parentsystemuserid]
            OR (v.[parentsystemuserid] IS NULL AND s.[parentsystemuserid] IS NOT NULL)
        OR (v.[parentsystemuserid] IS NOT NULL AND s.[parentsystemuserid] IS NULL)
        OR v.[parentsystemuserid_entitytype] <> s.[parentsystemuserid_entitytype]
            OR (v.[parentsystemuserid_entitytype] IS NULL AND s.[parentsystemuserid_entitytype] IS NOT NULL)
        OR (v.[parentsystemuserid_entitytype] IS NOT NULL AND s.[parentsystemuserid_entitytype] IS NULL)
        OR v.[parentsystemuseridname] <> s.[parentsystemuseridname]
            OR (v.[parentsystemuseridname] IS NULL AND s.[parentsystemuseridname] IS NOT NULL)
        OR (v.[parentsystemuseridname] IS NOT NULL AND s.[parentsystemuseridname] IS NULL)
        OR v.[parentsystemuseridyominame] <> s.[parentsystemuseridyominame]
            OR (v.[parentsystemuseridyominame] IS NULL AND s.[parentsystemuseridyominame] IS NOT NULL)
        OR (v.[parentsystemuseridyominame] IS NOT NULL AND s.[parentsystemuseridyominame] IS NULL)
        OR v.[passporthi] <> s.[passporthi]
            OR (v.[passporthi] IS NULL AND s.[passporthi] IS NOT NULL)
        OR (v.[passporthi] IS NOT NULL AND s.[passporthi] IS NULL)
        OR v.[passportlo] <> s.[passportlo]
            OR (v.[passportlo] IS NULL AND s.[passportlo] IS NOT NULL)
        OR (v.[passportlo] IS NOT NULL AND s.[passportlo] IS NULL)
        OR v.[personalemailaddress] <> s.[personalemailaddress]
            OR (v.[personalemailaddress] IS NULL AND s.[personalemailaddress] IS NOT NULL)
        OR (v.[personalemailaddress] IS NOT NULL AND s.[personalemailaddress] IS NULL)
        OR v.[photourl] <> s.[photourl]
            OR (v.[photourl] IS NULL AND s.[photourl] IS NOT NULL)
        OR (v.[photourl] IS NOT NULL AND s.[photourl] IS NULL)
        OR v.[positionid] <> s.[positionid]
            OR (v.[positionid] IS NULL AND s.[positionid] IS NOT NULL)
        OR (v.[positionid] IS NOT NULL AND s.[positionid] IS NULL)
        OR v.[positionid_entitytype] <> s.[positionid_entitytype]
            OR (v.[positionid_entitytype] IS NULL AND s.[positionid_entitytype] IS NOT NULL)
        OR (v.[positionid_entitytype] IS NOT NULL AND s.[positionid_entitytype] IS NULL)
        OR v.[positionidname] <> s.[positionidname]
            OR (v.[positionidname] IS NULL AND s.[positionidname] IS NOT NULL)
        OR (v.[positionidname] IS NOT NULL AND s.[positionidname] IS NULL)
        OR v.[preferredaddresscode] <> s.[preferredaddresscode]
            OR (v.[preferredaddresscode] IS NULL AND s.[preferredaddresscode] IS NOT NULL)
        OR (v.[preferredaddresscode] IS NOT NULL AND s.[preferredaddresscode] IS NULL)
        OR v.[preferredemailcode] <> s.[preferredemailcode]
            OR (v.[preferredemailcode] IS NULL AND s.[preferredemailcode] IS NOT NULL)
        OR (v.[preferredemailcode] IS NOT NULL AND s.[preferredemailcode] IS NULL)
        OR v.[preferredphonecode] <> s.[preferredphonecode]
            OR (v.[preferredphonecode] IS NULL AND s.[preferredphonecode] IS NOT NULL)
        OR (v.[preferredphonecode] IS NOT NULL AND s.[preferredphonecode] IS NULL)
        OR v.[processid] <> s.[processid]
            OR (v.[processid] IS NULL AND s.[processid] IS NOT NULL)
        OR (v.[processid] IS NOT NULL AND s.[processid] IS NULL)
        OR v.[queueid] <> s.[queueid]
            OR (v.[queueid] IS NULL AND s.[queueid] IS NOT NULL)
        OR (v.[queueid] IS NOT NULL AND s.[queueid] IS NULL)
        OR v.[queueid_entitytype] <> s.[queueid_entitytype]
            OR (v.[queueid_entitytype] IS NULL AND s.[queueid_entitytype] IS NOT NULL)
        OR (v.[queueid_entitytype] IS NOT NULL AND s.[queueid_entitytype] IS NULL)
        OR v.[queueidname] <> s.[queueidname]
            OR (v.[queueidname] IS NULL AND s.[queueidname] IS NOT NULL)
        OR (v.[queueidname] IS NOT NULL AND s.[queueidname] IS NULL)
        OR v.[salutation] <> s.[salutation]
            OR (v.[salutation] IS NULL AND s.[salutation] IS NOT NULL)
        OR (v.[salutation] IS NOT NULL AND s.[salutation] IS NULL)
        OR v.[setupuser] <> s.[setupuser]
            OR (v.[setupuser] IS NULL AND s.[setupuser] IS NOT NULL)
        OR (v.[setupuser] IS NOT NULL AND s.[setupuser] IS NULL)
        OR v.[sharepointemailaddress] <> s.[sharepointemailaddress]
            OR (v.[sharepointemailaddress] IS NULL AND s.[sharepointemailaddress] IS NOT NULL)
        OR (v.[sharepointemailaddress] IS NOT NULL AND s.[sharepointemailaddress] IS NULL)
        OR v.[SinkCreatedOn] <> s.[SinkCreatedOn]
            OR (v.[SinkCreatedOn] IS NULL AND s.[SinkCreatedOn] IS NOT NULL)
        OR (v.[SinkCreatedOn] IS NOT NULL AND s.[SinkCreatedOn] IS NULL)
        OR v.[SinkModifiedOn] <> s.[SinkModifiedOn]
            OR (v.[SinkModifiedOn] IS NULL AND s.[SinkModifiedOn] IS NOT NULL)
        OR (v.[SinkModifiedOn] IS NOT NULL AND s.[SinkModifiedOn] IS NULL)
        OR v.[siteid] <> s.[siteid]
            OR (v.[siteid] IS NULL AND s.[siteid] IS NOT NULL)
        OR (v.[siteid] IS NOT NULL AND s.[siteid] IS NULL)
        OR v.[siteid_entitytype] <> s.[siteid_entitytype]
            OR (v.[siteid_entitytype] IS NULL AND s.[siteid_entitytype] IS NOT NULL)
        OR (v.[siteid_entitytype] IS NOT NULL AND s.[siteid_entitytype] IS NULL)
        OR v.[siteidname] <> s.[siteidname]
            OR (v.[siteidname] IS NULL AND s.[siteidname] IS NOT NULL)
        OR (v.[siteidname] IS NOT NULL AND s.[siteidname] IS NULL)
        OR v.[skills] <> s.[skills]
            OR (v.[skills] IS NULL AND s.[skills] IS NOT NULL)
        OR (v.[skills] IS NOT NULL AND s.[skills] IS NULL)
        OR v.[stageid] <> s.[stageid]
            OR (v.[stageid] IS NULL AND s.[stageid] IS NOT NULL)
        OR (v.[stageid] IS NOT NULL AND s.[stageid] IS NULL)
        OR v.[systemuserid] <> s.[systemuserid]
            OR (v.[systemuserid] IS NULL AND s.[systemuserid] IS NOT NULL)
        OR (v.[systemuserid] IS NOT NULL AND s.[systemuserid] IS NULL)
        OR v.[territoryid] <> s.[territoryid]
            OR (v.[territoryid] IS NULL AND s.[territoryid] IS NOT NULL)
        OR (v.[territoryid] IS NOT NULL AND s.[territoryid] IS NULL)
        OR v.[territoryid_entitytype] <> s.[territoryid_entitytype]
            OR (v.[territoryid_entitytype] IS NULL AND s.[territoryid_entitytype] IS NOT NULL)
        OR (v.[territoryid_entitytype] IS NOT NULL AND s.[territoryid_entitytype] IS NULL)
        OR v.[territoryidname] <> s.[territoryidname]
            OR (v.[territoryidname] IS NULL AND s.[territoryidname] IS NOT NULL)
        OR (v.[territoryidname] IS NOT NULL AND s.[territoryidname] IS NULL)
        OR v.[timezoneruleversionnumber] <> s.[timezoneruleversionnumber]
            OR (v.[timezoneruleversionnumber] IS NULL AND s.[timezoneruleversionnumber] IS NOT NULL)
        OR (v.[timezoneruleversionnumber] IS NOT NULL AND s.[timezoneruleversionnumber] IS NULL)
        OR v.[title] <> s.[title]
            OR (v.[title] IS NULL AND s.[title] IS NOT NULL)
        OR (v.[title] IS NOT NULL AND s.[title] IS NULL)
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
        OR v.[userlicensetype] <> s.[userlicensetype]
            OR (v.[userlicensetype] IS NULL AND s.[userlicensetype] IS NOT NULL)
        OR (v.[userlicensetype] IS NOT NULL AND s.[userlicensetype] IS NULL)
        OR v.[userpuid] <> s.[userpuid]
            OR (v.[userpuid] IS NULL AND s.[userpuid] IS NOT NULL)
        OR (v.[userpuid] IS NOT NULL AND s.[userpuid] IS NULL)
        OR v.[utcconversiontimezonecode] <> s.[utcconversiontimezonecode]
            OR (v.[utcconversiontimezonecode] IS NULL AND s.[utcconversiontimezonecode] IS NOT NULL)
        OR (v.[utcconversiontimezonecode] IS NOT NULL AND s.[utcconversiontimezonecode] IS NULL)
        OR v.[versionnumber] <> s.[versionnumber]
            OR (v.[versionnumber] IS NULL AND s.[versionnumber] IS NOT NULL)
        OR (v.[versionnumber] IS NOT NULL AND s.[versionnumber] IS NULL)
        OR v.[windowsliveid] <> s.[windowsliveid]
            OR (v.[windowsliveid] IS NULL AND s.[windowsliveid] IS NOT NULL)
        OR (v.[windowsliveid] IS NOT NULL AND s.[windowsliveid] IS NULL)
        OR v.[yammeremailaddress] <> s.[yammeremailaddress]
            OR (v.[yammeremailaddress] IS NULL AND s.[yammeremailaddress] IS NOT NULL)
        OR (v.[yammeremailaddress] IS NOT NULL AND s.[yammeremailaddress] IS NULL)
        OR v.[yammeruserid] <> s.[yammeruserid]
            OR (v.[yammeruserid] IS NULL AND s.[yammeruserid] IS NOT NULL)
        OR (v.[yammeruserid] IS NOT NULL AND s.[yammeruserid] IS NULL)
        OR v.[yomifirstname] <> s.[yomifirstname]
            OR (v.[yomifirstname] IS NULL AND s.[yomifirstname] IS NOT NULL)
        OR (v.[yomifirstname] IS NOT NULL AND s.[yomifirstname] IS NULL)
        OR v.[yomifullname] <> s.[yomifullname]
            OR (v.[yomifullname] IS NULL AND s.[yomifullname] IS NOT NULL)
        OR (v.[yomifullname] IS NOT NULL AND s.[yomifullname] IS NULL)
        OR v.[yomilastname] <> s.[yomilastname]
            OR (v.[yomilastname] IS NULL AND s.[yomilastname] IS NOT NULL)
        OR (v.[yomilastname] IS NOT NULL AND s.[yomilastname] IS NULL)
        OR v.[yomimiddlename] <> s.[yomimiddlename]
            OR (v.[yomimiddlename] IS NULL AND s.[yomimiddlename] IS NOT NULL)
        OR (v.[yomimiddlename] IS NOT NULL AND s.[yomimiddlename] IS NULL)
        )
        THEN 
            UPDATE SET
                [ThreadLogUpdateId] = @ThreadLogId
            

                
        WHEN NOT MATCHED BY TARGET 
            THEN INSERT
            ( 
            [Id]
            , [accessmode]
            , [activedirectoryguid]
            , [address1_addressid]
            , [address1_addresstypecode]
            , [address1_city]
            , [address1_composite]
            , [address1_country]
            , [address1_county]
            , [address1_fax]
            , [address1_latitude]
            , [address1_line1]
            , [address1_line2]
            , [address1_line3]
            , [address1_longitude]
            , [address1_name]
            , [address1_postalcode]
            , [address1_postofficebox]
            , [address1_shippingmethodcode]
            , [address1_stateorprovince]
            , [address1_telephone1]
            , [address1_telephone2]
            , [address1_telephone3]
            , [address1_upszone]
            , [address1_utcoffset]
            , [address2_addressid]
            , [address2_addresstypecode]
            , [address2_city]
            , [address2_composite]
            , [address2_country]
            , [address2_county]
            , [address2_fax]
            , [address2_latitude]
            , [address2_line1]
            , [address2_line2]
            , [address2_line3]
            , [address2_longitude]
            , [address2_name]
            , [address2_postalcode]
            , [address2_postofficebox]
            , [address2_shippingmethodcode]
            , [address2_stateorprovince]
            , [address2_telephone1]
            , [address2_telephone2]
            , [address2_telephone3]
            , [address2_upszone]
            , [address2_utcoffset]
            , [applicationid]
            , [applicationiduri]
            , [azureactivedirectoryobjectid]
            , [businessunitid]
            , [businessunitid_entitytype]
            , [businessunitidname]
            , [calendarid]
            , [calendarid_entitytype]
            , [caltype]
            , [createdby]
            , [createdby_entitytype]
            , [createdbyname]
            , [createdbyyominame]
            , [createdon]
            , [createdonbehalfby]
            , [createdonbehalfby_entitytype]
            , [createdonbehalfbyname]
            , [createdonbehalfbyyominame]
            , [defaultfilterspopulated]
            , [defaultmailbox]
            , [defaultmailbox_entitytype]
            , [defaultmailboxname]
            , [defaultodbfoldername]
            , [disabledreason]
            , [displayinserviceviews]
            , [domainname]
            , [emailrouteraccessapproval]
            , [employeeid]
            , [entityimage_timestamp]
            , [entityimage_url]
            , [entityimageid]
            , [exchangerate]
            , [firstname]
            , [fullname]
            , [governmentid]
            , [homephone]
            , [identityid]
            , [importsequencenumber]
            , [incomingemaildeliverymethod]
            , [internalemailaddress]
            , [invitestatuscode]
            , [isactivedirectoryuser]
            , [isdisabled]
            , [isemailaddressapprovedbyo365admin]
            , [isintegrationuser]
            , [islicensed]
            , [issyncwithdirectory]
            , [jobtitle]
            , [lastname]
            , [latestupdatetime]
            , [llp_arbesdbname]
            , [llp_arbessyncallowed]
            , [llp_automastersyncallowed]
            , [llp_automastersyncdbname]
            , [llp_automaticallysendtoautomaster]
            , [llp_certsyncallowed]
            , [llp_certsyncdbname]
            , [llp_defaultopportunitytype]
            , [llp_idnetsuite]
            , [llp_sfinsuranceid]
            , [llp_sfinsuranceid_entitytype]
            , [llp_sfinsuranceidname]
            , [llp_sfinsuranceidyominame]
            , [llp_sfsalespersonid]
            , [llp_sfsalespersonid_entitytype]
            , [llp_sfsalespersonidname]
            , [llp_sfsalespersonidyominame]
            , [llp_sportlanguage]
            , [llp_sportsellergroup]
            , [llp_sportsellerorganization]
            , [llp_utsalespersonid]
            , [llp_utsalespersonid_entitytype]
            , [llp_utsalespersonidname]
            , [llp_utsalespersonidyominame]
            , [llp_xdslogin]
            , [middlename]
            , [mobilealertemail]
            , [mobileofflineprofileid]
            , [mobileofflineprofileid_entitytype]
            , [mobileofflineprofileidname]
            , [mobilephone]
            , [modifiedby]
            , [modifiedby_entitytype]
            , [modifiedbyname]
            , [modifiedbyyominame]
            , [modifiedon]
            , [modifiedonbehalfby]
            , [modifiedonbehalfby_entitytype]
            , [modifiedonbehalfbyname]
            , [modifiedonbehalfbyyominame]
            , [msdyn_gdproptout]
            , [nickname]
            , [organizationid]
            , [organizationidname]
            , [outgoingemaildeliverymethod]
            , [overriddencreatedon]
            , [parentsystemuserid]
            , [parentsystemuserid_entitytype]
            , [parentsystemuseridname]
            , [parentsystemuseridyominame]
            , [passporthi]
            , [passportlo]
            , [personalemailaddress]
            , [photourl]
            , [positionid]
            , [positionid_entitytype]
            , [positionidname]
            , [preferredaddresscode]
            , [preferredemailcode]
            , [preferredphonecode]
            , [processid]
            , [queueid]
            , [queueid_entitytype]
            , [queueidname]
            , [salutation]
            , [setupuser]
            , [sharepointemailaddress]
            , [SinkCreatedOn]
            , [SinkModifiedOn]
            , [siteid]
            , [siteid_entitytype]
            , [siteidname]
            , [skills]
            , [stageid]
            , [systemuserid]
            , [territoryid]
            , [territoryid_entitytype]
            , [territoryidname]
            , [timezoneruleversionnumber]
            , [title]
            , [transactioncurrencyid]
            , [transactioncurrencyid_entitytype]
            , [transactioncurrencyidname]
            , [traversedpath]
            , [userlicensetype]
            , [userpuid]
            , [utcconversiontimezonecode]
            , [versionnumber]
            , [windowsliveid]
            , [yammeremailaddress]
            , [yammeruserid]
            , [yomifirstname]
            , [yomifullname]
            , [yomilastname]
            , [yomimiddlename]
            , [DataSourceId]
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
            
    ) VALUES (
            s.[Id]
            , s.[accessmode]
            , s.[activedirectoryguid]
            , s.[address1_addressid]
            , s.[address1_addresstypecode]
            , s.[address1_city]
            , s.[address1_composite]
            , s.[address1_country]
            , s.[address1_county]
            , s.[address1_fax]
            , s.[address1_latitude]
            , s.[address1_line1]
            , s.[address1_line2]
            , s.[address1_line3]
            , s.[address1_longitude]
            , s.[address1_name]
            , s.[address1_postalcode]
            , s.[address1_postofficebox]
            , s.[address1_shippingmethodcode]
            , s.[address1_stateorprovince]
            , s.[address1_telephone1]
            , s.[address1_telephone2]
            , s.[address1_telephone3]
            , s.[address1_upszone]
            , s.[address1_utcoffset]
            , s.[address2_addressid]
            , s.[address2_addresstypecode]
            , s.[address2_city]
            , s.[address2_composite]
            , s.[address2_country]
            , s.[address2_county]
            , s.[address2_fax]
            , s.[address2_latitude]
            , s.[address2_line1]
            , s.[address2_line2]
            , s.[address2_line3]
            , s.[address2_longitude]
            , s.[address2_name]
            , s.[address2_postalcode]
            , s.[address2_postofficebox]
            , s.[address2_shippingmethodcode]
            , s.[address2_stateorprovince]
            , s.[address2_telephone1]
            , s.[address2_telephone2]
            , s.[address2_telephone3]
            , s.[address2_upszone]
            , s.[address2_utcoffset]
            , s.[applicationid]
            , s.[applicationiduri]
            , s.[azureactivedirectoryobjectid]
            , s.[businessunitid]
            , s.[businessunitid_entitytype]
            , s.[businessunitidname]
            , s.[calendarid]
            , s.[calendarid_entitytype]
            , s.[caltype]
            , s.[createdby]
            , s.[createdby_entitytype]
            , s.[createdbyname]
            , s.[createdbyyominame]
            , s.[createdon]
            , s.[createdonbehalfby]
            , s.[createdonbehalfby_entitytype]
            , s.[createdonbehalfbyname]
            , s.[createdonbehalfbyyominame]
            , s.[defaultfilterspopulated]
            , s.[defaultmailbox]
            , s.[defaultmailbox_entitytype]
            , s.[defaultmailboxname]
            , s.[defaultodbfoldername]
            , s.[disabledreason]
            , s.[displayinserviceviews]
            , s.[domainname]
            , s.[emailrouteraccessapproval]
            , s.[employeeid]
            , s.[entityimage_timestamp]
            , s.[entityimage_url]
            , s.[entityimageid]
            , s.[exchangerate]
            , s.[firstname]
            , s.[fullname]
            , s.[governmentid]
            , s.[homephone]
            , s.[identityid]
            , s.[importsequencenumber]
            , s.[incomingemaildeliverymethod]
            , s.[internalemailaddress]
            , s.[invitestatuscode]
            , s.[isactivedirectoryuser]
            , s.[isdisabled]
            , s.[isemailaddressapprovedbyo365admin]
            , s.[isintegrationuser]
            , s.[islicensed]
            , s.[issyncwithdirectory]
            , s.[jobtitle]
            , s.[lastname]
            , s.[latestupdatetime]
            , s.[llp_arbesdbname]
            , s.[llp_arbessyncallowed]
            , s.[llp_automastersyncallowed]
            , s.[llp_automastersyncdbname]
            , s.[llp_automaticallysendtoautomaster]
            , s.[llp_certsyncallowed]
            , s.[llp_certsyncdbname]
            , s.[llp_defaultopportunitytype]
            , s.[llp_idnetsuite]
            , s.[llp_sfinsuranceid]
            , s.[llp_sfinsuranceid_entitytype]
            , s.[llp_sfinsuranceidname]
            , s.[llp_sfinsuranceidyominame]
            , s.[llp_sfsalespersonid]
            , s.[llp_sfsalespersonid_entitytype]
            , s.[llp_sfsalespersonidname]
            , s.[llp_sfsalespersonidyominame]
            , s.[llp_sportlanguage]
            , s.[llp_sportsellergroup]
            , s.[llp_sportsellerorganization]
            , s.[llp_utsalespersonid]
            , s.[llp_utsalespersonid_entitytype]
            , s.[llp_utsalespersonidname]
            , s.[llp_utsalespersonidyominame]
            , s.[llp_xdslogin]
            , s.[middlename]
            , s.[mobilealertemail]
            , s.[mobileofflineprofileid]
            , s.[mobileofflineprofileid_entitytype]
            , s.[mobileofflineprofileidname]
            , s.[mobilephone]
            , s.[modifiedby]
            , s.[modifiedby_entitytype]
            , s.[modifiedbyname]
            , s.[modifiedbyyominame]
            , s.[modifiedon]
            , s.[modifiedonbehalfby]
            , s.[modifiedonbehalfby_entitytype]
            , s.[modifiedonbehalfbyname]
            , s.[modifiedonbehalfbyyominame]
            , s.[msdyn_gdproptout]
            , s.[nickname]
            , s.[organizationid]
            , s.[organizationidname]
            , s.[outgoingemaildeliverymethod]
            , s.[overriddencreatedon]
            , s.[parentsystemuserid]
            , s.[parentsystemuserid_entitytype]
            , s.[parentsystemuseridname]
            , s.[parentsystemuseridyominame]
            , s.[passporthi]
            , s.[passportlo]
            , s.[personalemailaddress]
            , s.[photourl]
            , s.[positionid]
            , s.[positionid_entitytype]
            , s.[positionidname]
            , s.[preferredaddresscode]
            , s.[preferredemailcode]
            , s.[preferredphonecode]
            , s.[processid]
            , s.[queueid]
            , s.[queueid_entitytype]
            , s.[queueidname]
            , s.[salutation]
            , s.[setupuser]
            , s.[sharepointemailaddress]
            , s.[SinkCreatedOn]
            , s.[SinkModifiedOn]
            , s.[siteid]
            , s.[siteid_entitytype]
            , s.[siteidname]
            , s.[skills]
            , s.[stageid]
            , s.[systemuserid]
            , s.[territoryid]
            , s.[territoryid_entitytype]
            , s.[territoryidname]
            , s.[timezoneruleversionnumber]
            , s.[title]
            , s.[transactioncurrencyid]
            , s.[transactioncurrencyid_entitytype]
            , s.[transactioncurrencyidname]
            , s.[traversedpath]
            , s.[userlicensetype]
            , s.[userpuid]
            , s.[utcconversiontimezonecode]
            , s.[versionnumber]
            , s.[windowsliveid]
            , s.[yammeremailaddress]
            , s.[yammeruserid]
            , s.[yomifirstname]
            , s.[yomifullname]
            , s.[yomilastname]
            , s.[yomimiddlename]
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
    
    INSERT INTO [Vault].[CRMdboSystemuser] (
            [Id]
            , [accessmode]
            , [activedirectoryguid]
            , [address1_addressid]
            , [address1_addresstypecode]
            , [address1_city]
            , [address1_composite]
            , [address1_country]
            , [address1_county]
            , [address1_fax]
            , [address1_latitude]
            , [address1_line1]
            , [address1_line2]
            , [address1_line3]
            , [address1_longitude]
            , [address1_name]
            , [address1_postalcode]
            , [address1_postofficebox]
            , [address1_shippingmethodcode]
            , [address1_stateorprovince]
            , [address1_telephone1]
            , [address1_telephone2]
            , [address1_telephone3]
            , [address1_upszone]
            , [address1_utcoffset]
            , [address2_addressid]
            , [address2_addresstypecode]
            , [address2_city]
            , [address2_composite]
            , [address2_country]
            , [address2_county]
            , [address2_fax]
            , [address2_latitude]
            , [address2_line1]
            , [address2_line2]
            , [address2_line3]
            , [address2_longitude]
            , [address2_name]
            , [address2_postalcode]
            , [address2_postofficebox]
            , [address2_shippingmethodcode]
            , [address2_stateorprovince]
            , [address2_telephone1]
            , [address2_telephone2]
            , [address2_telephone3]
            , [address2_upszone]
            , [address2_utcoffset]
            , [applicationid]
            , [applicationiduri]
            , [azureactivedirectoryobjectid]
            , [businessunitid]
            , [businessunitid_entitytype]
            , [businessunitidname]
            , [calendarid]
            , [calendarid_entitytype]
            , [caltype]
            , [createdby]
            , [createdby_entitytype]
            , [createdbyname]
            , [createdbyyominame]
            , [createdon]
            , [createdonbehalfby]
            , [createdonbehalfby_entitytype]
            , [createdonbehalfbyname]
            , [createdonbehalfbyyominame]
            , [defaultfilterspopulated]
            , [defaultmailbox]
            , [defaultmailbox_entitytype]
            , [defaultmailboxname]
            , [defaultodbfoldername]
            , [disabledreason]
            , [displayinserviceviews]
            , [domainname]
            , [emailrouteraccessapproval]
            , [employeeid]
            , [entityimage_timestamp]
            , [entityimage_url]
            , [entityimageid]
            , [exchangerate]
            , [firstname]
            , [fullname]
            , [governmentid]
            , [homephone]
            , [identityid]
            , [importsequencenumber]
            , [incomingemaildeliverymethod]
            , [internalemailaddress]
            , [invitestatuscode]
            , [isactivedirectoryuser]
            , [isdisabled]
            , [isemailaddressapprovedbyo365admin]
            , [isintegrationuser]
            , [islicensed]
            , [issyncwithdirectory]
            , [jobtitle]
            , [lastname]
            , [latestupdatetime]
            , [llp_arbesdbname]
            , [llp_arbessyncallowed]
            , [llp_automastersyncallowed]
            , [llp_automastersyncdbname]
            , [llp_automaticallysendtoautomaster]
            , [llp_certsyncallowed]
            , [llp_certsyncdbname]
            , [llp_defaultopportunitytype]
            , [llp_idnetsuite]
            , [llp_sfinsuranceid]
            , [llp_sfinsuranceid_entitytype]
            , [llp_sfinsuranceidname]
            , [llp_sfinsuranceidyominame]
            , [llp_sfsalespersonid]
            , [llp_sfsalespersonid_entitytype]
            , [llp_sfsalespersonidname]
            , [llp_sfsalespersonidyominame]
            , [llp_sportlanguage]
            , [llp_sportsellergroup]
            , [llp_sportsellerorganization]
            , [llp_utsalespersonid]
            , [llp_utsalespersonid_entitytype]
            , [llp_utsalespersonidname]
            , [llp_utsalespersonidyominame]
            , [llp_xdslogin]
            , [middlename]
            , [mobilealertemail]
            , [mobileofflineprofileid]
            , [mobileofflineprofileid_entitytype]
            , [mobileofflineprofileidname]
            , [mobilephone]
            , [modifiedby]
            , [modifiedby_entitytype]
            , [modifiedbyname]
            , [modifiedbyyominame]
            , [modifiedon]
            , [modifiedonbehalfby]
            , [modifiedonbehalfby_entitytype]
            , [modifiedonbehalfbyname]
            , [modifiedonbehalfbyyominame]
            , [msdyn_gdproptout]
            , [nickname]
            , [organizationid]
            , [organizationidname]
            , [outgoingemaildeliverymethod]
            , [overriddencreatedon]
            , [parentsystemuserid]
            , [parentsystemuserid_entitytype]
            , [parentsystemuseridname]
            , [parentsystemuseridyominame]
            , [passporthi]
            , [passportlo]
            , [personalemailaddress]
            , [photourl]
            , [positionid]
            , [positionid_entitytype]
            , [positionidname]
            , [preferredaddresscode]
            , [preferredemailcode]
            , [preferredphonecode]
            , [processid]
            , [queueid]
            , [queueid_entitytype]
            , [queueidname]
            , [salutation]
            , [setupuser]
            , [sharepointemailaddress]
            , [SinkCreatedOn]
            , [SinkModifiedOn]
            , [siteid]
            , [siteid_entitytype]
            , [siteidname]
            , [skills]
            , [stageid]
            , [systemuserid]
            , [territoryid]
            , [territoryid_entitytype]
            , [territoryidname]
            , [timezoneruleversionnumber]
            , [title]
            , [transactioncurrencyid]
            , [transactioncurrencyid_entitytype]
            , [transactioncurrencyidname]
            , [traversedpath]
            , [userlicensetype]
            , [userpuid]
            , [utcconversiontimezonecode]
            , [versionnumber]
            , [windowsliveid]
            , [yammeremailaddress]
            , [yammeruserid]
            , [yomifirstname]
            , [yomifullname]
            , [yomilastname]
            , [yomimiddlename]
            , [DataSourceId]
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
        
    ) 
    OUTPUT Inserted.ThreadLogUpdateId INTO @UpdateRowCounts
    SELECT

            s.[Id]
            , s.[accessmode]
            , s.[activedirectoryguid]
            , s.[address1_addressid]
            , s.[address1_addresstypecode]
            , s.[address1_city]
            , s.[address1_composite]
            , s.[address1_country]
            , s.[address1_county]
            , s.[address1_fax]
            , s.[address1_latitude]
            , s.[address1_line1]
            , s.[address1_line2]
            , s.[address1_line3]
            , s.[address1_longitude]
            , s.[address1_name]
            , s.[address1_postalcode]
            , s.[address1_postofficebox]
            , s.[address1_shippingmethodcode]
            , s.[address1_stateorprovince]
            , s.[address1_telephone1]
            , s.[address1_telephone2]
            , s.[address1_telephone3]
            , s.[address1_upszone]
            , s.[address1_utcoffset]
            , s.[address2_addressid]
            , s.[address2_addresstypecode]
            , s.[address2_city]
            , s.[address2_composite]
            , s.[address2_country]
            , s.[address2_county]
            , s.[address2_fax]
            , s.[address2_latitude]
            , s.[address2_line1]
            , s.[address2_line2]
            , s.[address2_line3]
            , s.[address2_longitude]
            , s.[address2_name]
            , s.[address2_postalcode]
            , s.[address2_postofficebox]
            , s.[address2_shippingmethodcode]
            , s.[address2_stateorprovince]
            , s.[address2_telephone1]
            , s.[address2_telephone2]
            , s.[address2_telephone3]
            , s.[address2_upszone]
            , s.[address2_utcoffset]
            , s.[applicationid]
            , s.[applicationiduri]
            , s.[azureactivedirectoryobjectid]
            , s.[businessunitid]
            , s.[businessunitid_entitytype]
            , s.[businessunitidname]
            , s.[calendarid]
            , s.[calendarid_entitytype]
            , s.[caltype]
            , s.[createdby]
            , s.[createdby_entitytype]
            , s.[createdbyname]
            , s.[createdbyyominame]
            , s.[createdon]
            , s.[createdonbehalfby]
            , s.[createdonbehalfby_entitytype]
            , s.[createdonbehalfbyname]
            , s.[createdonbehalfbyyominame]
            , s.[defaultfilterspopulated]
            , s.[defaultmailbox]
            , s.[defaultmailbox_entitytype]
            , s.[defaultmailboxname]
            , s.[defaultodbfoldername]
            , s.[disabledreason]
            , s.[displayinserviceviews]
            , s.[domainname]
            , s.[emailrouteraccessapproval]
            , s.[employeeid]
            , s.[entityimage_timestamp]
            , s.[entityimage_url]
            , s.[entityimageid]
            , s.[exchangerate]
            , s.[firstname]
            , s.[fullname]
            , s.[governmentid]
            , s.[homephone]
            , s.[identityid]
            , s.[importsequencenumber]
            , s.[incomingemaildeliverymethod]
            , s.[internalemailaddress]
            , s.[invitestatuscode]
            , s.[isactivedirectoryuser]
            , s.[isdisabled]
            , s.[isemailaddressapprovedbyo365admin]
            , s.[isintegrationuser]
            , s.[islicensed]
            , s.[issyncwithdirectory]
            , s.[jobtitle]
            , s.[lastname]
            , s.[latestupdatetime]
            , s.[llp_arbesdbname]
            , s.[llp_arbessyncallowed]
            , s.[llp_automastersyncallowed]
            , s.[llp_automastersyncdbname]
            , s.[llp_automaticallysendtoautomaster]
            , s.[llp_certsyncallowed]
            , s.[llp_certsyncdbname]
            , s.[llp_defaultopportunitytype]
            , s.[llp_idnetsuite]
            , s.[llp_sfinsuranceid]
            , s.[llp_sfinsuranceid_entitytype]
            , s.[llp_sfinsuranceidname]
            , s.[llp_sfinsuranceidyominame]
            , s.[llp_sfsalespersonid]
            , s.[llp_sfsalespersonid_entitytype]
            , s.[llp_sfsalespersonidname]
            , s.[llp_sfsalespersonidyominame]
            , s.[llp_sportlanguage]
            , s.[llp_sportsellergroup]
            , s.[llp_sportsellerorganization]
            , s.[llp_utsalespersonid]
            , s.[llp_utsalespersonid_entitytype]
            , s.[llp_utsalespersonidname]
            , s.[llp_utsalespersonidyominame]
            , s.[llp_xdslogin]
            , s.[middlename]
            , s.[mobilealertemail]
            , s.[mobileofflineprofileid]
            , s.[mobileofflineprofileid_entitytype]
            , s.[mobileofflineprofileidname]
            , s.[mobilephone]
            , s.[modifiedby]
            , s.[modifiedby_entitytype]
            , s.[modifiedbyname]
            , s.[modifiedbyyominame]
            , s.[modifiedon]
            , s.[modifiedonbehalfby]
            , s.[modifiedonbehalfby_entitytype]
            , s.[modifiedonbehalfbyname]
            , s.[modifiedonbehalfbyyominame]
            , s.[msdyn_gdproptout]
            , s.[nickname]
            , s.[organizationid]
            , s.[organizationidname]
            , s.[outgoingemaildeliverymethod]
            , s.[overriddencreatedon]
            , s.[parentsystemuserid]
            , s.[parentsystemuserid_entitytype]
            , s.[parentsystemuseridname]
            , s.[parentsystemuseridyominame]
            , s.[passporthi]
            , s.[passportlo]
            , s.[personalemailaddress]
            , s.[photourl]
            , s.[positionid]
            , s.[positionid_entitytype]
            , s.[positionidname]
            , s.[preferredaddresscode]
            , s.[preferredemailcode]
            , s.[preferredphonecode]
            , s.[processid]
            , s.[queueid]
            , s.[queueid_entitytype]
            , s.[queueidname]
            , s.[salutation]
            , s.[setupuser]
            , s.[sharepointemailaddress]
            , s.[SinkCreatedOn]
            , s.[SinkModifiedOn]
            , s.[siteid]
            , s.[siteid_entitytype]
            , s.[siteidname]
            , s.[skills]
            , s.[stageid]
            , s.[systemuserid]
            , s.[territoryid]
            , s.[territoryid_entitytype]
            , s.[territoryidname]
            , s.[timezoneruleversionnumber]
            , s.[title]
            , s.[transactioncurrencyid]
            , s.[transactioncurrencyid_entitytype]
            , s.[transactioncurrencyidname]
            , s.[traversedpath]
            , s.[userlicensetype]
            , s.[userpuid]
            , s.[utcconversiontimezonecode]
            , s.[versionnumber]
            , s.[windowsliveid]
            , s.[yammeremailaddress]
            , s.[yammeruserid]
            , s.[yomifirstname]
            , s.[yomifullname]
            , s.[yomilastname]
            , s.[yomimiddlename]
            , s.[DataSourceId]
            , @ThreadLogId
            , -1
            , -1
            , N'U' -- update
    FROM Stage.CRMdboSystemuser AS s
    INNER JOIN Vault.CRMdboSystemuser AS v
        ON  s.[Id] = v.[Id] AND v.ThreadLogUpdateId = @ThreadLogId
    
    INSERT INTO [Vault].[CRMdboSystemuser] (
            [Id]
            , [accessmode]
            , [activedirectoryguid]
            , [address1_addressid]
            , [address1_addresstypecode]
            , [address1_city]
            , [address1_composite]
            , [address1_country]
            , [address1_county]
            , [address1_fax]
            , [address1_latitude]
            , [address1_line1]
            , [address1_line2]
            , [address1_line3]
            , [address1_longitude]
            , [address1_name]
            , [address1_postalcode]
            , [address1_postofficebox]
            , [address1_shippingmethodcode]
            , [address1_stateorprovince]
            , [address1_telephone1]
            , [address1_telephone2]
            , [address1_telephone3]
            , [address1_upszone]
            , [address1_utcoffset]
            , [address2_addressid]
            , [address2_addresstypecode]
            , [address2_city]
            , [address2_composite]
            , [address2_country]
            , [address2_county]
            , [address2_fax]
            , [address2_latitude]
            , [address2_line1]
            , [address2_line2]
            , [address2_line3]
            , [address2_longitude]
            , [address2_name]
            , [address2_postalcode]
            , [address2_postofficebox]
            , [address2_shippingmethodcode]
            , [address2_stateorprovince]
            , [address2_telephone1]
            , [address2_telephone2]
            , [address2_telephone3]
            , [address2_upszone]
            , [address2_utcoffset]
            , [applicationid]
            , [applicationiduri]
            , [azureactivedirectoryobjectid]
            , [businessunitid]
            , [businessunitid_entitytype]
            , [businessunitidname]
            , [calendarid]
            , [calendarid_entitytype]
            , [caltype]
            , [createdby]
            , [createdby_entitytype]
            , [createdbyname]
            , [createdbyyominame]
            , [createdon]
            , [createdonbehalfby]
            , [createdonbehalfby_entitytype]
            , [createdonbehalfbyname]
            , [createdonbehalfbyyominame]
            , [defaultfilterspopulated]
            , [defaultmailbox]
            , [defaultmailbox_entitytype]
            , [defaultmailboxname]
            , [defaultodbfoldername]
            , [disabledreason]
            , [displayinserviceviews]
            , [domainname]
            , [emailrouteraccessapproval]
            , [employeeid]
            , [entityimage_timestamp]
            , [entityimage_url]
            , [entityimageid]
            , [exchangerate]
            , [firstname]
            , [fullname]
            , [governmentid]
            , [homephone]
            , [identityid]
            , [importsequencenumber]
            , [incomingemaildeliverymethod]
            , [internalemailaddress]
            , [invitestatuscode]
            , [isactivedirectoryuser]
            , [isdisabled]
            , [isemailaddressapprovedbyo365admin]
            , [isintegrationuser]
            , [islicensed]
            , [issyncwithdirectory]
            , [jobtitle]
            , [lastname]
            , [latestupdatetime]
            , [llp_arbesdbname]
            , [llp_arbessyncallowed]
            , [llp_automastersyncallowed]
            , [llp_automastersyncdbname]
            , [llp_automaticallysendtoautomaster]
            , [llp_certsyncallowed]
            , [llp_certsyncdbname]
            , [llp_defaultopportunitytype]
            , [llp_idnetsuite]
            , [llp_sfinsuranceid]
            , [llp_sfinsuranceid_entitytype]
            , [llp_sfinsuranceidname]
            , [llp_sfinsuranceidyominame]
            , [llp_sfsalespersonid]
            , [llp_sfsalespersonid_entitytype]
            , [llp_sfsalespersonidname]
            , [llp_sfsalespersonidyominame]
            , [llp_sportlanguage]
            , [llp_sportsellergroup]
            , [llp_sportsellerorganization]
            , [llp_utsalespersonid]
            , [llp_utsalespersonid_entitytype]
            , [llp_utsalespersonidname]
            , [llp_utsalespersonidyominame]
            , [llp_xdslogin]
            , [middlename]
            , [mobilealertemail]
            , [mobileofflineprofileid]
            , [mobileofflineprofileid_entitytype]
            , [mobileofflineprofileidname]
            , [mobilephone]
            , [modifiedby]
            , [modifiedby_entitytype]
            , [modifiedbyname]
            , [modifiedbyyominame]
            , [modifiedon]
            , [modifiedonbehalfby]
            , [modifiedonbehalfby_entitytype]
            , [modifiedonbehalfbyname]
            , [modifiedonbehalfbyyominame]
            , [msdyn_gdproptout]
            , [nickname]
            , [organizationid]
            , [organizationidname]
            , [outgoingemaildeliverymethod]
            , [overriddencreatedon]
            , [parentsystemuserid]
            , [parentsystemuserid_entitytype]
            , [parentsystemuseridname]
            , [parentsystemuseridyominame]
            , [passporthi]
            , [passportlo]
            , [personalemailaddress]
            , [photourl]
            , [positionid]
            , [positionid_entitytype]
            , [positionidname]
            , [preferredaddresscode]
            , [preferredemailcode]
            , [preferredphonecode]
            , [processid]
            , [queueid]
            , [queueid_entitytype]
            , [queueidname]
            , [salutation]
            , [setupuser]
            , [sharepointemailaddress]
            , [SinkCreatedOn]
            , [SinkModifiedOn]
            , [siteid]
            , [siteid_entitytype]
            , [siteidname]
            , [skills]
            , [stageid]
            , [systemuserid]
            , [territoryid]
            , [territoryid_entitytype]
            , [territoryidname]
            , [timezoneruleversionnumber]
            , [title]
            , [transactioncurrencyid]
            , [transactioncurrencyid_entitytype]
            , [transactioncurrencyidname]
            , [traversedpath]
            , [userlicensetype]
            , [userpuid]
            , [utcconversiontimezonecode]
            , [versionnumber]
            , [windowsliveid]
            , [yammeremailaddress]
            , [yammeruserid]
            , [yomifirstname]
            , [yomifullname]
            , [yomilastname]
            , [yomimiddlename]
            , [DataSourceId]
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
            
    ) 
    OUTPUT Inserted.ThreadLogDeleteId INTO @DeleteRowCounts
    SELECT
            v.[Id]
            , v.[accessmode]
            , v.[activedirectoryguid]
            , v.[address1_addressid]
            , v.[address1_addresstypecode]
            , v.[address1_city]
            , v.[address1_composite]
            , v.[address1_country]
            , v.[address1_county]
            , v.[address1_fax]
            , v.[address1_latitude]
            , v.[address1_line1]
            , v.[address1_line2]
            , v.[address1_line3]
            , v.[address1_longitude]
            , v.[address1_name]
            , v.[address1_postalcode]
            , v.[address1_postofficebox]
            , v.[address1_shippingmethodcode]
            , v.[address1_stateorprovince]
            , v.[address1_telephone1]
            , v.[address1_telephone2]
            , v.[address1_telephone3]
            , v.[address1_upszone]
            , v.[address1_utcoffset]
            , v.[address2_addressid]
            , v.[address2_addresstypecode]
            , v.[address2_city]
            , v.[address2_composite]
            , v.[address2_country]
            , v.[address2_county]
            , v.[address2_fax]
            , v.[address2_latitude]
            , v.[address2_line1]
            , v.[address2_line2]
            , v.[address2_line3]
            , v.[address2_longitude]
            , v.[address2_name]
            , v.[address2_postalcode]
            , v.[address2_postofficebox]
            , v.[address2_shippingmethodcode]
            , v.[address2_stateorprovince]
            , v.[address2_telephone1]
            , v.[address2_telephone2]
            , v.[address2_telephone3]
            , v.[address2_upszone]
            , v.[address2_utcoffset]
            , v.[applicationid]
            , v.[applicationiduri]
            , v.[azureactivedirectoryobjectid]
            , v.[businessunitid]
            , v.[businessunitid_entitytype]
            , v.[businessunitidname]
            , v.[calendarid]
            , v.[calendarid_entitytype]
            , v.[caltype]
            , v.[createdby]
            , v.[createdby_entitytype]
            , v.[createdbyname]
            , v.[createdbyyominame]
            , v.[createdon]
            , v.[createdonbehalfby]
            , v.[createdonbehalfby_entitytype]
            , v.[createdonbehalfbyname]
            , v.[createdonbehalfbyyominame]
            , v.[defaultfilterspopulated]
            , v.[defaultmailbox]
            , v.[defaultmailbox_entitytype]
            , v.[defaultmailboxname]
            , v.[defaultodbfoldername]
            , v.[disabledreason]
            , v.[displayinserviceviews]
            , v.[domainname]
            , v.[emailrouteraccessapproval]
            , v.[employeeid]
            , v.[entityimage_timestamp]
            , v.[entityimage_url]
            , v.[entityimageid]
            , v.[exchangerate]
            , v.[firstname]
            , v.[fullname]
            , v.[governmentid]
            , v.[homephone]
            , v.[identityid]
            , v.[importsequencenumber]
            , v.[incomingemaildeliverymethod]
            , v.[internalemailaddress]
            , v.[invitestatuscode]
            , v.[isactivedirectoryuser]
            , v.[isdisabled]
            , v.[isemailaddressapprovedbyo365admin]
            , v.[isintegrationuser]
            , v.[islicensed]
            , v.[issyncwithdirectory]
            , v.[jobtitle]
            , v.[lastname]
            , v.[latestupdatetime]
            , v.[llp_arbesdbname]
            , v.[llp_arbessyncallowed]
            , v.[llp_automastersyncallowed]
            , v.[llp_automastersyncdbname]
            , v.[llp_automaticallysendtoautomaster]
            , v.[llp_certsyncallowed]
            , v.[llp_certsyncdbname]
            , v.[llp_defaultopportunitytype]
            , v.[llp_idnetsuite]
            , v.[llp_sfinsuranceid]
            , v.[llp_sfinsuranceid_entitytype]
            , v.[llp_sfinsuranceidname]
            , v.[llp_sfinsuranceidyominame]
            , v.[llp_sfsalespersonid]
            , v.[llp_sfsalespersonid_entitytype]
            , v.[llp_sfsalespersonidname]
            , v.[llp_sfsalespersonidyominame]
            , v.[llp_sportlanguage]
            , v.[llp_sportsellergroup]
            , v.[llp_sportsellerorganization]
            , v.[llp_utsalespersonid]
            , v.[llp_utsalespersonid_entitytype]
            , v.[llp_utsalespersonidname]
            , v.[llp_utsalespersonidyominame]
            , v.[llp_xdslogin]
            , v.[middlename]
            , v.[mobilealertemail]
            , v.[mobileofflineprofileid]
            , v.[mobileofflineprofileid_entitytype]
            , v.[mobileofflineprofileidname]
            , v.[mobilephone]
            , v.[modifiedby]
            , v.[modifiedby_entitytype]
            , v.[modifiedbyname]
            , v.[modifiedbyyominame]
            , v.[modifiedon]
            , v.[modifiedonbehalfby]
            , v.[modifiedonbehalfby_entitytype]
            , v.[modifiedonbehalfbyname]
            , v.[modifiedonbehalfbyyominame]
            , v.[msdyn_gdproptout]
            , v.[nickname]
            , v.[organizationid]
            , v.[organizationidname]
            , v.[outgoingemaildeliverymethod]
            , v.[overriddencreatedon]
            , v.[parentsystemuserid]
            , v.[parentsystemuserid_entitytype]
            , v.[parentsystemuseridname]
            , v.[parentsystemuseridyominame]
            , v.[passporthi]
            , v.[passportlo]
            , v.[personalemailaddress]
            , v.[photourl]
            , v.[positionid]
            , v.[positionid_entitytype]
            , v.[positionidname]
            , v.[preferredaddresscode]
            , v.[preferredemailcode]
            , v.[preferredphonecode]
            , v.[processid]
            , v.[queueid]
            , v.[queueid_entitytype]
            , v.[queueidname]
            , v.[salutation]
            , v.[setupuser]
            , v.[sharepointemailaddress]
            , v.[SinkCreatedOn]
            , v.[SinkModifiedOn]
            , v.[siteid]
            , v.[siteid_entitytype]
            , v.[siteidname]
            , v.[skills]
            , v.[stageid]
            , v.[systemuserid]
            , v.[territoryid]
            , v.[territoryid_entitytype]
            , v.[territoryidname]
            , v.[timezoneruleversionnumber]
            , v.[title]
            , v.[transactioncurrencyid]
            , v.[transactioncurrencyid_entitytype]
            , v.[transactioncurrencyidname]
            , v.[traversedpath]
            , v.[userlicensetype]
            , v.[userpuid]
            , v.[utcconversiontimezonecode]
            , v.[versionnumber]
            , v.[windowsliveid]
            , v.[yammeremailaddress]
            , v.[yammeruserid]
            , v.[yomifirstname]
            , v.[yomifullname]
            , v.[yomilastname]
            , v.[yomimiddlename]
            , v.[DataSourceId]
            , @ThreadLogId
            , -1
            , -1
            , N'D' -- update
    FROM Vault.CRMdboSystemuser AS v
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
                , TableFinalRowCount = (SELECT COUNT(*) FROM [Vault].[CRMdboSystemuser] WITH (NOLOCK))
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
