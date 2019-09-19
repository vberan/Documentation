Stored Procedure Vault.uspLoadCRMdboBusinessunit {#spVaultuspLoadCRMdboBusinessunit}
------------------------------------------------

Definition of Stored procedure:

``` {.sql}
CREATE PROCEDURE [Vault].[uspLoadCRMdboBusinessunit] 
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
            SET TableInitialRowCount = (SELECT COUNT(*) FROM [Vault].[CRMdboBusinessunit] WITH (NOLOCK))
        WHERE ThreadLogId = @ThreadLogId;

            BEGIN TRANSACTION;

    
        MERGE INTO [Vault].[CRMdboBusinessunit] AS v
        USING [Stage].[CRMdboBusinessunit] AS s
            ON ( s.[Id] = v.[Id]AND s.[DataSourceId] = v.[DataSourceId]
     AND v.[ThreadLogDeleteId] = -1 AND v.[ThreadLogUpdateId] = -1 AND v.[ChangeOperation] <> N'D'
    )

        WHEN MATCHED AND
            (
            v.[address1_addressid] <> s.[address1_addressid]
            OR (v.[address1_addressid] IS NULL AND s.[address1_addressid] IS NOT NULL)
        OR (v.[address1_addressid] IS NOT NULL AND s.[address1_addressid] IS NULL)
        OR v.[address1_addresstypecode] <> s.[address1_addresstypecode]
            OR (v.[address1_addresstypecode] IS NULL AND s.[address1_addresstypecode] IS NOT NULL)
        OR (v.[address1_addresstypecode] IS NOT NULL AND s.[address1_addresstypecode] IS NULL)
        OR v.[address1_city] <> s.[address1_city]
            OR (v.[address1_city] IS NULL AND s.[address1_city] IS NOT NULL)
        OR (v.[address1_city] IS NOT NULL AND s.[address1_city] IS NULL)
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
        OR v.[businessunitid] <> s.[businessunitid]
            OR (v.[businessunitid] IS NULL AND s.[businessunitid] IS NOT NULL)
        OR (v.[businessunitid] IS NOT NULL AND s.[businessunitid] IS NULL)
        OR v.[calendarid] <> s.[calendarid]
            OR (v.[calendarid] IS NULL AND s.[calendarid] IS NOT NULL)
        OR (v.[calendarid] IS NOT NULL AND s.[calendarid] IS NULL)
        OR v.[calendarid_entitytype] <> s.[calendarid_entitytype]
            OR (v.[calendarid_entitytype] IS NULL AND s.[calendarid_entitytype] IS NOT NULL)
        OR (v.[calendarid_entitytype] IS NOT NULL AND s.[calendarid_entitytype] IS NULL)
        OR v.[costcenter] <> s.[costcenter]
            OR (v.[costcenter] IS NULL AND s.[costcenter] IS NOT NULL)
        OR (v.[costcenter] IS NOT NULL AND s.[costcenter] IS NULL)
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
        OR v.[creditlimit] <> s.[creditlimit]
            OR (v.[creditlimit] IS NULL AND s.[creditlimit] IS NOT NULL)
        OR (v.[creditlimit] IS NOT NULL AND s.[creditlimit] IS NULL)
        OR v.[description] <> s.[description]
            OR (v.[description] IS NULL AND s.[description] IS NOT NULL)
        OR (v.[description] IS NOT NULL AND s.[description] IS NULL)
        OR v.[disabledreason] <> s.[disabledreason]
            OR (v.[disabledreason] IS NULL AND s.[disabledreason] IS NOT NULL)
        OR (v.[disabledreason] IS NOT NULL AND s.[disabledreason] IS NULL)
        OR v.[divisionname] <> s.[divisionname]
            OR (v.[divisionname] IS NULL AND s.[divisionname] IS NOT NULL)
        OR (v.[divisionname] IS NOT NULL AND s.[divisionname] IS NULL)
        OR v.[emailaddress] <> s.[emailaddress]
            OR (v.[emailaddress] IS NULL AND s.[emailaddress] IS NOT NULL)
        OR (v.[emailaddress] IS NOT NULL AND s.[emailaddress] IS NULL)
        OR v.[exchangerate] <> s.[exchangerate]
            OR (v.[exchangerate] IS NULL AND s.[exchangerate] IS NOT NULL)
        OR (v.[exchangerate] IS NOT NULL AND s.[exchangerate] IS NULL)
        OR v.[fileasname] <> s.[fileasname]
            OR (v.[fileasname] IS NULL AND s.[fileasname] IS NOT NULL)
        OR (v.[fileasname] IS NOT NULL AND s.[fileasname] IS NULL)
        OR v.[ftpsiteurl] <> s.[ftpsiteurl]
            OR (v.[ftpsiteurl] IS NULL AND s.[ftpsiteurl] IS NOT NULL)
        OR (v.[ftpsiteurl] IS NOT NULL AND s.[ftpsiteurl] IS NULL)
        OR v.[importsequencenumber] <> s.[importsequencenumber]
            OR (v.[importsequencenumber] IS NULL AND s.[importsequencenumber] IS NOT NULL)
        OR (v.[importsequencenumber] IS NOT NULL AND s.[importsequencenumber] IS NULL)
        OR v.[inheritancemask] <> s.[inheritancemask]
            OR (v.[inheritancemask] IS NULL AND s.[inheritancemask] IS NOT NULL)
        OR (v.[inheritancemask] IS NOT NULL AND s.[inheritancemask] IS NULL)
        OR v.[isdisabled] <> s.[isdisabled]
            OR (v.[isdisabled] IS NULL AND s.[isdisabled] IS NOT NULL)
        OR (v.[isdisabled] IS NOT NULL AND s.[isdisabled] IS NULL)
        OR v.[llp_countryid] <> s.[llp_countryid]
            OR (v.[llp_countryid] IS NULL AND s.[llp_countryid] IS NOT NULL)
        OR (v.[llp_countryid] IS NOT NULL AND s.[llp_countryid] IS NULL)
        OR v.[llp_countryid_entitytype] <> s.[llp_countryid_entitytype]
            OR (v.[llp_countryid_entitytype] IS NULL AND s.[llp_countryid_entitytype] IS NOT NULL)
        OR (v.[llp_countryid_entitytype] IS NOT NULL AND s.[llp_countryid_entitytype] IS NULL)
        OR v.[llp_countryidname] <> s.[llp_countryidname]
            OR (v.[llp_countryidname] IS NULL AND s.[llp_countryidname] IS NOT NULL)
        OR (v.[llp_countryidname] IS NOT NULL AND s.[llp_countryidname] IS NULL)
        OR v.[llp_iddealernr] <> s.[llp_iddealernr]
            OR (v.[llp_iddealernr] IS NULL AND s.[llp_iddealernr] IS NOT NULL)
        OR (v.[llp_iddealernr] IS NOT NULL AND s.[llp_iddealernr] IS NULL)
        OR v.[llp_idnetsuite] <> s.[llp_idnetsuite]
            OR (v.[llp_idnetsuite] IS NULL AND s.[llp_idnetsuite] IS NOT NULL)
        OR (v.[llp_idnetsuite] IS NOT NULL AND s.[llp_idnetsuite] IS NULL)
        OR v.[llp_isworkshop] <> s.[llp_isworkshop]
            OR (v.[llp_isworkshop] IS NULL AND s.[llp_isworkshop] IS NOT NULL)
        OR (v.[llp_isworkshop] IS NOT NULL AND s.[llp_isworkshop] IS NULL)
        OR v.[llp_teamid] <> s.[llp_teamid]
            OR (v.[llp_teamid] IS NULL AND s.[llp_teamid] IS NOT NULL)
        OR (v.[llp_teamid] IS NOT NULL AND s.[llp_teamid] IS NULL)
        OR v.[llp_teamid_entitytype] <> s.[llp_teamid_entitytype]
            OR (v.[llp_teamid_entitytype] IS NULL AND s.[llp_teamid_entitytype] IS NOT NULL)
        OR (v.[llp_teamid_entitytype] IS NOT NULL AND s.[llp_teamid_entitytype] IS NULL)
        OR v.[llp_teamidname] <> s.[llp_teamidname]
            OR (v.[llp_teamidname] IS NULL AND s.[llp_teamidname] IS NOT NULL)
        OR (v.[llp_teamidname] IS NOT NULL AND s.[llp_teamidname] IS NULL)
        OR v.[llp_teamidyominame] <> s.[llp_teamidyominame]
            OR (v.[llp_teamidyominame] IS NULL AND s.[llp_teamidyominame] IS NOT NULL)
        OR (v.[llp_teamidyominame] IS NOT NULL AND s.[llp_teamidyominame] IS NULL)
        OR v.[llp_utapprovaltemplateid] <> s.[llp_utapprovaltemplateid]
            OR (v.[llp_utapprovaltemplateid] IS NULL AND s.[llp_utapprovaltemplateid] IS NOT NULL)
        OR (v.[llp_utapprovaltemplateid] IS NOT NULL AND s.[llp_utapprovaltemplateid] IS NULL)
        OR v.[llp_utapprovaltemplateid_entitytype] <> s.[llp_utapprovaltemplateid_entitytype]
            OR (v.[llp_utapprovaltemplateid_entitytype] IS NULL AND s.[llp_utapprovaltemplateid_entitytype] IS NOT NULL)
        OR (v.[llp_utapprovaltemplateid_entitytype] IS NOT NULL AND s.[llp_utapprovaltemplateid_entitytype] IS NULL)
        OR v.[llp_utapprovaltemplateidname] <> s.[llp_utapprovaltemplateidname]
            OR (v.[llp_utapprovaltemplateidname] IS NULL AND s.[llp_utapprovaltemplateidname] IS NOT NULL)
        OR (v.[llp_utapprovaltemplateidname] IS NOT NULL AND s.[llp_utapprovaltemplateidname] IS NULL)
        OR v.[llp_utreservationapproverid] <> s.[llp_utreservationapproverid]
            OR (v.[llp_utreservationapproverid] IS NULL AND s.[llp_utreservationapproverid] IS NOT NULL)
        OR (v.[llp_utreservationapproverid] IS NOT NULL AND s.[llp_utreservationapproverid] IS NULL)
        OR v.[llp_utreservationapproverid_entitytype] <> s.[llp_utreservationapproverid_entitytype]
            OR (v.[llp_utreservationapproverid_entitytype] IS NULL AND s.[llp_utreservationapproverid_entitytype] IS NOT NULL)
        OR (v.[llp_utreservationapproverid_entitytype] IS NOT NULL AND s.[llp_utreservationapproverid_entitytype] IS NULL)
        OR v.[llp_utreservationapproveridname] <> s.[llp_utreservationapproveridname]
            OR (v.[llp_utreservationapproveridname] IS NULL AND s.[llp_utreservationapproveridname] IS NOT NULL)
        OR (v.[llp_utreservationapproveridname] IS NOT NULL AND s.[llp_utreservationapproveridname] IS NULL)
        OR v.[llp_utreservationapproveridyominame] <> s.[llp_utreservationapproveridyominame]
            OR (v.[llp_utreservationapproveridyominame] IS NULL AND s.[llp_utreservationapproveridyominame] IS NOT NULL)
        OR (v.[llp_utreservationapproveridyominame] IS NOT NULL AND s.[llp_utreservationapproveridyominame] IS NULL)
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
        OR v.[name] <> s.[name]
            OR (v.[name] IS NULL AND s.[name] IS NOT NULL)
        OR (v.[name] IS NOT NULL AND s.[name] IS NULL)
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
        OR v.[parentbusinessunitid] <> s.[parentbusinessunitid]
            OR (v.[parentbusinessunitid] IS NULL AND s.[parentbusinessunitid] IS NOT NULL)
        OR (v.[parentbusinessunitid] IS NOT NULL AND s.[parentbusinessunitid] IS NULL)
        OR v.[parentbusinessunitid_entitytype] <> s.[parentbusinessunitid_entitytype]
            OR (v.[parentbusinessunitid_entitytype] IS NULL AND s.[parentbusinessunitid_entitytype] IS NOT NULL)
        OR (v.[parentbusinessunitid_entitytype] IS NOT NULL AND s.[parentbusinessunitid_entitytype] IS NULL)
        OR v.[parentbusinessunitidname] <> s.[parentbusinessunitidname]
            OR (v.[parentbusinessunitidname] IS NULL AND s.[parentbusinessunitidname] IS NOT NULL)
        OR (v.[parentbusinessunitidname] IS NOT NULL AND s.[parentbusinessunitidname] IS NULL)
        OR v.[picture] <> s.[picture]
            OR (v.[picture] IS NULL AND s.[picture] IS NOT NULL)
        OR (v.[picture] IS NOT NULL AND s.[picture] IS NULL)
        OR v.[SinkCreatedOn] <> s.[SinkCreatedOn]
            OR (v.[SinkCreatedOn] IS NULL AND s.[SinkCreatedOn] IS NOT NULL)
        OR (v.[SinkCreatedOn] IS NOT NULL AND s.[SinkCreatedOn] IS NULL)
        OR v.[SinkModifiedOn] <> s.[SinkModifiedOn]
            OR (v.[SinkModifiedOn] IS NULL AND s.[SinkModifiedOn] IS NOT NULL)
        OR (v.[SinkModifiedOn] IS NOT NULL AND s.[SinkModifiedOn] IS NULL)
        OR v.[stockexchange] <> s.[stockexchange]
            OR (v.[stockexchange] IS NULL AND s.[stockexchange] IS NOT NULL)
        OR (v.[stockexchange] IS NOT NULL AND s.[stockexchange] IS NULL)
        OR v.[tickersymbol] <> s.[tickersymbol]
            OR (v.[tickersymbol] IS NULL AND s.[tickersymbol] IS NOT NULL)
        OR (v.[tickersymbol] IS NOT NULL AND s.[tickersymbol] IS NULL)
        OR v.[transactioncurrencyid] <> s.[transactioncurrencyid]
            OR (v.[transactioncurrencyid] IS NULL AND s.[transactioncurrencyid] IS NOT NULL)
        OR (v.[transactioncurrencyid] IS NOT NULL AND s.[transactioncurrencyid] IS NULL)
        OR v.[transactioncurrencyid_entitytype] <> s.[transactioncurrencyid_entitytype]
            OR (v.[transactioncurrencyid_entitytype] IS NULL AND s.[transactioncurrencyid_entitytype] IS NOT NULL)
        OR (v.[transactioncurrencyid_entitytype] IS NOT NULL AND s.[transactioncurrencyid_entitytype] IS NULL)
        OR v.[transactioncurrencyidname] <> s.[transactioncurrencyidname]
            OR (v.[transactioncurrencyidname] IS NULL AND s.[transactioncurrencyidname] IS NOT NULL)
        OR (v.[transactioncurrencyidname] IS NOT NULL AND s.[transactioncurrencyidname] IS NULL)
        OR v.[usergroupid] <> s.[usergroupid]
            OR (v.[usergroupid] IS NULL AND s.[usergroupid] IS NOT NULL)
        OR (v.[usergroupid] IS NOT NULL AND s.[usergroupid] IS NULL)
        OR v.[utcoffset] <> s.[utcoffset]
            OR (v.[utcoffset] IS NULL AND s.[utcoffset] IS NOT NULL)
        OR (v.[utcoffset] IS NOT NULL AND s.[utcoffset] IS NULL)
        OR v.[versionnumber] <> s.[versionnumber]
            OR (v.[versionnumber] IS NULL AND s.[versionnumber] IS NOT NULL)
        OR (v.[versionnumber] IS NOT NULL AND s.[versionnumber] IS NULL)
        OR v.[websiteurl] <> s.[websiteurl]
            OR (v.[websiteurl] IS NULL AND s.[websiteurl] IS NOT NULL)
        OR (v.[websiteurl] IS NOT NULL AND s.[websiteurl] IS NULL)
        OR v.[workflowsuspended] <> s.[workflowsuspended]
            OR (v.[workflowsuspended] IS NULL AND s.[workflowsuspended] IS NOT NULL)
        OR (v.[workflowsuspended] IS NOT NULL AND s.[workflowsuspended] IS NULL)
        )
        THEN 
            UPDATE SET
                [ThreadLogUpdateId] = @ThreadLogId
            

                
        WHEN NOT MATCHED BY TARGET 
            THEN INSERT
            ( 
            [Id]
            , [address1_addressid]
            , [address1_addresstypecode]
            , [address1_city]
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
            , [businessunitid]
            , [calendarid]
            , [calendarid_entitytype]
            , [costcenter]
            , [createdby]
            , [createdby_entitytype]
            , [createdbyname]
            , [createdbyyominame]
            , [createdon]
            , [createdonbehalfby]
            , [createdonbehalfby_entitytype]
            , [createdonbehalfbyname]
            , [createdonbehalfbyyominame]
            , [creditlimit]
            , [description]
            , [disabledreason]
            , [divisionname]
            , [emailaddress]
            , [exchangerate]
            , [fileasname]
            , [ftpsiteurl]
            , [importsequencenumber]
            , [inheritancemask]
            , [isdisabled]
            , [llp_countryid]
            , [llp_countryid_entitytype]
            , [llp_countryidname]
            , [llp_iddealernr]
            , [llp_idnetsuite]
            , [llp_isworkshop]
            , [llp_teamid]
            , [llp_teamid_entitytype]
            , [llp_teamidname]
            , [llp_teamidyominame]
            , [llp_utapprovaltemplateid]
            , [llp_utapprovaltemplateid_entitytype]
            , [llp_utapprovaltemplateidname]
            , [llp_utreservationapproverid]
            , [llp_utreservationapproverid_entitytype]
            , [llp_utreservationapproveridname]
            , [llp_utreservationapproveridyominame]
            , [modifiedby]
            , [modifiedby_entitytype]
            , [modifiedbyname]
            , [modifiedbyyominame]
            , [modifiedon]
            , [modifiedonbehalfby]
            , [modifiedonbehalfby_entitytype]
            , [modifiedonbehalfbyname]
            , [modifiedonbehalfbyyominame]
            , [name]
            , [organizationid]
            , [organizationid_entitytype]
            , [organizationidname]
            , [overriddencreatedon]
            , [parentbusinessunitid]
            , [parentbusinessunitid_entitytype]
            , [parentbusinessunitidname]
            , [picture]
            , [SinkCreatedOn]
            , [SinkModifiedOn]
            , [stockexchange]
            , [tickersymbol]
            , [transactioncurrencyid]
            , [transactioncurrencyid_entitytype]
            , [transactioncurrencyidname]
            , [usergroupid]
            , [utcoffset]
            , [versionnumber]
            , [websiteurl]
            , [workflowsuspended]
            , [DataSourceId]
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
            
    ) VALUES (
            s.[Id]
            , s.[address1_addressid]
            , s.[address1_addresstypecode]
            , s.[address1_city]
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
            , s.[businessunitid]
            , s.[calendarid]
            , s.[calendarid_entitytype]
            , s.[costcenter]
            , s.[createdby]
            , s.[createdby_entitytype]
            , s.[createdbyname]
            , s.[createdbyyominame]
            , s.[createdon]
            , s.[createdonbehalfby]
            , s.[createdonbehalfby_entitytype]
            , s.[createdonbehalfbyname]
            , s.[createdonbehalfbyyominame]
            , s.[creditlimit]
            , s.[description]
            , s.[disabledreason]
            , s.[divisionname]
            , s.[emailaddress]
            , s.[exchangerate]
            , s.[fileasname]
            , s.[ftpsiteurl]
            , s.[importsequencenumber]
            , s.[inheritancemask]
            , s.[isdisabled]
            , s.[llp_countryid]
            , s.[llp_countryid_entitytype]
            , s.[llp_countryidname]
            , s.[llp_iddealernr]
            , s.[llp_idnetsuite]
            , s.[llp_isworkshop]
            , s.[llp_teamid]
            , s.[llp_teamid_entitytype]
            , s.[llp_teamidname]
            , s.[llp_teamidyominame]
            , s.[llp_utapprovaltemplateid]
            , s.[llp_utapprovaltemplateid_entitytype]
            , s.[llp_utapprovaltemplateidname]
            , s.[llp_utreservationapproverid]
            , s.[llp_utreservationapproverid_entitytype]
            , s.[llp_utreservationapproveridname]
            , s.[llp_utreservationapproveridyominame]
            , s.[modifiedby]
            , s.[modifiedby_entitytype]
            , s.[modifiedbyname]
            , s.[modifiedbyyominame]
            , s.[modifiedon]
            , s.[modifiedonbehalfby]
            , s.[modifiedonbehalfby_entitytype]
            , s.[modifiedonbehalfbyname]
            , s.[modifiedonbehalfbyyominame]
            , s.[name]
            , s.[organizationid]
            , s.[organizationid_entitytype]
            , s.[organizationidname]
            , s.[overriddencreatedon]
            , s.[parentbusinessunitid]
            , s.[parentbusinessunitid_entitytype]
            , s.[parentbusinessunitidname]
            , s.[picture]
            , s.[SinkCreatedOn]
            , s.[SinkModifiedOn]
            , s.[stockexchange]
            , s.[tickersymbol]
            , s.[transactioncurrencyid]
            , s.[transactioncurrencyid_entitytype]
            , s.[transactioncurrencyidname]
            , s.[usergroupid]
            , s.[utcoffset]
            , s.[versionnumber]
            , s.[websiteurl]
            , s.[workflowsuspended]
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
    
    INSERT INTO [Vault].[CRMdboBusinessunit] (
            [Id]
            , [address1_addressid]
            , [address1_addresstypecode]
            , [address1_city]
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
            , [businessunitid]
            , [calendarid]
            , [calendarid_entitytype]
            , [costcenter]
            , [createdby]
            , [createdby_entitytype]
            , [createdbyname]
            , [createdbyyominame]
            , [createdon]
            , [createdonbehalfby]
            , [createdonbehalfby_entitytype]
            , [createdonbehalfbyname]
            , [createdonbehalfbyyominame]
            , [creditlimit]
            , [description]
            , [disabledreason]
            , [divisionname]
            , [emailaddress]
            , [exchangerate]
            , [fileasname]
            , [ftpsiteurl]
            , [importsequencenumber]
            , [inheritancemask]
            , [isdisabled]
            , [llp_countryid]
            , [llp_countryid_entitytype]
            , [llp_countryidname]
            , [llp_iddealernr]
            , [llp_idnetsuite]
            , [llp_isworkshop]
            , [llp_teamid]
            , [llp_teamid_entitytype]
            , [llp_teamidname]
            , [llp_teamidyominame]
            , [llp_utapprovaltemplateid]
            , [llp_utapprovaltemplateid_entitytype]
            , [llp_utapprovaltemplateidname]
            , [llp_utreservationapproverid]
            , [llp_utreservationapproverid_entitytype]
            , [llp_utreservationapproveridname]
            , [llp_utreservationapproveridyominame]
            , [modifiedby]
            , [modifiedby_entitytype]
            , [modifiedbyname]
            , [modifiedbyyominame]
            , [modifiedon]
            , [modifiedonbehalfby]
            , [modifiedonbehalfby_entitytype]
            , [modifiedonbehalfbyname]
            , [modifiedonbehalfbyyominame]
            , [name]
            , [organizationid]
            , [organizationid_entitytype]
            , [organizationidname]
            , [overriddencreatedon]
            , [parentbusinessunitid]
            , [parentbusinessunitid_entitytype]
            , [parentbusinessunitidname]
            , [picture]
            , [SinkCreatedOn]
            , [SinkModifiedOn]
            , [stockexchange]
            , [tickersymbol]
            , [transactioncurrencyid]
            , [transactioncurrencyid_entitytype]
            , [transactioncurrencyidname]
            , [usergroupid]
            , [utcoffset]
            , [versionnumber]
            , [websiteurl]
            , [workflowsuspended]
            , [DataSourceId]
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
        
    ) 
    OUTPUT Inserted.ThreadLogUpdateId INTO @UpdateRowCounts
    SELECT

            s.[Id]
            , s.[address1_addressid]
            , s.[address1_addresstypecode]
            , s.[address1_city]
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
            , s.[businessunitid]
            , s.[calendarid]
            , s.[calendarid_entitytype]
            , s.[costcenter]
            , s.[createdby]
            , s.[createdby_entitytype]
            , s.[createdbyname]
            , s.[createdbyyominame]
            , s.[createdon]
            , s.[createdonbehalfby]
            , s.[createdonbehalfby_entitytype]
            , s.[createdonbehalfbyname]
            , s.[createdonbehalfbyyominame]
            , s.[creditlimit]
            , s.[description]
            , s.[disabledreason]
            , s.[divisionname]
            , s.[emailaddress]
            , s.[exchangerate]
            , s.[fileasname]
            , s.[ftpsiteurl]
            , s.[importsequencenumber]
            , s.[inheritancemask]
            , s.[isdisabled]
            , s.[llp_countryid]
            , s.[llp_countryid_entitytype]
            , s.[llp_countryidname]
            , s.[llp_iddealernr]
            , s.[llp_idnetsuite]
            , s.[llp_isworkshop]
            , s.[llp_teamid]
            , s.[llp_teamid_entitytype]
            , s.[llp_teamidname]
            , s.[llp_teamidyominame]
            , s.[llp_utapprovaltemplateid]
            , s.[llp_utapprovaltemplateid_entitytype]
            , s.[llp_utapprovaltemplateidname]
            , s.[llp_utreservationapproverid]
            , s.[llp_utreservationapproverid_entitytype]
            , s.[llp_utreservationapproveridname]
            , s.[llp_utreservationapproveridyominame]
            , s.[modifiedby]
            , s.[modifiedby_entitytype]
            , s.[modifiedbyname]
            , s.[modifiedbyyominame]
            , s.[modifiedon]
            , s.[modifiedonbehalfby]
            , s.[modifiedonbehalfby_entitytype]
            , s.[modifiedonbehalfbyname]
            , s.[modifiedonbehalfbyyominame]
            , s.[name]
            , s.[organizationid]
            , s.[organizationid_entitytype]
            , s.[organizationidname]
            , s.[overriddencreatedon]
            , s.[parentbusinessunitid]
            , s.[parentbusinessunitid_entitytype]
            , s.[parentbusinessunitidname]
            , s.[picture]
            , s.[SinkCreatedOn]
            , s.[SinkModifiedOn]
            , s.[stockexchange]
            , s.[tickersymbol]
            , s.[transactioncurrencyid]
            , s.[transactioncurrencyid_entitytype]
            , s.[transactioncurrencyidname]
            , s.[usergroupid]
            , s.[utcoffset]
            , s.[versionnumber]
            , s.[websiteurl]
            , s.[workflowsuspended]
            , s.[DataSourceId]
            , @ThreadLogId
            , -1
            , -1
            , N'U' -- update
    FROM Stage.CRMdboBusinessunit AS s
    INNER JOIN Vault.CRMdboBusinessunit AS v
        ON  s.[Id] = v.[Id] AND v.ThreadLogUpdateId = @ThreadLogId
    
    INSERT INTO [Vault].[CRMdboBusinessunit] (
            [Id]
            , [address1_addressid]
            , [address1_addresstypecode]
            , [address1_city]
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
            , [businessunitid]
            , [calendarid]
            , [calendarid_entitytype]
            , [costcenter]
            , [createdby]
            , [createdby_entitytype]
            , [createdbyname]
            , [createdbyyominame]
            , [createdon]
            , [createdonbehalfby]
            , [createdonbehalfby_entitytype]
            , [createdonbehalfbyname]
            , [createdonbehalfbyyominame]
            , [creditlimit]
            , [description]
            , [disabledreason]
            , [divisionname]
            , [emailaddress]
            , [exchangerate]
            , [fileasname]
            , [ftpsiteurl]
            , [importsequencenumber]
            , [inheritancemask]
            , [isdisabled]
            , [llp_countryid]
            , [llp_countryid_entitytype]
            , [llp_countryidname]
            , [llp_iddealernr]
            , [llp_idnetsuite]
            , [llp_isworkshop]
            , [llp_teamid]
            , [llp_teamid_entitytype]
            , [llp_teamidname]
            , [llp_teamidyominame]
            , [llp_utapprovaltemplateid]
            , [llp_utapprovaltemplateid_entitytype]
            , [llp_utapprovaltemplateidname]
            , [llp_utreservationapproverid]
            , [llp_utreservationapproverid_entitytype]
            , [llp_utreservationapproveridname]
            , [llp_utreservationapproveridyominame]
            , [modifiedby]
            , [modifiedby_entitytype]
            , [modifiedbyname]
            , [modifiedbyyominame]
            , [modifiedon]
            , [modifiedonbehalfby]
            , [modifiedonbehalfby_entitytype]
            , [modifiedonbehalfbyname]
            , [modifiedonbehalfbyyominame]
            , [name]
            , [organizationid]
            , [organizationid_entitytype]
            , [organizationidname]
            , [overriddencreatedon]
            , [parentbusinessunitid]
            , [parentbusinessunitid_entitytype]
            , [parentbusinessunitidname]
            , [picture]
            , [SinkCreatedOn]
            , [SinkModifiedOn]
            , [stockexchange]
            , [tickersymbol]
            , [transactioncurrencyid]
            , [transactioncurrencyid_entitytype]
            , [transactioncurrencyidname]
            , [usergroupid]
            , [utcoffset]
            , [versionnumber]
            , [websiteurl]
            , [workflowsuspended]
            , [DataSourceId]
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
            
    ) 
    OUTPUT Inserted.ThreadLogDeleteId INTO @DeleteRowCounts
    SELECT
            v.[Id]
            , v.[address1_addressid]
            , v.[address1_addresstypecode]
            , v.[address1_city]
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
            , v.[businessunitid]
            , v.[calendarid]
            , v.[calendarid_entitytype]
            , v.[costcenter]
            , v.[createdby]
            , v.[createdby_entitytype]
            , v.[createdbyname]
            , v.[createdbyyominame]
            , v.[createdon]
            , v.[createdonbehalfby]
            , v.[createdonbehalfby_entitytype]
            , v.[createdonbehalfbyname]
            , v.[createdonbehalfbyyominame]
            , v.[creditlimit]
            , v.[description]
            , v.[disabledreason]
            , v.[divisionname]
            , v.[emailaddress]
            , v.[exchangerate]
            , v.[fileasname]
            , v.[ftpsiteurl]
            , v.[importsequencenumber]
            , v.[inheritancemask]
            , v.[isdisabled]
            , v.[llp_countryid]
            , v.[llp_countryid_entitytype]
            , v.[llp_countryidname]
            , v.[llp_iddealernr]
            , v.[llp_idnetsuite]
            , v.[llp_isworkshop]
            , v.[llp_teamid]
            , v.[llp_teamid_entitytype]
            , v.[llp_teamidname]
            , v.[llp_teamidyominame]
            , v.[llp_utapprovaltemplateid]
            , v.[llp_utapprovaltemplateid_entitytype]
            , v.[llp_utapprovaltemplateidname]
            , v.[llp_utreservationapproverid]
            , v.[llp_utreservationapproverid_entitytype]
            , v.[llp_utreservationapproveridname]
            , v.[llp_utreservationapproveridyominame]
            , v.[modifiedby]
            , v.[modifiedby_entitytype]
            , v.[modifiedbyname]
            , v.[modifiedbyyominame]
            , v.[modifiedon]
            , v.[modifiedonbehalfby]
            , v.[modifiedonbehalfby_entitytype]
            , v.[modifiedonbehalfbyname]
            , v.[modifiedonbehalfbyyominame]
            , v.[name]
            , v.[organizationid]
            , v.[organizationid_entitytype]
            , v.[organizationidname]
            , v.[overriddencreatedon]
            , v.[parentbusinessunitid]
            , v.[parentbusinessunitid_entitytype]
            , v.[parentbusinessunitidname]
            , v.[picture]
            , v.[SinkCreatedOn]
            , v.[SinkModifiedOn]
            , v.[stockexchange]
            , v.[tickersymbol]
            , v.[transactioncurrencyid]
            , v.[transactioncurrencyid_entitytype]
            , v.[transactioncurrencyidname]
            , v.[usergroupid]
            , v.[utcoffset]
            , v.[versionnumber]
            , v.[websiteurl]
            , v.[workflowsuspended]
            , v.[DataSourceId]
            , @ThreadLogId
            , -1
            , -1
            , N'D' -- update
    FROM Vault.CRMdboBusinessunit AS v
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
                , TableFinalRowCount = (SELECT COUNT(*) FROM [Vault].[CRMdboBusinessunit] WITH (NOLOCK))
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
