Stored Procedure Vault.uspLoadCRMdboOpportunity {#spVaultuspLoadCRMdboOpportunity}
-----------------------------------------------

Definition of Stored procedure:

``` {.sql}
CREATE PROCEDURE [Vault].[uspLoadCRMdboOpportunity] 
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
            SET TableInitialRowCount = (SELECT COUNT(*) FROM [Vault].[CRMdboOpportunity] WITH (NOLOCK))
        WHERE ThreadLogId = @ThreadLogId;

            BEGIN TRANSACTION;

    
        MERGE INTO [Vault].[CRMdboOpportunity] AS v
        USING [Stage].[CRMdboOpportunity] AS s
            ON ( s.[Id] = v.[Id]AND s.[DataSourceId] = v.[DataSourceId]
     AND v.[ThreadLogDeleteId] = -1 AND v.[ThreadLogUpdateId] = -1 AND v.[ChangeOperation] <> N'D'
    )

        WHEN MATCHED AND
            (
            v.[accountid] <> s.[accountid]
            OR (v.[accountid] IS NULL AND s.[accountid] IS NOT NULL)
        OR (v.[accountid] IS NOT NULL AND s.[accountid] IS NULL)
        OR v.[accountid_entitytype] <> s.[accountid_entitytype]
            OR (v.[accountid_entitytype] IS NULL AND s.[accountid_entitytype] IS NOT NULL)
        OR (v.[accountid_entitytype] IS NOT NULL AND s.[accountid_entitytype] IS NULL)
        OR v.[accountidname] <> s.[accountidname]
            OR (v.[accountidname] IS NULL AND s.[accountidname] IS NOT NULL)
        OR (v.[accountidname] IS NOT NULL AND s.[accountidname] IS NULL)
        OR v.[accountidyominame] <> s.[accountidyominame]
            OR (v.[accountidyominame] IS NULL AND s.[accountidyominame] IS NOT NULL)
        OR (v.[accountidyominame] IS NOT NULL AND s.[accountidyominame] IS NULL)
        OR v.[actualclosedate] <> s.[actualclosedate]
            OR (v.[actualclosedate] IS NULL AND s.[actualclosedate] IS NOT NULL)
        OR (v.[actualclosedate] IS NOT NULL AND s.[actualclosedate] IS NULL)
        OR v.[actualvalue] <> s.[actualvalue]
            OR (v.[actualvalue] IS NULL AND s.[actualvalue] IS NOT NULL)
        OR (v.[actualvalue] IS NOT NULL AND s.[actualvalue] IS NULL)
        OR v.[actualvalue_base] <> s.[actualvalue_base]
            OR (v.[actualvalue_base] IS NULL AND s.[actualvalue_base] IS NOT NULL)
        OR (v.[actualvalue_base] IS NOT NULL AND s.[actualvalue_base] IS NULL)
        OR v.[budgetamount] <> s.[budgetamount]
            OR (v.[budgetamount] IS NULL AND s.[budgetamount] IS NOT NULL)
        OR (v.[budgetamount] IS NOT NULL AND s.[budgetamount] IS NULL)
        OR v.[budgetamount_base] <> s.[budgetamount_base]
            OR (v.[budgetamount_base] IS NULL AND s.[budgetamount_base] IS NOT NULL)
        OR (v.[budgetamount_base] IS NOT NULL AND s.[budgetamount_base] IS NULL)
        OR v.[budgetstatus] <> s.[budgetstatus]
            OR (v.[budgetstatus] IS NULL AND s.[budgetstatus] IS NOT NULL)
        OR (v.[budgetstatus] IS NOT NULL AND s.[budgetstatus] IS NULL)
        OR v.[campaignid] <> s.[campaignid]
            OR (v.[campaignid] IS NULL AND s.[campaignid] IS NOT NULL)
        OR (v.[campaignid] IS NOT NULL AND s.[campaignid] IS NULL)
        OR v.[campaignid_entitytype] <> s.[campaignid_entitytype]
            OR (v.[campaignid_entitytype] IS NULL AND s.[campaignid_entitytype] IS NOT NULL)
        OR (v.[campaignid_entitytype] IS NOT NULL AND s.[campaignid_entitytype] IS NULL)
        OR v.[campaignidname] <> s.[campaignidname]
            OR (v.[campaignidname] IS NULL AND s.[campaignidname] IS NOT NULL)
        OR (v.[campaignidname] IS NOT NULL AND s.[campaignidname] IS NULL)
        OR v.[captureproposalfeedback] <> s.[captureproposalfeedback]
            OR (v.[captureproposalfeedback] IS NULL AND s.[captureproposalfeedback] IS NOT NULL)
        OR (v.[captureproposalfeedback] IS NOT NULL AND s.[captureproposalfeedback] IS NULL)
        OR v.[closeprobability] <> s.[closeprobability]
            OR (v.[closeprobability] IS NULL AND s.[closeprobability] IS NOT NULL)
        OR (v.[closeprobability] IS NOT NULL AND s.[closeprobability] IS NULL)
        OR v.[completefinalproposal] <> s.[completefinalproposal]
            OR (v.[completefinalproposal] IS NULL AND s.[completefinalproposal] IS NOT NULL)
        OR (v.[completefinalproposal] IS NOT NULL AND s.[completefinalproposal] IS NULL)
        OR v.[completeinternalreview] <> s.[completeinternalreview]
            OR (v.[completeinternalreview] IS NULL AND s.[completeinternalreview] IS NOT NULL)
        OR (v.[completeinternalreview] IS NOT NULL AND s.[completeinternalreview] IS NULL)
        OR v.[confirminterest] <> s.[confirminterest]
            OR (v.[confirminterest] IS NULL AND s.[confirminterest] IS NOT NULL)
        OR (v.[confirminterest] IS NOT NULL AND s.[confirminterest] IS NULL)
        OR v.[contactid] <> s.[contactid]
            OR (v.[contactid] IS NULL AND s.[contactid] IS NOT NULL)
        OR (v.[contactid] IS NOT NULL AND s.[contactid] IS NULL)
        OR v.[contactid_entitytype] <> s.[contactid_entitytype]
            OR (v.[contactid_entitytype] IS NULL AND s.[contactid_entitytype] IS NOT NULL)
        OR (v.[contactid_entitytype] IS NOT NULL AND s.[contactid_entitytype] IS NULL)
        OR v.[contactidname] <> s.[contactidname]
            OR (v.[contactidname] IS NULL AND s.[contactidname] IS NOT NULL)
        OR (v.[contactidname] IS NOT NULL AND s.[contactidname] IS NULL)
        OR v.[contactidyominame] <> s.[contactidyominame]
            OR (v.[contactidyominame] IS NULL AND s.[contactidyominame] IS NOT NULL)
        OR (v.[contactidyominame] IS NOT NULL AND s.[contactidyominame] IS NULL)
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
        OR v.[currentsituation] <> s.[currentsituation]
            OR (v.[currentsituation] IS NULL AND s.[currentsituation] IS NOT NULL)
        OR (v.[currentsituation] IS NOT NULL AND s.[currentsituation] IS NULL)
        OR v.[customerid] <> s.[customerid]
            OR (v.[customerid] IS NULL AND s.[customerid] IS NOT NULL)
        OR (v.[customerid] IS NOT NULL AND s.[customerid] IS NULL)
        OR v.[customerid_entitytype] <> s.[customerid_entitytype]
            OR (v.[customerid_entitytype] IS NULL AND s.[customerid_entitytype] IS NOT NULL)
        OR (v.[customerid_entitytype] IS NOT NULL AND s.[customerid_entitytype] IS NULL)
        OR v.[customeridname] <> s.[customeridname]
            OR (v.[customeridname] IS NULL AND s.[customeridname] IS NOT NULL)
        OR (v.[customeridname] IS NOT NULL AND s.[customeridname] IS NULL)
        OR v.[customeridtype] <> s.[customeridtype]
            OR (v.[customeridtype] IS NULL AND s.[customeridtype] IS NOT NULL)
        OR (v.[customeridtype] IS NOT NULL AND s.[customeridtype] IS NULL)
        OR v.[customeridyominame] <> s.[customeridyominame]
            OR (v.[customeridyominame] IS NULL AND s.[customeridyominame] IS NOT NULL)
        OR (v.[customeridyominame] IS NOT NULL AND s.[customeridyominame] IS NULL)
        OR v.[customerneed] <> s.[customerneed]
            OR (v.[customerneed] IS NULL AND s.[customerneed] IS NOT NULL)
        OR (v.[customerneed] IS NOT NULL AND s.[customerneed] IS NULL)
        OR v.[customerpainpoints] <> s.[customerpainpoints]
            OR (v.[customerpainpoints] IS NULL AND s.[customerpainpoints] IS NOT NULL)
        OR (v.[customerpainpoints] IS NOT NULL AND s.[customerpainpoints] IS NULL)
        OR v.[decisionmaker] <> s.[decisionmaker]
            OR (v.[decisionmaker] IS NULL AND s.[decisionmaker] IS NOT NULL)
        OR (v.[decisionmaker] IS NOT NULL AND s.[decisionmaker] IS NULL)
        OR v.[description] <> s.[description]
            OR (v.[description] IS NULL AND s.[description] IS NOT NULL)
        OR (v.[description] IS NOT NULL AND s.[description] IS NULL)
        OR v.[developproposal] <> s.[developproposal]
            OR (v.[developproposal] IS NULL AND s.[developproposal] IS NOT NULL)
        OR (v.[developproposal] IS NOT NULL AND s.[developproposal] IS NULL)
        OR v.[discountamount] <> s.[discountamount]
            OR (v.[discountamount] IS NULL AND s.[discountamount] IS NOT NULL)
        OR (v.[discountamount] IS NOT NULL AND s.[discountamount] IS NULL)
        OR v.[discountamount_base] <> s.[discountamount_base]
            OR (v.[discountamount_base] IS NULL AND s.[discountamount_base] IS NOT NULL)
        OR (v.[discountamount_base] IS NOT NULL AND s.[discountamount_base] IS NULL)
        OR v.[discountpercentage] <> s.[discountpercentage]
            OR (v.[discountpercentage] IS NULL AND s.[discountpercentage] IS NOT NULL)
        OR (v.[discountpercentage] IS NOT NULL AND s.[discountpercentage] IS NULL)
        OR v.[emailaddress] <> s.[emailaddress]
            OR (v.[emailaddress] IS NULL AND s.[emailaddress] IS NOT NULL)
        OR (v.[emailaddress] IS NOT NULL AND s.[emailaddress] IS NULL)
        OR v.[estimatedclosedate] <> s.[estimatedclosedate]
            OR (v.[estimatedclosedate] IS NULL AND s.[estimatedclosedate] IS NOT NULL)
        OR (v.[estimatedclosedate] IS NOT NULL AND s.[estimatedclosedate] IS NULL)
        OR v.[estimatedvalue] <> s.[estimatedvalue]
            OR (v.[estimatedvalue] IS NULL AND s.[estimatedvalue] IS NOT NULL)
        OR (v.[estimatedvalue] IS NOT NULL AND s.[estimatedvalue] IS NULL)
        OR v.[estimatedvalue_base] <> s.[estimatedvalue_base]
            OR (v.[estimatedvalue_base] IS NULL AND s.[estimatedvalue_base] IS NOT NULL)
        OR (v.[estimatedvalue_base] IS NOT NULL AND s.[estimatedvalue_base] IS NULL)
        OR v.[evaluatefit] <> s.[evaluatefit]
            OR (v.[evaluatefit] IS NULL AND s.[evaluatefit] IS NOT NULL)
        OR (v.[evaluatefit] IS NOT NULL AND s.[evaluatefit] IS NULL)
        OR v.[exchangerate] <> s.[exchangerate]
            OR (v.[exchangerate] IS NULL AND s.[exchangerate] IS NOT NULL)
        OR (v.[exchangerate] IS NOT NULL AND s.[exchangerate] IS NULL)
        OR v.[filedebrief] <> s.[filedebrief]
            OR (v.[filedebrief] IS NULL AND s.[filedebrief] IS NOT NULL)
        OR (v.[filedebrief] IS NOT NULL AND s.[filedebrief] IS NULL)
        OR v.[finaldecisiondate] <> s.[finaldecisiondate]
            OR (v.[finaldecisiondate] IS NULL AND s.[finaldecisiondate] IS NOT NULL)
        OR (v.[finaldecisiondate] IS NOT NULL AND s.[finaldecisiondate] IS NULL)
        OR v.[freightamount] <> s.[freightamount]
            OR (v.[freightamount] IS NULL AND s.[freightamount] IS NOT NULL)
        OR (v.[freightamount] IS NOT NULL AND s.[freightamount] IS NULL)
        OR v.[freightamount_base] <> s.[freightamount_base]
            OR (v.[freightamount_base] IS NULL AND s.[freightamount_base] IS NOT NULL)
        OR (v.[freightamount_base] IS NOT NULL AND s.[freightamount_base] IS NULL)
        OR v.[identifycompetitors] <> s.[identifycompetitors]
            OR (v.[identifycompetitors] IS NULL AND s.[identifycompetitors] IS NOT NULL)
        OR (v.[identifycompetitors] IS NOT NULL AND s.[identifycompetitors] IS NULL)
        OR v.[identifycustomercontacts] <> s.[identifycustomercontacts]
            OR (v.[identifycustomercontacts] IS NULL AND s.[identifycustomercontacts] IS NOT NULL)
        OR (v.[identifycustomercontacts] IS NOT NULL AND s.[identifycustomercontacts] IS NULL)
        OR v.[identifypursuitteam] <> s.[identifypursuitteam]
            OR (v.[identifypursuitteam] IS NULL AND s.[identifypursuitteam] IS NOT NULL)
        OR (v.[identifypursuitteam] IS NOT NULL AND s.[identifypursuitteam] IS NULL)
        OR v.[importsequencenumber] <> s.[importsequencenumber]
            OR (v.[importsequencenumber] IS NULL AND s.[importsequencenumber] IS NOT NULL)
        OR (v.[importsequencenumber] IS NOT NULL AND s.[importsequencenumber] IS NULL)
        OR v.[initialcommunication] <> s.[initialcommunication]
            OR (v.[initialcommunication] IS NULL AND s.[initialcommunication] IS NOT NULL)
        OR (v.[initialcommunication] IS NOT NULL AND s.[initialcommunication] IS NULL)
        OR v.[isprivate] <> s.[isprivate]
            OR (v.[isprivate] IS NULL AND s.[isprivate] IS NOT NULL)
        OR (v.[isprivate] IS NOT NULL AND s.[isprivate] IS NULL)
        OR v.[isrevenuesystemcalculated] <> s.[isrevenuesystemcalculated]
            OR (v.[isrevenuesystemcalculated] IS NULL AND s.[isrevenuesystemcalculated] IS NOT NULL)
        OR (v.[isrevenuesystemcalculated] IS NOT NULL AND s.[isrevenuesystemcalculated] IS NULL)
        OR v.[lastonholdtime] <> s.[lastonholdtime]
            OR (v.[lastonholdtime] IS NULL AND s.[lastonholdtime] IS NOT NULL)
        OR (v.[lastonholdtime] IS NOT NULL AND s.[lastonholdtime] IS NULL)
        OR v.[llp_add] <> s.[llp_add]
            OR (v.[llp_add] IS NULL AND s.[llp_add] IS NOT NULL)
        OR (v.[llp_add] IS NOT NULL AND s.[llp_add] IS NULL)
        OR v.[llp_agreedhandoverdate] <> s.[llp_agreedhandoverdate]
            OR (v.[llp_agreedhandoverdate] IS NULL AND s.[llp_agreedhandoverdate] IS NOT NULL)
        OR (v.[llp_agreedhandoverdate] IS NOT NULL AND s.[llp_agreedhandoverdate] IS NULL)
        OR v.[llp_alltrucksapprovedandaccepted] <> s.[llp_alltrucksapprovedandaccepted]
            OR (v.[llp_alltrucksapprovedandaccepted] IS NULL AND s.[llp_alltrucksapprovedandaccepted] IS NOT NULL)
        OR (v.[llp_alltrucksapprovedandaccepted] IS NOT NULL AND s.[llp_alltrucksapprovedandaccepted] IS NULL)
        OR v.[llp_approvalstatus] <> s.[llp_approvalstatus]
            OR (v.[llp_approvalstatus] IS NULL AND s.[llp_approvalstatus] IS NOT NULL)
        OR (v.[llp_approvalstatus] IS NOT NULL AND s.[llp_approvalstatus] IS NULL)
        OR v.[llp_assetprice] <> s.[llp_assetprice]
            OR (v.[llp_assetprice] IS NULL AND s.[llp_assetprice] IS NOT NULL)
        OR (v.[llp_assetprice] IS NOT NULL AND s.[llp_assetprice] IS NULL)
        OR v.[llp_assetprice_base] <> s.[llp_assetprice_base]
            OR (v.[llp_assetprice_base] IS NULL AND s.[llp_assetprice_base] IS NOT NULL)
        OR (v.[llp_assetprice_base] IS NOT NULL AND s.[llp_assetprice_base] IS NULL)
        OR v.[llp_automaticallycreatedsfopp] <> s.[llp_automaticallycreatedsfopp]
            OR (v.[llp_automaticallycreatedsfopp] IS NULL AND s.[llp_automaticallycreatedsfopp] IS NOT NULL)
        OR (v.[llp_automaticallycreatedsfopp] IS NOT NULL AND s.[llp_automaticallycreatedsfopp] IS NULL)
        OR v.[llp_automaticallycreatedsiopp] <> s.[llp_automaticallycreatedsiopp]
            OR (v.[llp_automaticallycreatedsiopp] IS NULL AND s.[llp_automaticallycreatedsiopp] IS NOT NULL)
        OR (v.[llp_automaticallycreatedsiopp] IS NOT NULL AND s.[llp_automaticallycreatedsiopp] IS NULL)
        OR v.[llp_averageoverdueinlast2years] <> s.[llp_averageoverdueinlast2years]
            OR (v.[llp_averageoverdueinlast2years] IS NULL AND s.[llp_averageoverdueinlast2years] IS NOT NULL)
        OR (v.[llp_averageoverdueinlast2years] IS NOT NULL AND s.[llp_averageoverdueinlast2years] IS NULL)
        OR v.[llp_bodybuildingcontractsigned] <> s.[llp_bodybuildingcontractsigned]
            OR (v.[llp_bodybuildingcontractsigned] IS NULL AND s.[llp_bodybuildingcontractsigned] IS NOT NULL)
        OR (v.[llp_bodybuildingcontractsigned] IS NOT NULL AND s.[llp_bodybuildingcontractsigned] IS NULL)
        OR v.[llp_bodybuildingcoordinatedby] <> s.[llp_bodybuildingcoordinatedby]
            OR (v.[llp_bodybuildingcoordinatedby] IS NULL AND s.[llp_bodybuildingcoordinatedby] IS NOT NULL)
        OR (v.[llp_bodybuildingcoordinatedby] IS NOT NULL AND s.[llp_bodybuildingcoordinatedby] IS NULL)
        OR v.[llp_bodybuildinggeneralsupplierid] <> s.[llp_bodybuildinggeneralsupplierid]
            OR (v.[llp_bodybuildinggeneralsupplierid] IS NULL AND s.[llp_bodybuildinggeneralsupplierid] IS NOT NULL)
        OR (v.[llp_bodybuildinggeneralsupplierid] IS NOT NULL AND s.[llp_bodybuildinggeneralsupplierid] IS NULL)
        OR v.[llp_bodybuildinggeneralsupplierid_entitytype] <> s.[llp_bodybuildinggeneralsupplierid_entitytype]
            OR (v.[llp_bodybuildinggeneralsupplierid_entitytype] IS NULL AND s.[llp_bodybuildinggeneralsupplierid_entitytype] IS NOT NULL)
        OR (v.[llp_bodybuildinggeneralsupplierid_entitytype] IS NOT NULL AND s.[llp_bodybuildinggeneralsupplierid_entitytype] IS NULL)
        OR v.[llp_bodybuildinggeneralsupplieridname] <> s.[llp_bodybuildinggeneralsupplieridname]
            OR (v.[llp_bodybuildinggeneralsupplieridname] IS NULL AND s.[llp_bodybuildinggeneralsupplieridname] IS NOT NULL)
        OR (v.[llp_bodybuildinggeneralsupplieridname] IS NOT NULL AND s.[llp_bodybuildinggeneralsupplieridname] IS NULL)
        OR v.[llp_bodybuildinggeneralsupplieridyominame] <> s.[llp_bodybuildinggeneralsupplieridyominame]
            OR (v.[llp_bodybuildinggeneralsupplieridyominame] IS NULL AND s.[llp_bodybuildinggeneralsupplieridyominame] IS NOT NULL)
        OR (v.[llp_bodybuildinggeneralsupplieridyominame] IS NOT NULL AND s.[llp_bodybuildinggeneralsupplieridyominame] IS NULL)
        OR v.[llp_bodybuildinghandoverdate] <> s.[llp_bodybuildinghandoverdate]
            OR (v.[llp_bodybuildinghandoverdate] IS NULL AND s.[llp_bodybuildinghandoverdate] IS NOT NULL)
        OR (v.[llp_bodybuildinghandoverdate] IS NOT NULL AND s.[llp_bodybuildinghandoverdate] IS NULL)
        OR v.[llp_bodywork] <> s.[llp_bodywork]
            OR (v.[llp_bodywork] IS NULL AND s.[llp_bodywork] IS NOT NULL)
        OR (v.[llp_bodywork] IS NOT NULL AND s.[llp_bodywork] IS NULL)
        OR v.[llp_buofvehicleid] <> s.[llp_buofvehicleid]
            OR (v.[llp_buofvehicleid] IS NULL AND s.[llp_buofvehicleid] IS NOT NULL)
        OR (v.[llp_buofvehicleid] IS NOT NULL AND s.[llp_buofvehicleid] IS NULL)
        OR v.[llp_buofvehicleid_entitytype] <> s.[llp_buofvehicleid_entitytype]
            OR (v.[llp_buofvehicleid_entitytype] IS NULL AND s.[llp_buofvehicleid_entitytype] IS NOT NULL)
        OR (v.[llp_buofvehicleid_entitytype] IS NOT NULL AND s.[llp_buofvehicleid_entitytype] IS NULL)
        OR v.[llp_buofvehicleidname] <> s.[llp_buofvehicleidname]
            OR (v.[llp_buofvehicleidname] IS NULL AND s.[llp_buofvehicleidname] IS NOT NULL)
        OR (v.[llp_buofvehicleidname] IS NOT NULL AND s.[llp_buofvehicleidname] IS NULL)
        OR v.[llp_cdd] <> s.[llp_cdd]
            OR (v.[llp_cdd] IS NULL AND s.[llp_cdd] IS NOT NULL)
        OR (v.[llp_cdd] IS NOT NULL AND s.[llp_cdd] IS NULL)
        OR v.[llp_checkedofcustomerneeds] <> s.[llp_checkedofcustomerneeds]
            OR (v.[llp_checkedofcustomerneeds] IS NULL AND s.[llp_checkedofcustomerneeds] IS NOT NULL)
        OR (v.[llp_checkedofcustomerneeds] IS NOT NULL AND s.[llp_checkedofcustomerneeds] IS NULL)
        OR v.[llp_competitors] <> s.[llp_competitors]
            OR (v.[llp_competitors] IS NULL AND s.[llp_competitors] IS NOT NULL)
        OR (v.[llp_competitors] IS NOT NULL AND s.[llp_competitors] IS NULL)
        OR v.[llp_competitorsinsuraceother] <> s.[llp_competitorsinsuraceother]
            OR (v.[llp_competitorsinsuraceother] IS NULL AND s.[llp_competitorsinsuraceother] IS NOT NULL)
        OR (v.[llp_competitorsinsuraceother] IS NOT NULL AND s.[llp_competitorsinsuraceother] IS NULL)
        OR v.[llp_competitorsinsurance] <> s.[llp_competitorsinsurance]
            OR (v.[llp_competitorsinsurance] IS NULL AND s.[llp_competitorsinsurance] IS NOT NULL)
        OR (v.[llp_competitorsinsurance] IS NOT NULL AND s.[llp_competitorsinsurance] IS NULL)
        OR v.[llp_competitorsinsuranceselection] <> s.[llp_competitorsinsuranceselection]
            OR (v.[llp_competitorsinsuranceselection] IS NULL AND s.[llp_competitorsinsuranceselection] IS NOT NULL)
        OR (v.[llp_competitorsinsuranceselection] IS NOT NULL AND s.[llp_competitorsinsuranceselection] IS NULL)
        OR v.[llp_competitorsleasingother] <> s.[llp_competitorsleasingother]
            OR (v.[llp_competitorsleasingother] IS NULL AND s.[llp_competitorsleasingother] IS NOT NULL)
        OR (v.[llp_competitorsleasingother] IS NOT NULL AND s.[llp_competitorsleasingother] IS NULL)
        OR v.[llp_competitorsselection] <> s.[llp_competitorsselection]
            OR (v.[llp_competitorsselection] IS NULL AND s.[llp_competitorsselection] IS NOT NULL)
        OR (v.[llp_competitorsselection] IS NOT NULL AND s.[llp_competitorsselection] IS NULL)
        OR v.[llp_contractlenght] <> s.[llp_contractlenght]
            OR (v.[llp_contractlenght] IS NULL AND s.[llp_contractlenght] IS NOT NULL)
        OR (v.[llp_contractlenght] IS NOT NULL AND s.[llp_contractlenght] IS NULL)
        OR v.[llp_contractlengthmonth] <> s.[llp_contractlengthmonth]
            OR (v.[llp_contractlengthmonth] IS NULL AND s.[llp_contractlengthmonth] IS NOT NULL)
        OR (v.[llp_contractlengthmonth] IS NOT NULL AND s.[llp_contractlengthmonth] IS NULL)
        OR v.[llp_contractsigned] <> s.[llp_contractsigned]
            OR (v.[llp_contractsigned] IS NULL AND s.[llp_contractsigned] IS NOT NULL)
        OR (v.[llp_contractsigned] IS NOT NULL AND s.[llp_contractsigned] IS NULL)
        OR v.[llp_contractsignedby] <> s.[llp_contractsignedby]
            OR (v.[llp_contractsignedby] IS NULL AND s.[llp_contractsignedby] IS NOT NULL)
        OR (v.[llp_contractsignedby] IS NOT NULL AND s.[llp_contractsignedby] IS NULL)
        OR v.[llp_contractsignedby_entitytype] <> s.[llp_contractsignedby_entitytype]
            OR (v.[llp_contractsignedby_entitytype] IS NULL AND s.[llp_contractsignedby_entitytype] IS NOT NULL)
        OR (v.[llp_contractsignedby_entitytype] IS NOT NULL AND s.[llp_contractsignedby_entitytype] IS NULL)
        OR v.[llp_contractsignedbyname] <> s.[llp_contractsignedbyname]
            OR (v.[llp_contractsignedbyname] IS NULL AND s.[llp_contractsignedbyname] IS NOT NULL)
        OR (v.[llp_contractsignedbyname] IS NOT NULL AND s.[llp_contractsignedbyname] IS NULL)
        OR v.[llp_contractsignedbyon] <> s.[llp_contractsignedbyon]
            OR (v.[llp_contractsignedbyon] IS NULL AND s.[llp_contractsignedbyon] IS NOT NULL)
        OR (v.[llp_contractsignedbyon] IS NOT NULL AND s.[llp_contractsignedbyon] IS NULL)
        OR v.[llp_contractsignedbyyominame] <> s.[llp_contractsignedbyyominame]
            OR (v.[llp_contractsignedbyyominame] IS NULL AND s.[llp_contractsignedbyyominame] IS NOT NULL)
        OR (v.[llp_contractsignedbyyominame] IS NOT NULL AND s.[llp_contractsignedbyyominame] IS NULL)
        OR v.[llp_contracttype] <> s.[llp_contracttype]
            OR (v.[llp_contracttype] IS NULL AND s.[llp_contracttype] IS NOT NULL)
        OR (v.[llp_contracttype] IS NOT NULL AND s.[llp_contracttype] IS NULL)
        OR v.[llp_countofofferedtrucks] <> s.[llp_countofofferedtrucks]
            OR (v.[llp_countofofferedtrucks] IS NULL AND s.[llp_countofofferedtrucks] IS NOT NULL)
        OR (v.[llp_countofofferedtrucks] IS NOT NULL AND s.[llp_countofofferedtrucks] IS NULL)
        OR v.[llp_countofofferedtrucks_date] <> s.[llp_countofofferedtrucks_date]
            OR (v.[llp_countofofferedtrucks_date] IS NULL AND s.[llp_countofofferedtrucks_date] IS NOT NULL)
        OR (v.[llp_countofofferedtrucks_date] IS NOT NULL AND s.[llp_countofofferedtrucks_date] IS NULL)
        OR v.[llp_countofofferedtrucks_state] <> s.[llp_countofofferedtrucks_state]
            OR (v.[llp_countofofferedtrucks_state] IS NULL AND s.[llp_countofofferedtrucks_state] IS NOT NULL)
        OR (v.[llp_countofofferedtrucks_state] IS NOT NULL AND s.[llp_countofofferedtrucks_state] IS NULL)
        OR v.[llp_countrieswerefilled] <> s.[llp_countrieswerefilled]
            OR (v.[llp_countrieswerefilled] IS NULL AND s.[llp_countrieswerefilled] IS NOT NULL)
        OR (v.[llp_countrieswerefilled] IS NOT NULL AND s.[llp_countrieswerefilled] IS NULL)
        OR v.[llp_createdonreport] <> s.[llp_createdonreport]
            OR (v.[llp_createdonreport] IS NULL AND s.[llp_createdonreport] IS NOT NULL)
        OR (v.[llp_createdonreport] IS NOT NULL AND s.[llp_createdonreport] IS NULL)
        OR v.[llp_createsportoffer] <> s.[llp_createsportoffer]
            OR (v.[llp_createsportoffer] IS NULL AND s.[llp_createsportoffer] IS NOT NULL)
        OR (v.[llp_createsportoffer] IS NOT NULL AND s.[llp_createsportoffer] IS NULL)
        OR v.[llp_creditapplicationapproved] <> s.[llp_creditapplicationapproved]
            OR (v.[llp_creditapplicationapproved] IS NULL AND s.[llp_creditapplicationapproved] IS NOT NULL)
        OR (v.[llp_creditapplicationapproved] IS NOT NULL AND s.[llp_creditapplicationapproved] IS NULL)
        OR v.[llp_creditapplicationcreated] <> s.[llp_creditapplicationcreated]
            OR (v.[llp_creditapplicationcreated] IS NULL AND s.[llp_creditapplicationcreated] IS NOT NULL)
        OR (v.[llp_creditapplicationcreated] IS NOT NULL AND s.[llp_creditapplicationcreated] IS NULL)
        OR v.[llp_creditprecheckdone] <> s.[llp_creditprecheckdone]
            OR (v.[llp_creditprecheckdone] IS NULL AND s.[llp_creditprecheckdone] IS NOT NULL)
        OR (v.[llp_creditprecheckdone] IS NOT NULL AND s.[llp_creditprecheckdone] IS NULL)
        OR v.[llp_currency] <> s.[llp_currency]
            OR (v.[llp_currency] IS NULL AND s.[llp_currency] IS NOT NULL)
        OR (v.[llp_currency] IS NOT NULL AND s.[llp_currency] IS NULL)
        OR v.[llp_currency_base] <> s.[llp_currency_base]
            OR (v.[llp_currency_base] IS NULL AND s.[llp_currency_base] IS NOT NULL)
        OR (v.[llp_currency_base] IS NOT NULL AND s.[llp_currency_base] IS NULL)
        OR v.[llp_currentfleetmileage] <> s.[llp_currentfleetmileage]
            OR (v.[llp_currentfleetmileage] IS NULL AND s.[llp_currentfleetmileage] IS NOT NULL)
        OR (v.[llp_currentfleetmileage] IS NOT NULL AND s.[llp_currentfleetmileage] IS NULL)
        OR v.[llp_currentfleetmileagekmyear] <> s.[llp_currentfleetmileagekmyear]
            OR (v.[llp_currentfleetmileagekmyear] IS NULL AND s.[llp_currentfleetmileagekmyear] IS NOT NULL)
        OR (v.[llp_currentfleetmileagekmyear] IS NOT NULL AND s.[llp_currentfleetmileagekmyear] IS NULL)
        OR v.[llp_customeracceptedtheoffer] <> s.[llp_customeracceptedtheoffer]
            OR (v.[llp_customeracceptedtheoffer] IS NULL AND s.[llp_customeracceptedtheoffer] IS NOT NULL)
        OR (v.[llp_customeracceptedtheoffer] IS NOT NULL AND s.[llp_customeracceptedtheoffer] IS NULL)
        OR v.[llp_customerbillingaddress] <> s.[llp_customerbillingaddress]
            OR (v.[llp_customerbillingaddress] IS NULL AND s.[llp_customerbillingaddress] IS NOT NULL)
        OR (v.[llp_customerbillingaddress] IS NOT NULL AND s.[llp_customerbillingaddress] IS NULL)
        OR v.[llp_customeremail] <> s.[llp_customeremail]
            OR (v.[llp_customeremail] IS NULL AND s.[llp_customeremail] IS NOT NULL)
        OR (v.[llp_customeremail] IS NOT NULL AND s.[llp_customeremail] IS NULL)
        OR v.[llp_customername] <> s.[llp_customername]
            OR (v.[llp_customername] IS NULL AND s.[llp_customername] IS NOT NULL)
        OR (v.[llp_customername] IS NOT NULL AND s.[llp_customername] IS NULL)
        OR v.[llp_customerphone] <> s.[llp_customerphone]
            OR (v.[llp_customerphone] IS NULL AND s.[llp_customerphone] IS NOT NULL)
        OR (v.[llp_customerphone] IS NOT NULL AND s.[llp_customerphone] IS NULL)
        OR v.[llp_customerswerefilled] <> s.[llp_customerswerefilled]
            OR (v.[llp_customerswerefilled] IS NULL AND s.[llp_customerswerefilled] IS NOT NULL)
        OR (v.[llp_customerswerefilled] IS NOT NULL AND s.[llp_customerswerefilled] IS NULL)
        OR v.[llp_deliverycompleted] <> s.[llp_deliverycompleted]
            OR (v.[llp_deliverycompleted] IS NULL AND s.[llp_deliverycompleted] IS NOT NULL)
        OR (v.[llp_deliverycompleted] IS NOT NULL AND s.[llp_deliverycompleted] IS NULL)
        OR v.[llp_deliverydate] <> s.[llp_deliverydate]
            OR (v.[llp_deliverydate] IS NULL AND s.[llp_deliverydate] IS NOT NULL)
        OR (v.[llp_deliverydate] IS NOT NULL AND s.[llp_deliverydate] IS NULL)
        OR v.[llp_dout] <> s.[llp_dout]
            OR (v.[llp_dout] IS NULL AND s.[llp_dout] IS NOT NULL)
        OR (v.[llp_dout] IS NOT NULL AND s.[llp_dout] IS NULL)
        OR v.[llp_downpayment] <> s.[llp_downpayment]
            OR (v.[llp_downpayment] IS NULL AND s.[llp_downpayment] IS NOT NULL)
        OR (v.[llp_downpayment] IS NOT NULL AND s.[llp_downpayment] IS NULL)
        OR v.[llp_dppercent] <> s.[llp_dppercent]
            OR (v.[llp_dppercent] IS NULL AND s.[llp_dppercent] IS NOT NULL)
        OR (v.[llp_dppercent] IS NOT NULL AND s.[llp_dppercent] IS NULL)
        OR v.[llp_estimatedbodybuildingcompletiondate] <> s.[llp_estimatedbodybuildingcompletiondate]
            OR (v.[llp_estimatedbodybuildingcompletiondate] IS NULL AND s.[llp_estimatedbodybuildingcompletiondate] IS NOT NULL)
        OR (v.[llp_estimatedbodybuildingcompletiondate] IS NOT NULL AND s.[llp_estimatedbodybuildingcompletiondate] IS NULL)
        OR v.[llp_estimateddeliverydate] <> s.[llp_estimateddeliverydate]
            OR (v.[llp_estimateddeliverydate] IS NULL AND s.[llp_estimateddeliverydate] IS NOT NULL)
        OR (v.[llp_estimateddeliverydate] IS NOT NULL AND s.[llp_estimateddeliverydate] IS NULL)
        OR v.[llp_estimatedorderdate] <> s.[llp_estimatedorderdate]
            OR (v.[llp_estimatedorderdate] IS NULL AND s.[llp_estimatedorderdate] IS NOT NULL)
        OR (v.[llp_estimatedorderdate] IS NOT NULL AND s.[llp_estimatedorderdate] IS NULL)
        OR v.[llp_externalfinancing] <> s.[llp_externalfinancing]
            OR (v.[llp_externalfinancing] IS NULL AND s.[llp_externalfinancing] IS NOT NULL)
        OR (v.[llp_externalfinancing] IS NOT NULL AND s.[llp_externalfinancing] IS NULL)
        OR v.[llp_financing2] <> s.[llp_financing2]
            OR (v.[llp_financing2] IS NULL AND s.[llp_financing2] IS NOT NULL)
        OR (v.[llp_financing2] IS NOT NULL AND s.[llp_financing2] IS NULL)
        OR v.[llp_financingapproved] <> s.[llp_financingapproved]
            OR (v.[llp_financingapproved] IS NULL AND s.[llp_financingapproved] IS NOT NULL)
        OR (v.[llp_financingapproved] IS NOT NULL AND s.[llp_financingapproved] IS NULL)
        OR v.[llp_financingconfirmed] <> s.[llp_financingconfirmed]
            OR (v.[llp_financingconfirmed] IS NULL AND s.[llp_financingconfirmed] IS NOT NULL)
        OR (v.[llp_financingconfirmed] IS NOT NULL AND s.[llp_financingconfirmed] IS NULL)
        OR v.[llp_financinghidden] <> s.[llp_financinghidden]
            OR (v.[llp_financinghidden] IS NULL AND s.[llp_financinghidden] IS NOT NULL)
        OR (v.[llp_financinghidden] IS NOT NULL AND s.[llp_financinghidden] IS NULL)
        OR v.[llp_financingnoreasonother] <> s.[llp_financingnoreasonother]
            OR (v.[llp_financingnoreasonother] IS NULL AND s.[llp_financingnoreasonother] IS NOT NULL)
        OR (v.[llp_financingnoreasonother] IS NOT NULL AND s.[llp_financingnoreasonother] IS NULL)
        OR v.[llp_financingnothereason] <> s.[llp_financingnothereason]
            OR (v.[llp_financingnothereason] IS NULL AND s.[llp_financingnothereason] IS NOT NULL)
        OR (v.[llp_financingnothereason] IS NOT NULL AND s.[llp_financingnothereason] IS NULL)
        OR v.[llp_financingopportunitycreated] <> s.[llp_financingopportunitycreated]
            OR (v.[llp_financingopportunitycreated] IS NULL AND s.[llp_financingopportunitycreated] IS NOT NULL)
        OR (v.[llp_financingopportunitycreated] IS NOT NULL AND s.[llp_financingopportunitycreated] IS NULL)
        OR v.[llp_gdprcheck] <> s.[llp_gdprcheck]
            OR (v.[llp_gdprcheck] IS NULL AND s.[llp_gdprcheck] IS NOT NULL)
        OR (v.[llp_gdprcheck] IS NOT NULL AND s.[llp_gdprcheck] IS NULL)
        OR v.[llp_htmlspread] <> s.[llp_htmlspread]
            OR (v.[llp_htmlspread] IS NULL AND s.[llp_htmlspread] IS NOT NULL)
        OR (v.[llp_htmlspread] IS NOT NULL AND s.[llp_htmlspread] IS NULL)
        OR v.[llp_indicativeofferaccepted] <> s.[llp_indicativeofferaccepted]
            OR (v.[llp_indicativeofferaccepted] IS NULL AND s.[llp_indicativeofferaccepted] IS NOT NULL)
        OR (v.[llp_indicativeofferaccepted] IS NOT NULL AND s.[llp_indicativeofferaccepted] IS NULL)
        OR v.[llp_indicativeofferwassaved] <> s.[llp_indicativeofferwassaved]
            OR (v.[llp_indicativeofferwassaved] IS NULL AND s.[llp_indicativeofferwassaved] IS NOT NULL)
        OR (v.[llp_indicativeofferwassaved] IS NOT NULL AND s.[llp_indicativeofferwassaved] IS NULL)
        OR v.[llp_informationdirectlyfromcustomer] <> s.[llp_informationdirectlyfromcustomer]
            OR (v.[llp_informationdirectlyfromcustomer] IS NULL AND s.[llp_informationdirectlyfromcustomer] IS NOT NULL)
        OR (v.[llp_informationdirectlyfromcustomer] IS NOT NULL AND s.[llp_informationdirectlyfromcustomer] IS NULL)
        OR v.[llp_informationfromjusticecz] <> s.[llp_informationfromjusticecz]
            OR (v.[llp_informationfromjusticecz] IS NULL AND s.[llp_informationfromjusticecz] IS NOT NULL)
        OR (v.[llp_informationfromjusticecz] IS NOT NULL AND s.[llp_informationfromjusticecz] IS NULL)
        OR v.[llp_insurance2] <> s.[llp_insurance2]
            OR (v.[llp_insurance2] IS NULL AND s.[llp_insurance2] IS NOT NULL)
        OR (v.[llp_insurance2] IS NOT NULL AND s.[llp_insurance2] IS NULL)
        OR v.[llp_insurancehidden] <> s.[llp_insurancehidden]
            OR (v.[llp_insurancehidden] IS NULL AND s.[llp_insurancehidden] IS NOT NULL)
        OR (v.[llp_insurancehidden] IS NOT NULL AND s.[llp_insurancehidden] IS NULL)
        OR v.[llp_insuranceprice] <> s.[llp_insuranceprice]
            OR (v.[llp_insuranceprice] IS NULL AND s.[llp_insuranceprice] IS NOT NULL)
        OR (v.[llp_insuranceprice] IS NOT NULL AND s.[llp_insuranceprice] IS NULL)
        OR v.[llp_insuranceprice_base] <> s.[llp_insuranceprice_base]
            OR (v.[llp_insuranceprice_base] IS NULL AND s.[llp_insuranceprice_base] IS NOT NULL)
        OR (v.[llp_insuranceprice_base] IS NOT NULL AND s.[llp_insuranceprice_base] IS NULL)
        OR v.[llp_insuranceproductsselection] <> s.[llp_insuranceproductsselection]
            OR (v.[llp_insuranceproductsselection] IS NULL AND s.[llp_insuranceproductsselection] IS NOT NULL)
        OR (v.[llp_insuranceproductsselection] IS NOT NULL AND s.[llp_insuranceproductsselection] IS NULL)
        OR v.[llp_insuranceproductswereselected] <> s.[llp_insuranceproductswereselected]
            OR (v.[llp_insuranceproductswereselected] IS NULL AND s.[llp_insuranceproductswereselected] IS NOT NULL)
        OR (v.[llp_insuranceproductswereselected] IS NOT NULL AND s.[llp_insuranceproductswereselected] IS NULL)
        OR v.[llp_insurenceoffersend] <> s.[llp_insurenceoffersend]
            OR (v.[llp_insurenceoffersend] IS NULL AND s.[llp_insurenceoffersend] IS NOT NULL)
        OR (v.[llp_insurenceoffersend] IS NOT NULL AND s.[llp_insurenceoffersend] IS NULL)
        OR v.[llp_insurersselection] <> s.[llp_insurersselection]
            OR (v.[llp_insurersselection] IS NULL AND s.[llp_insurersselection] IS NOT NULL)
        OR (v.[llp_insurersselection] IS NOT NULL AND s.[llp_insurersselection] IS NULL)
        OR v.[llp_insurerswereselected] <> s.[llp_insurerswereselected]
            OR (v.[llp_insurerswereselected] IS NULL AND s.[llp_insurerswereselected] IS NOT NULL)
        OR (v.[llp_insurerswereselected] IS NOT NULL AND s.[llp_insurerswereselected] IS NULL)
        OR v.[llp_integrationsportguid] <> s.[llp_integrationsportguid]
            OR (v.[llp_integrationsportguid] IS NULL AND s.[llp_integrationsportguid] IS NOT NULL)
        OR (v.[llp_integrationsportguid] IS NOT NULL AND s.[llp_integrationsportguid] IS NULL)
        OR v.[llp_km] <> s.[llp_km]
            OR (v.[llp_km] IS NULL AND s.[llp_km] IS NOT NULL)
        OR (v.[llp_km] IS NOT NULL AND s.[llp_km] IS NULL)
        OR v.[llp_knownrivaloffer] <> s.[llp_knownrivaloffer]
            OR (v.[llp_knownrivaloffer] IS NULL AND s.[llp_knownrivaloffer] IS NOT NULL)
        OR (v.[llp_knownrivaloffer] IS NOT NULL AND s.[llp_knownrivaloffer] IS NULL)
        OR v.[llp_leasingasset] <> s.[llp_leasingasset]
            OR (v.[llp_leasingasset] IS NULL AND s.[llp_leasingasset] IS NOT NULL)
        OR (v.[llp_leasingasset] IS NOT NULL AND s.[llp_leasingasset] IS NULL)
        OR v.[llp_lockguid] <> s.[llp_lockguid]
            OR (v.[llp_lockguid] IS NULL AND s.[llp_lockguid] IS NOT NULL)
        OR (v.[llp_lockguid] IS NOT NULL AND s.[llp_lockguid] IS NULL)
        OR v.[llp_lossratiopercent] <> s.[llp_lossratiopercent]
            OR (v.[llp_lossratiopercent] IS NULL AND s.[llp_lossratiopercent] IS NOT NULL)
        OR (v.[llp_lossratiopercent] IS NOT NULL AND s.[llp_lossratiopercent] IS NULL)
        OR v.[llp_margin] <> s.[llp_margin]
            OR (v.[llp_margin] IS NULL AND s.[llp_margin] IS NOT NULL)
        OR (v.[llp_margin] IS NOT NULL AND s.[llp_margin] IS NULL)
        OR v.[llp_maxage] <> s.[llp_maxage]
            OR (v.[llp_maxage] IS NULL AND s.[llp_maxage] IS NOT NULL)
        OR (v.[llp_maxage] IS NOT NULL AND s.[llp_maxage] IS NULL)
        OR v.[llp_maxmileage] <> s.[llp_maxmileage]
            OR (v.[llp_maxmileage] IS NULL AND s.[llp_maxmileage] IS NOT NULL)
        OR (v.[llp_maxmileage] IS NOT NULL AND s.[llp_maxmileage] IS NULL)
        OR v.[llp_maxprice] <> s.[llp_maxprice]
            OR (v.[llp_maxprice] IS NULL AND s.[llp_maxprice] IS NOT NULL)
        OR (v.[llp_maxprice] IS NOT NULL AND s.[llp_maxprice] IS NULL)
        OR v.[llp_maxprice_base] <> s.[llp_maxprice_base]
            OR (v.[llp_maxprice_base] IS NULL AND s.[llp_maxprice_base] IS NOT NULL)
        OR (v.[llp_maxprice_base] IS NOT NULL AND s.[llp_maxprice_base] IS NULL)
        OR v.[llp_meetingwithbodybuilder] <> s.[llp_meetingwithbodybuilder]
            OR (v.[llp_meetingwithbodybuilder] IS NULL AND s.[llp_meetingwithbodybuilder] IS NOT NULL)
        OR (v.[llp_meetingwithbodybuilder] IS NOT NULL AND s.[llp_meetingwithbodybuilder] IS NULL)
        OR v.[llp_netsuitechange] <> s.[llp_netsuitechange]
            OR (v.[llp_netsuitechange] IS NULL AND s.[llp_netsuitechange] IS NOT NULL)
        OR (v.[llp_netsuitechange] IS NOT NULL AND s.[llp_netsuitechange] IS NULL)
        OR v.[llp_newpurchasemileagekmyear] <> s.[llp_newpurchasemileagekmyear]
            OR (v.[llp_newpurchasemileagekmyear] IS NULL AND s.[llp_newpurchasemileagekmyear] IS NOT NULL)
        OR (v.[llp_newpurchasemileagekmyear] IS NOT NULL AND s.[llp_newpurchasemileagekmyear] IS NULL)
        OR v.[llp_newpurchusemileage] <> s.[llp_newpurchusemileage]
            OR (v.[llp_newpurchusemileage] IS NULL AND s.[llp_newpurchusemileage] IS NOT NULL)
        OR (v.[llp_newpurchusemileage] IS NOT NULL AND s.[llp_newpurchusemileage] IS NULL)
        OR v.[llp_notifydrivecoach] <> s.[llp_notifydrivecoach]
            OR (v.[llp_notifydrivecoach] IS NULL AND s.[llp_notifydrivecoach] IS NOT NULL)
        OR (v.[llp_notifydrivecoach] IS NOT NULL AND s.[llp_notifydrivecoach] IS NULL)
        OR v.[llp_numberofitemsofobjectspecification] <> s.[llp_numberofitemsofobjectspecification]
            OR (v.[llp_numberofitemsofobjectspecification] IS NULL AND s.[llp_numberofitemsofobjectspecification] IS NOT NULL)
        OR (v.[llp_numberofitemsofobjectspecification] IS NOT NULL AND s.[llp_numberofitemsofobjectspecification] IS NULL)
        OR v.[llp_numberofitemsofobjectspecification_date] <> s.[llp_numberofitemsofobjectspecification_date]
            OR (v.[llp_numberofitemsofobjectspecification_date] IS NULL AND s.[llp_numberofitemsofobjectspecification_date] IS NOT NULL)
        OR (v.[llp_numberofitemsofobjectspecification_date] IS NOT NULL AND s.[llp_numberofitemsofobjectspecification_date] IS NULL)
        OR v.[llp_numberofitemsofobjectspecification_state] <> s.[llp_numberofitemsofobjectspecification_state]
            OR (v.[llp_numberofitemsofobjectspecification_state] IS NULL AND s.[llp_numberofitemsofobjectspecification_state] IS NOT NULL)
        OR (v.[llp_numberofitemsofobjectspecification_state] IS NOT NULL AND s.[llp_numberofitemsofobjectspecification_state] IS NULL)
        OR v.[llp_numberoftrucks] <> s.[llp_numberoftrucks]
            OR (v.[llp_numberoftrucks] IS NULL AND s.[llp_numberoftrucks] IS NOT NULL)
        OR (v.[llp_numberoftrucks] IS NOT NULL AND s.[llp_numberoftrucks] IS NULL)
        OR v.[llp_numberoftrucksinfleet] <> s.[llp_numberoftrucksinfleet]
            OR (v.[llp_numberoftrucksinfleet] IS NULL AND s.[llp_numberoftrucksinfleet] IS NOT NULL)
        OR (v.[llp_numberoftrucksinfleet] IS NOT NULL AND s.[llp_numberoftrucksinfleet] IS NULL)
        OR v.[llp_objectspecificationcompleted] <> s.[llp_objectspecificationcompleted]
            OR (v.[llp_objectspecificationcompleted] IS NULL AND s.[llp_objectspecificationcompleted] IS NOT NULL)
        OR (v.[llp_objectspecificationcompleted] IS NOT NULL AND s.[llp_objectspecificationcompleted] IS NULL)
        OR v.[llp_offeraccepted] <> s.[llp_offeraccepted]
            OR (v.[llp_offeraccepted] IS NULL AND s.[llp_offeraccepted] IS NOT NULL)
        OR (v.[llp_offeraccepted] IS NOT NULL AND s.[llp_offeraccepted] IS NULL)
        OR v.[llp_offeracceptedbycustomer] <> s.[llp_offeracceptedbycustomer]
            OR (v.[llp_offeracceptedbycustomer] IS NULL AND s.[llp_offeracceptedbycustomer] IS NOT NULL)
        OR (v.[llp_offeracceptedbycustomer] IS NOT NULL AND s.[llp_offeracceptedbycustomer] IS NULL)
        OR v.[llp_opportunitycountries_count] <> s.[llp_opportunitycountries_count]
            OR (v.[llp_opportunitycountries_count] IS NULL AND s.[llp_opportunitycountries_count] IS NOT NULL)
        OR (v.[llp_opportunitycountries_count] IS NOT NULL AND s.[llp_opportunitycountries_count] IS NULL)
        OR v.[llp_opportunitycountries_weightsum] <> s.[llp_opportunitycountries_weightsum]
            OR (v.[llp_opportunitycountries_weightsum] IS NULL AND s.[llp_opportunitycountries_weightsum] IS NOT NULL)
        OR (v.[llp_opportunitycountries_weightsum] IS NOT NULL AND s.[llp_opportunitycountries_weightsum] IS NULL)
        OR v.[llp_opportunitycustomer_count] <> s.[llp_opportunitycustomer_count]
            OR (v.[llp_opportunitycustomer_count] IS NULL AND s.[llp_opportunitycustomer_count] IS NOT NULL)
        OR (v.[llp_opportunitycustomer_count] IS NOT NULL AND s.[llp_opportunitycustomer_count] IS NULL)
        OR v.[llp_opportunitycustomer_weightsum] <> s.[llp_opportunitycustomer_weightsum]
            OR (v.[llp_opportunitycustomer_weightsum] IS NULL AND s.[llp_opportunitycustomer_weightsum] IS NOT NULL)
        OR (v.[llp_opportunitycustomer_weightsum] IS NOT NULL AND s.[llp_opportunitycustomer_weightsum] IS NULL)
        OR v.[llp_opportunityforfinancingwaslost] <> s.[llp_opportunityforfinancingwaslost]
            OR (v.[llp_opportunityforfinancingwaslost] IS NULL AND s.[llp_opportunityforfinancingwaslost] IS NOT NULL)
        OR (v.[llp_opportunityforfinancingwaslost] IS NOT NULL AND s.[llp_opportunityforfinancingwaslost] IS NULL)
        OR v.[llp_opportunitynumber] <> s.[llp_opportunitynumber]
            OR (v.[llp_opportunitynumber] IS NULL AND s.[llp_opportunitynumber] IS NOT NULL)
        OR (v.[llp_opportunitynumber] IS NOT NULL AND s.[llp_opportunitynumber] IS NULL)
        OR v.[llp_opportunitypreferableinsurer_count] <> s.[llp_opportunitypreferableinsurer_count]
            OR (v.[llp_opportunitypreferableinsurer_count] IS NULL AND s.[llp_opportunitypreferableinsurer_count] IS NOT NULL)
        OR (v.[llp_opportunitypreferableinsurer_count] IS NOT NULL AND s.[llp_opportunitypreferableinsurer_count] IS NULL)
        OR v.[llp_opportunitytype] <> s.[llp_opportunitytype]
            OR (v.[llp_opportunitytype] IS NULL AND s.[llp_opportunitytype] IS NOT NULL)
        OR (v.[llp_opportunitytype] IS NOT NULL AND s.[llp_opportunitytype] IS NULL)
        OR v.[llp_opportunitytypeofinsurance_count] <> s.[llp_opportunitytypeofinsurance_count]
            OR (v.[llp_opportunitytypeofinsurance_count] IS NULL AND s.[llp_opportunitytypeofinsurance_count] IS NOT NULL)
        OR (v.[llp_opportunitytypeofinsurance_count] IS NOT NULL AND s.[llp_opportunitytypeofinsurance_count] IS NULL)
        OR v.[llp_parentalbuid] <> s.[llp_parentalbuid]
            OR (v.[llp_parentalbuid] IS NULL AND s.[llp_parentalbuid] IS NOT NULL)
        OR (v.[llp_parentalbuid] IS NOT NULL AND s.[llp_parentalbuid] IS NULL)
        OR v.[llp_parentalbuid_entitytype] <> s.[llp_parentalbuid_entitytype]
            OR (v.[llp_parentalbuid_entitytype] IS NULL AND s.[llp_parentalbuid_entitytype] IS NOT NULL)
        OR (v.[llp_parentalbuid_entitytype] IS NOT NULL AND s.[llp_parentalbuid_entitytype] IS NULL)
        OR v.[llp_parentalbuidname] <> s.[llp_parentalbuidname]
            OR (v.[llp_parentalbuidname] IS NULL AND s.[llp_parentalbuidname] IS NOT NULL)
        OR (v.[llp_parentalbuidname] IS NOT NULL AND s.[llp_parentalbuidname] IS NULL)
        OR v.[llp_pdicomplete] <> s.[llp_pdicomplete]
            OR (v.[llp_pdicomplete] IS NULL AND s.[llp_pdicomplete] IS NOT NULL)
        OR (v.[llp_pdicomplete] IS NOT NULL AND s.[llp_pdicomplete] IS NULL)
        OR v.[llp_peakinlastyear] <> s.[llp_peakinlastyear]
            OR (v.[llp_peakinlastyear] IS NULL AND s.[llp_peakinlastyear] IS NOT NULL)
        OR (v.[llp_peakinlastyear] IS NOT NULL AND s.[llp_peakinlastyear] IS NULL)
        OR v.[llp_preferableinsurerid] <> s.[llp_preferableinsurerid]
            OR (v.[llp_preferableinsurerid] IS NULL AND s.[llp_preferableinsurerid] IS NOT NULL)
        OR (v.[llp_preferableinsurerid] IS NOT NULL AND s.[llp_preferableinsurerid] IS NULL)
        OR v.[llp_preferableinsurerid_entitytype] <> s.[llp_preferableinsurerid_entitytype]
            OR (v.[llp_preferableinsurerid_entitytype] IS NULL AND s.[llp_preferableinsurerid_entitytype] IS NOT NULL)
        OR (v.[llp_preferableinsurerid_entitytype] IS NOT NULL AND s.[llp_preferableinsurerid_entitytype] IS NULL)
        OR v.[llp_preferableinsureridname] <> s.[llp_preferableinsureridname]
            OR (v.[llp_preferableinsureridname] IS NULL AND s.[llp_preferableinsureridname] IS NOT NULL)
        OR (v.[llp_preferableinsureridname] IS NOT NULL AND s.[llp_preferableinsureridname] IS NULL)
        OR v.[llp_preferedfinancialproduct] <> s.[llp_preferedfinancialproduct]
            OR (v.[llp_preferedfinancialproduct] IS NULL AND s.[llp_preferedfinancialproduct] IS NOT NULL)
        OR (v.[llp_preferedfinancialproduct] IS NOT NULL AND s.[llp_preferedfinancialproduct] IS NULL)
        OR v.[llp_primaryquoteid] <> s.[llp_primaryquoteid]
            OR (v.[llp_primaryquoteid] IS NULL AND s.[llp_primaryquoteid] IS NOT NULL)
        OR (v.[llp_primaryquoteid] IS NOT NULL AND s.[llp_primaryquoteid] IS NULL)
        OR v.[llp_primaryquoteid_entitytype] <> s.[llp_primaryquoteid_entitytype]
            OR (v.[llp_primaryquoteid_entitytype] IS NULL AND s.[llp_primaryquoteid_entitytype] IS NOT NULL)
        OR (v.[llp_primaryquoteid_entitytype] IS NOT NULL AND s.[llp_primaryquoteid_entitytype] IS NULL)
        OR v.[llp_primaryquoteidname] <> s.[llp_primaryquoteidname]
            OR (v.[llp_primaryquoteidname] IS NULL AND s.[llp_primaryquoteidname] IS NOT NULL)
        OR (v.[llp_primaryquoteidname] IS NOT NULL AND s.[llp_primaryquoteidname] IS NULL)
        OR v.[llp_proposalsentdate] <> s.[llp_proposalsentdate]
            OR (v.[llp_proposalsentdate] IS NULL AND s.[llp_proposalsentdate] IS NOT NULL)
        OR (v.[llp_proposalsentdate] IS NOT NULL AND s.[llp_proposalsentdate] IS NULL)
        OR v.[llp_proposedprice] <> s.[llp_proposedprice]
            OR (v.[llp_proposedprice] IS NULL AND s.[llp_proposedprice] IS NOT NULL)
        OR (v.[llp_proposedprice] IS NOT NULL AND s.[llp_proposedprice] IS NULL)
        OR v.[llp_proposedprice_base] <> s.[llp_proposedprice_base]
            OR (v.[llp_proposedprice_base] IS NULL AND s.[llp_proposedprice_base] IS NOT NULL)
        OR (v.[llp_proposedprice_base] IS NOT NULL AND s.[llp_proposedprice_base] IS NULL)
        OR v.[llp_recordapproved] <> s.[llp_recordapproved]
            OR (v.[llp_recordapproved] IS NULL AND s.[llp_recordapproved] IS NOT NULL)
        OR (v.[llp_recordapproved] IS NOT NULL AND s.[llp_recordapproved] IS NULL)
        OR v.[llp_regno] <> s.[llp_regno]
            OR (v.[llp_regno] IS NULL AND s.[llp_regno] IS NOT NULL)
        OR (v.[llp_regno] IS NOT NULL AND s.[llp_regno] IS NULL)
        OR v.[llp_remark] <> s.[llp_remark]
            OR (v.[llp_remark] IS NULL AND s.[llp_remark] IS NOT NULL)
        OR (v.[llp_remark] IS NOT NULL AND s.[llp_remark] IS NULL)
        OR v.[llp_reservevehicle] <> s.[llp_reservevehicle]
            OR (v.[llp_reservevehicle] IS NULL AND s.[llp_reservevehicle] IS NOT NULL)
        OR (v.[llp_reservevehicle] IS NOT NULL AND s.[llp_reservevehicle] IS NULL)
        OR v.[llp_service] <> s.[llp_service]
            OR (v.[llp_service] IS NULL AND s.[llp_service] IS NOT NULL)
        OR (v.[llp_service] IS NOT NULL AND s.[llp_service] IS NULL)
        OR v.[llp_servicesactivated] <> s.[llp_servicesactivated]
            OR (v.[llp_servicesactivated] IS NULL AND s.[llp_servicesactivated] IS NOT NULL)
        OR (v.[llp_servicesactivated] IS NOT NULL AND s.[llp_servicesactivated] IS NULL)
        OR v.[llp_sfcategory] <> s.[llp_sfcategory]
            OR (v.[llp_sfcategory] IS NULL AND s.[llp_sfcategory] IS NOT NULL)
        OR (v.[llp_sfcategory] IS NOT NULL AND s.[llp_sfcategory] IS NULL)
        OR v.[llp_sourceopportunityid] <> s.[llp_sourceopportunityid]
            OR (v.[llp_sourceopportunityid] IS NULL AND s.[llp_sourceopportunityid] IS NOT NULL)
        OR (v.[llp_sourceopportunityid] IS NOT NULL AND s.[llp_sourceopportunityid] IS NULL)
        OR v.[llp_sourceopportunityid_entitytype] <> s.[llp_sourceopportunityid_entitytype]
            OR (v.[llp_sourceopportunityid_entitytype] IS NULL AND s.[llp_sourceopportunityid_entitytype] IS NOT NULL)
        OR (v.[llp_sourceopportunityid_entitytype] IS NOT NULL AND s.[llp_sourceopportunityid_entitytype] IS NULL)
        OR v.[llp_sourceopportunityidname] <> s.[llp_sourceopportunityidname]
            OR (v.[llp_sourceopportunityidname] IS NULL AND s.[llp_sourceopportunityidname] IS NOT NULL)
        OR (v.[llp_sourceopportunityidname] IS NOT NULL AND s.[llp_sourceopportunityidname] IS NULL)
        OR v.[llp_spreadapplicationapproved] <> s.[llp_spreadapplicationapproved]
            OR (v.[llp_spreadapplicationapproved] IS NULL AND s.[llp_spreadapplicationapproved] IS NOT NULL)
        OR (v.[llp_spreadapplicationapproved] IS NOT NULL AND s.[llp_spreadapplicationapproved] IS NULL)
        OR v.[llp_spreadapplicationmarginreason] <> s.[llp_spreadapplicationmarginreason]
            OR (v.[llp_spreadapplicationmarginreason] IS NULL AND s.[llp_spreadapplicationmarginreason] IS NOT NULL)
        OR (v.[llp_spreadapplicationmarginreason] IS NOT NULL AND s.[llp_spreadapplicationmarginreason] IS NULL)
        OR v.[llp_subjecttbfinanced] <> s.[llp_subjecttbfinanced]
            OR (v.[llp_subjecttbfinanced] IS NULL AND s.[llp_subjecttbfinanced] IS NOT NULL)
        OR (v.[llp_subjecttbfinanced] IS NOT NULL AND s.[llp_subjecttbfinanced] IS NULL)
        OR v.[llp_tradein] <> s.[llp_tradein]
            OR (v.[llp_tradein] IS NULL AND s.[llp_tradein] IS NOT NULL)
        OR (v.[llp_tradein] IS NOT NULL AND s.[llp_tradein] IS NULL)
        OR v.[llp_tradeinrequestcompleted] <> s.[llp_tradeinrequestcompleted]
            OR (v.[llp_tradeinrequestcompleted] IS NULL AND s.[llp_tradeinrequestcompleted] IS NOT NULL)
        OR (v.[llp_tradeinrequestcompleted] IS NOT NULL AND s.[llp_tradeinrequestcompleted] IS NULL)
        OR v.[llp_trucktype] <> s.[llp_trucktype]
            OR (v.[llp_trucktype] IS NULL AND s.[llp_trucktype] IS NOT NULL)
        OR (v.[llp_trucktype] IS NOT NULL AND s.[llp_trucktype] IS NULL)
        OR v.[llp_typeofinsuranceproduct] <> s.[llp_typeofinsuranceproduct]
            OR (v.[llp_typeofinsuranceproduct] IS NULL AND s.[llp_typeofinsuranceproduct] IS NOT NULL)
        OR (v.[llp_typeofinsuranceproduct] IS NOT NULL AND s.[llp_typeofinsuranceproduct] IS NULL)
        OR v.[llp_typeoftransport] <> s.[llp_typeoftransport]
            OR (v.[llp_typeoftransport] IS NULL AND s.[llp_typeoftransport] IS NOT NULL)
        OR (v.[llp_typeoftransport] IS NOT NULL AND s.[llp_typeoftransport] IS NULL)
        OR v.[llp_typeoftransportselection] <> s.[llp_typeoftransportselection]
            OR (v.[llp_typeoftransportselection] IS NULL AND s.[llp_typeoftransportselection] IS NOT NULL)
        OR (v.[llp_typeoftransportselection] IS NOT NULL AND s.[llp_typeoftransportselection] IS NULL)
        OR v.[llp_urljusticecz] <> s.[llp_urljusticecz]
            OR (v.[llp_urljusticecz] IS NULL AND s.[llp_urljusticecz] IS NOT NULL)
        OR (v.[llp_urljusticecz] IS NOT NULL AND s.[llp_urljusticecz] IS NULL)
        OR v.[llp_utreservationapprovalrequired] <> s.[llp_utreservationapprovalrequired]
            OR (v.[llp_utreservationapprovalrequired] IS NULL AND s.[llp_utreservationapprovalrequired] IS NOT NULL)
        OR (v.[llp_utreservationapprovalrequired] IS NOT NULL AND s.[llp_utreservationapprovalrequired] IS NULL)
        OR v.[llp_utreservationapproverhiddenid] <> s.[llp_utreservationapproverhiddenid]
            OR (v.[llp_utreservationapproverhiddenid] IS NULL AND s.[llp_utreservationapproverhiddenid] IS NOT NULL)
        OR (v.[llp_utreservationapproverhiddenid] IS NOT NULL AND s.[llp_utreservationapproverhiddenid] IS NULL)
        OR v.[llp_utreservationapproverhiddenid_entitytype] <> s.[llp_utreservationapproverhiddenid_entitytype]
            OR (v.[llp_utreservationapproverhiddenid_entitytype] IS NULL AND s.[llp_utreservationapproverhiddenid_entitytype] IS NOT NULL)
        OR (v.[llp_utreservationapproverhiddenid_entitytype] IS NOT NULL AND s.[llp_utreservationapproverhiddenid_entitytype] IS NULL)
        OR v.[llp_utreservationapproverhiddenidname] <> s.[llp_utreservationapproverhiddenidname]
            OR (v.[llp_utreservationapproverhiddenidname] IS NULL AND s.[llp_utreservationapproverhiddenidname] IS NOT NULL)
        OR (v.[llp_utreservationapproverhiddenidname] IS NOT NULL AND s.[llp_utreservationapproverhiddenidname] IS NULL)
        OR v.[llp_utreservationapproverhiddenidyominame] <> s.[llp_utreservationapproverhiddenidyominame]
            OR (v.[llp_utreservationapproverhiddenidyominame] IS NULL AND s.[llp_utreservationapproverhiddenidyominame] IS NOT NULL)
        OR (v.[llp_utreservationapproverhiddenidyominame] IS NOT NULL AND s.[llp_utreservationapproverhiddenidyominame] IS NULL)
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
        OR v.[llp_vehicleid] <> s.[llp_vehicleid]
            OR (v.[llp_vehicleid] IS NULL AND s.[llp_vehicleid] IS NOT NULL)
        OR (v.[llp_vehicleid] IS NOT NULL AND s.[llp_vehicleid] IS NULL)
        OR v.[llp_vehicleid_entitytype] <> s.[llp_vehicleid_entitytype]
            OR (v.[llp_vehicleid_entitytype] IS NULL AND s.[llp_vehicleid_entitytype] IS NOT NULL)
        OR (v.[llp_vehicleid_entitytype] IS NOT NULL AND s.[llp_vehicleid_entitytype] IS NULL)
        OR v.[llp_vehicleidname] <> s.[llp_vehicleidname]
            OR (v.[llp_vehicleidname] IS NULL AND s.[llp_vehicleidname] IS NOT NULL)
        OR (v.[llp_vehicleidname] IS NOT NULL AND s.[llp_vehicleidname] IS NULL)
        OR v.[llp_vehicleprice] <> s.[llp_vehicleprice]
            OR (v.[llp_vehicleprice] IS NULL AND s.[llp_vehicleprice] IS NOT NULL)
        OR (v.[llp_vehicleprice] IS NOT NULL AND s.[llp_vehicleprice] IS NULL)
        OR v.[llp_vehicleprice_base] <> s.[llp_vehicleprice_base]
            OR (v.[llp_vehicleprice_base] IS NULL AND s.[llp_vehicleprice_base] IS NOT NULL)
        OR (v.[llp_vehicleprice_base] IS NOT NULL AND s.[llp_vehicleprice_base] IS NULL)
        OR v.[llp_vehicleregistrationnumber] <> s.[llp_vehicleregistrationnumber]
            OR (v.[llp_vehicleregistrationnumber] IS NULL AND s.[llp_vehicleregistrationnumber] IS NOT NULL)
        OR (v.[llp_vehicleregistrationnumber] IS NOT NULL AND s.[llp_vehicleregistrationnumber] IS NULL)
        OR v.[llp_vin] <> s.[llp_vin]
            OR (v.[llp_vin] IS NULL AND s.[llp_vin] IS NOT NULL)
        OR (v.[llp_vin] IS NOT NULL AND s.[llp_vin] IS NULL)
        OR v.[llp_virtualaccount] <> s.[llp_virtualaccount]
            OR (v.[llp_virtualaccount] IS NULL AND s.[llp_virtualaccount] IS NOT NULL)
        OR (v.[llp_virtualaccount] IS NOT NULL AND s.[llp_virtualaccount] IS NULL)
        OR v.[llp_weightsumcountriesissue] <> s.[llp_weightsumcountriesissue]
            OR (v.[llp_weightsumcountriesissue] IS NULL AND s.[llp_weightsumcountriesissue] IS NOT NULL)
        OR (v.[llp_weightsumcountriesissue] IS NOT NULL AND s.[llp_weightsumcountriesissue] IS NULL)
        OR v.[llp_weightsumcustomersissue] <> s.[llp_weightsumcustomersissue]
            OR (v.[llp_weightsumcustomersissue] IS NULL AND s.[llp_weightsumcustomersissue] IS NOT NULL)
        OR (v.[llp_weightsumcustomersissue] IS NOT NULL AND s.[llp_weightsumcustomersissue] IS NULL)
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
        OR v.[msdyn_forecastcategory] <> s.[msdyn_forecastcategory]
            OR (v.[msdyn_forecastcategory] IS NULL AND s.[msdyn_forecastcategory] IS NOT NULL)
        OR (v.[msdyn_forecastcategory] IS NOT NULL AND s.[msdyn_forecastcategory] IS NULL)
        OR v.[name] <> s.[name]
            OR (v.[name] IS NULL AND s.[name] IS NOT NULL)
        OR (v.[name] IS NOT NULL AND s.[name] IS NULL)
        OR v.[need] <> s.[need]
            OR (v.[need] IS NULL AND s.[need] IS NOT NULL)
        OR (v.[need] IS NOT NULL AND s.[need] IS NULL)
        OR v.[onholdtime] <> s.[onholdtime]
            OR (v.[onholdtime] IS NULL AND s.[onholdtime] IS NOT NULL)
        OR (v.[onholdtime] IS NOT NULL AND s.[onholdtime] IS NULL)
        OR v.[opportunityid] <> s.[opportunityid]
            OR (v.[opportunityid] IS NULL AND s.[opportunityid] IS NOT NULL)
        OR (v.[opportunityid] IS NOT NULL AND s.[opportunityid] IS NULL)
        OR v.[opportunityratingcode] <> s.[opportunityratingcode]
            OR (v.[opportunityratingcode] IS NULL AND s.[opportunityratingcode] IS NOT NULL)
        OR (v.[opportunityratingcode] IS NOT NULL AND s.[opportunityratingcode] IS NULL)
        OR v.[originatingleadid] <> s.[originatingleadid]
            OR (v.[originatingleadid] IS NULL AND s.[originatingleadid] IS NOT NULL)
        OR (v.[originatingleadid] IS NOT NULL AND s.[originatingleadid] IS NULL)
        OR v.[originatingleadid_entitytype] <> s.[originatingleadid_entitytype]
            OR (v.[originatingleadid_entitytype] IS NULL AND s.[originatingleadid_entitytype] IS NOT NULL)
        OR (v.[originatingleadid_entitytype] IS NOT NULL AND s.[originatingleadid_entitytype] IS NULL)
        OR v.[originatingleadidname] <> s.[originatingleadidname]
            OR (v.[originatingleadidname] IS NULL AND s.[originatingleadidname] IS NOT NULL)
        OR (v.[originatingleadidname] IS NOT NULL AND s.[originatingleadidname] IS NULL)
        OR v.[originatingleadidyominame] <> s.[originatingleadidyominame]
            OR (v.[originatingleadidyominame] IS NULL AND s.[originatingleadidyominame] IS NOT NULL)
        OR (v.[originatingleadidyominame] IS NOT NULL AND s.[originatingleadidyominame] IS NULL)
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
        OR v.[parentaccountid] <> s.[parentaccountid]
            OR (v.[parentaccountid] IS NULL AND s.[parentaccountid] IS NOT NULL)
        OR (v.[parentaccountid] IS NOT NULL AND s.[parentaccountid] IS NULL)
        OR v.[parentaccountid_entitytype] <> s.[parentaccountid_entitytype]
            OR (v.[parentaccountid_entitytype] IS NULL AND s.[parentaccountid_entitytype] IS NOT NULL)
        OR (v.[parentaccountid_entitytype] IS NOT NULL AND s.[parentaccountid_entitytype] IS NULL)
        OR v.[parentaccountidname] <> s.[parentaccountidname]
            OR (v.[parentaccountidname] IS NULL AND s.[parentaccountidname] IS NOT NULL)
        OR (v.[parentaccountidname] IS NOT NULL AND s.[parentaccountidname] IS NULL)
        OR v.[parentaccountidyominame] <> s.[parentaccountidyominame]
            OR (v.[parentaccountidyominame] IS NULL AND s.[parentaccountidyominame] IS NOT NULL)
        OR (v.[parentaccountidyominame] IS NOT NULL AND s.[parentaccountidyominame] IS NULL)
        OR v.[parentcontactid] <> s.[parentcontactid]
            OR (v.[parentcontactid] IS NULL AND s.[parentcontactid] IS NOT NULL)
        OR (v.[parentcontactid] IS NOT NULL AND s.[parentcontactid] IS NULL)
        OR v.[parentcontactid_entitytype] <> s.[parentcontactid_entitytype]
            OR (v.[parentcontactid_entitytype] IS NULL AND s.[parentcontactid_entitytype] IS NOT NULL)
        OR (v.[parentcontactid_entitytype] IS NOT NULL AND s.[parentcontactid_entitytype] IS NULL)
        OR v.[parentcontactidname] <> s.[parentcontactidname]
            OR (v.[parentcontactidname] IS NULL AND s.[parentcontactidname] IS NOT NULL)
        OR (v.[parentcontactidname] IS NOT NULL AND s.[parentcontactidname] IS NULL)
        OR v.[parentcontactidyominame] <> s.[parentcontactidyominame]
            OR (v.[parentcontactidyominame] IS NULL AND s.[parentcontactidyominame] IS NOT NULL)
        OR (v.[parentcontactidyominame] IS NOT NULL AND s.[parentcontactidyominame] IS NULL)
        OR v.[participatesinworkflow] <> s.[participatesinworkflow]
            OR (v.[participatesinworkflow] IS NULL AND s.[participatesinworkflow] IS NOT NULL)
        OR (v.[participatesinworkflow] IS NOT NULL AND s.[participatesinworkflow] IS NULL)
        OR v.[presentfinalproposal] <> s.[presentfinalproposal]
            OR (v.[presentfinalproposal] IS NULL AND s.[presentfinalproposal] IS NOT NULL)
        OR (v.[presentfinalproposal] IS NOT NULL AND s.[presentfinalproposal] IS NULL)
        OR v.[presentproposal] <> s.[presentproposal]
            OR (v.[presentproposal] IS NULL AND s.[presentproposal] IS NOT NULL)
        OR (v.[presentproposal] IS NOT NULL AND s.[presentproposal] IS NULL)
        OR v.[pricelevelid] <> s.[pricelevelid]
            OR (v.[pricelevelid] IS NULL AND s.[pricelevelid] IS NOT NULL)
        OR (v.[pricelevelid] IS NOT NULL AND s.[pricelevelid] IS NULL)
        OR v.[pricelevelid_entitytype] <> s.[pricelevelid_entitytype]
            OR (v.[pricelevelid_entitytype] IS NULL AND s.[pricelevelid_entitytype] IS NOT NULL)
        OR (v.[pricelevelid_entitytype] IS NOT NULL AND s.[pricelevelid_entitytype] IS NULL)
        OR v.[pricelevelidname] <> s.[pricelevelidname]
            OR (v.[pricelevelidname] IS NULL AND s.[pricelevelidname] IS NOT NULL)
        OR (v.[pricelevelidname] IS NOT NULL AND s.[pricelevelidname] IS NULL)
        OR v.[pricingerrorcode] <> s.[pricingerrorcode]
            OR (v.[pricingerrorcode] IS NULL AND s.[pricingerrorcode] IS NOT NULL)
        OR (v.[pricingerrorcode] IS NOT NULL AND s.[pricingerrorcode] IS NULL)
        OR v.[prioritycode] <> s.[prioritycode]
            OR (v.[prioritycode] IS NULL AND s.[prioritycode] IS NOT NULL)
        OR (v.[prioritycode] IS NOT NULL AND s.[prioritycode] IS NULL)
        OR v.[processid] <> s.[processid]
            OR (v.[processid] IS NULL AND s.[processid] IS NOT NULL)
        OR (v.[processid] IS NOT NULL AND s.[processid] IS NULL)
        OR v.[proposedsolution] <> s.[proposedsolution]
            OR (v.[proposedsolution] IS NULL AND s.[proposedsolution] IS NOT NULL)
        OR (v.[proposedsolution] IS NOT NULL AND s.[proposedsolution] IS NULL)
        OR v.[purchaseprocess] <> s.[purchaseprocess]
            OR (v.[purchaseprocess] IS NULL AND s.[purchaseprocess] IS NOT NULL)
        OR (v.[purchaseprocess] IS NOT NULL AND s.[purchaseprocess] IS NULL)
        OR v.[purchasetimeframe] <> s.[purchasetimeframe]
            OR (v.[purchasetimeframe] IS NULL AND s.[purchasetimeframe] IS NOT NULL)
        OR (v.[purchasetimeframe] IS NOT NULL AND s.[purchasetimeframe] IS NULL)
        OR v.[pursuitdecision] <> s.[pursuitdecision]
            OR (v.[pursuitdecision] IS NULL AND s.[pursuitdecision] IS NOT NULL)
        OR (v.[pursuitdecision] IS NOT NULL AND s.[pursuitdecision] IS NULL)
        OR v.[qualificationcomments] <> s.[qualificationcomments]
            OR (v.[qualificationcomments] IS NULL AND s.[qualificationcomments] IS NOT NULL)
        OR (v.[qualificationcomments] IS NOT NULL AND s.[qualificationcomments] IS NULL)
        OR v.[quotecomments] <> s.[quotecomments]
            OR (v.[quotecomments] IS NULL AND s.[quotecomments] IS NOT NULL)
        OR (v.[quotecomments] IS NOT NULL AND s.[quotecomments] IS NULL)
        OR v.[resolvefeedback] <> s.[resolvefeedback]
            OR (v.[resolvefeedback] IS NULL AND s.[resolvefeedback] IS NOT NULL)
        OR (v.[resolvefeedback] IS NOT NULL AND s.[resolvefeedback] IS NULL)
        OR v.[salesstage] <> s.[salesstage]
            OR (v.[salesstage] IS NULL AND s.[salesstage] IS NOT NULL)
        OR (v.[salesstage] IS NOT NULL AND s.[salesstage] IS NULL)
        OR v.[salesstagecode] <> s.[salesstagecode]
            OR (v.[salesstagecode] IS NULL AND s.[salesstagecode] IS NOT NULL)
        OR (v.[salesstagecode] IS NOT NULL AND s.[salesstagecode] IS NULL)
        OR v.[schedulefollowup_prospect] <> s.[schedulefollowup_prospect]
            OR (v.[schedulefollowup_prospect] IS NULL AND s.[schedulefollowup_prospect] IS NOT NULL)
        OR (v.[schedulefollowup_prospect] IS NOT NULL AND s.[schedulefollowup_prospect] IS NULL)
        OR v.[schedulefollowup_qualify] <> s.[schedulefollowup_qualify]
            OR (v.[schedulefollowup_qualify] IS NULL AND s.[schedulefollowup_qualify] IS NOT NULL)
        OR (v.[schedulefollowup_qualify] IS NOT NULL AND s.[schedulefollowup_qualify] IS NULL)
        OR v.[scheduleproposalmeeting] <> s.[scheduleproposalmeeting]
            OR (v.[scheduleproposalmeeting] IS NULL AND s.[scheduleproposalmeeting] IS NOT NULL)
        OR (v.[scheduleproposalmeeting] IS NOT NULL AND s.[scheduleproposalmeeting] IS NULL)
        OR v.[sendthankyounote] <> s.[sendthankyounote]
            OR (v.[sendthankyounote] IS NULL AND s.[sendthankyounote] IS NOT NULL)
        OR (v.[sendthankyounote] IS NOT NULL AND s.[sendthankyounote] IS NULL)
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
        OR v.[stageid] <> s.[stageid]
            OR (v.[stageid] IS NULL AND s.[stageid] IS NOT NULL)
        OR (v.[stageid] IS NOT NULL AND s.[stageid] IS NULL)
        OR v.[statecode] <> s.[statecode]
            OR (v.[statecode] IS NULL AND s.[statecode] IS NOT NULL)
        OR (v.[statecode] IS NOT NULL AND s.[statecode] IS NULL)
        OR v.[statuscode] <> s.[statuscode]
            OR (v.[statuscode] IS NULL AND s.[statuscode] IS NOT NULL)
        OR (v.[statuscode] IS NOT NULL AND s.[statuscode] IS NULL)
        OR v.[stepid] <> s.[stepid]
            OR (v.[stepid] IS NULL AND s.[stepid] IS NOT NULL)
        OR (v.[stepid] IS NOT NULL AND s.[stepid] IS NULL)
        OR v.[stepname] <> s.[stepname]
            OR (v.[stepname] IS NULL AND s.[stepname] IS NOT NULL)
        OR (v.[stepname] IS NOT NULL AND s.[stepname] IS NULL)
        OR v.[teamsfollowed] <> s.[teamsfollowed]
            OR (v.[teamsfollowed] IS NULL AND s.[teamsfollowed] IS NOT NULL)
        OR (v.[teamsfollowed] IS NOT NULL AND s.[teamsfollowed] IS NULL)
        OR v.[timeline] <> s.[timeline]
            OR (v.[timeline] IS NULL AND s.[timeline] IS NOT NULL)
        OR (v.[timeline] IS NOT NULL AND s.[timeline] IS NULL)
        OR v.[timespentbymeonemailandmeetings] <> s.[timespentbymeonemailandmeetings]
            OR (v.[timespentbymeonemailandmeetings] IS NULL AND s.[timespentbymeonemailandmeetings] IS NOT NULL)
        OR (v.[timespentbymeonemailandmeetings] IS NOT NULL AND s.[timespentbymeonemailandmeetings] IS NULL)
        OR v.[timezoneruleversionnumber] <> s.[timezoneruleversionnumber]
            OR (v.[timezoneruleversionnumber] IS NULL AND s.[timezoneruleversionnumber] IS NOT NULL)
        OR (v.[timezoneruleversionnumber] IS NOT NULL AND s.[timezoneruleversionnumber] IS NULL)
        OR v.[totalamount] <> s.[totalamount]
            OR (v.[totalamount] IS NULL AND s.[totalamount] IS NOT NULL)
        OR (v.[totalamount] IS NOT NULL AND s.[totalamount] IS NULL)
        OR v.[totalamount_base] <> s.[totalamount_base]
            OR (v.[totalamount_base] IS NULL AND s.[totalamount_base] IS NOT NULL)
        OR (v.[totalamount_base] IS NOT NULL AND s.[totalamount_base] IS NULL)
        OR v.[totalamountlessfreight] <> s.[totalamountlessfreight]
            OR (v.[totalamountlessfreight] IS NULL AND s.[totalamountlessfreight] IS NOT NULL)
        OR (v.[totalamountlessfreight] IS NOT NULL AND s.[totalamountlessfreight] IS NULL)
        OR v.[totalamountlessfreight_base] <> s.[totalamountlessfreight_base]
            OR (v.[totalamountlessfreight_base] IS NULL AND s.[totalamountlessfreight_base] IS NOT NULL)
        OR (v.[totalamountlessfreight_base] IS NOT NULL AND s.[totalamountlessfreight_base] IS NULL)
        OR v.[totaldiscountamount] <> s.[totaldiscountamount]
            OR (v.[totaldiscountamount] IS NULL AND s.[totaldiscountamount] IS NOT NULL)
        OR (v.[totaldiscountamount] IS NOT NULL AND s.[totaldiscountamount] IS NULL)
        OR v.[totaldiscountamount_base] <> s.[totaldiscountamount_base]
            OR (v.[totaldiscountamount_base] IS NULL AND s.[totaldiscountamount_base] IS NOT NULL)
        OR (v.[totaldiscountamount_base] IS NOT NULL AND s.[totaldiscountamount_base] IS NULL)
        OR v.[totallineitemamount] <> s.[totallineitemamount]
            OR (v.[totallineitemamount] IS NULL AND s.[totallineitemamount] IS NOT NULL)
        OR (v.[totallineitemamount] IS NOT NULL AND s.[totallineitemamount] IS NULL)
        OR v.[totallineitemamount_base] <> s.[totallineitemamount_base]
            OR (v.[totallineitemamount_base] IS NULL AND s.[totallineitemamount_base] IS NOT NULL)
        OR (v.[totallineitemamount_base] IS NOT NULL AND s.[totallineitemamount_base] IS NULL)
        OR v.[totallineitemdiscountamount] <> s.[totallineitemdiscountamount]
            OR (v.[totallineitemdiscountamount] IS NULL AND s.[totallineitemdiscountamount] IS NOT NULL)
        OR (v.[totallineitemdiscountamount] IS NOT NULL AND s.[totallineitemdiscountamount] IS NULL)
        OR v.[totallineitemdiscountamount_base] <> s.[totallineitemdiscountamount_base]
            OR (v.[totallineitemdiscountamount_base] IS NULL AND s.[totallineitemdiscountamount_base] IS NOT NULL)
        OR (v.[totallineitemdiscountamount_base] IS NOT NULL AND s.[totallineitemdiscountamount_base] IS NULL)
        OR v.[totaltax] <> s.[totaltax]
            OR (v.[totaltax] IS NULL AND s.[totaltax] IS NOT NULL)
        OR (v.[totaltax] IS NOT NULL AND s.[totaltax] IS NULL)
        OR v.[totaltax_base] <> s.[totaltax_base]
            OR (v.[totaltax_base] IS NULL AND s.[totaltax_base] IS NOT NULL)
        OR (v.[totaltax_base] IS NOT NULL AND s.[totaltax_base] IS NULL)
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
        OR v.[wa_brandid] <> s.[wa_brandid]
            OR (v.[wa_brandid] IS NULL AND s.[wa_brandid] IS NOT NULL)
        OR (v.[wa_brandid] IS NOT NULL AND s.[wa_brandid] IS NULL)
        OR v.[wa_brandid_entitytype] <> s.[wa_brandid_entitytype]
            OR (v.[wa_brandid_entitytype] IS NULL AND s.[wa_brandid_entitytype] IS NOT NULL)
        OR (v.[wa_brandid_entitytype] IS NOT NULL AND s.[wa_brandid_entitytype] IS NULL)
        OR v.[wa_brandidname] <> s.[wa_brandidname]
            OR (v.[wa_brandidname] IS NULL AND s.[wa_brandidname] IS NOT NULL)
        OR (v.[wa_brandidname] IS NOT NULL AND s.[wa_brandidname] IS NULL)
        OR v.[wa_externalid] <> s.[wa_externalid]
            OR (v.[wa_externalid] IS NULL AND s.[wa_externalid] IS NOT NULL)
        OR (v.[wa_externalid] IS NOT NULL AND s.[wa_externalid] IS NULL)
        OR v.[wa_opportunitygroup] <> s.[wa_opportunitygroup]
            OR (v.[wa_opportunitygroup] IS NULL AND s.[wa_opportunitygroup] IS NOT NULL)
        OR (v.[wa_opportunitygroup] IS NOT NULL AND s.[wa_opportunitygroup] IS NULL)
        OR v.[wa_opportunitygroup_entitytype] <> s.[wa_opportunitygroup_entitytype]
            OR (v.[wa_opportunitygroup_entitytype] IS NULL AND s.[wa_opportunitygroup_entitytype] IS NOT NULL)
        OR (v.[wa_opportunitygroup_entitytype] IS NOT NULL AND s.[wa_opportunitygroup_entitytype] IS NULL)
        OR v.[wa_opportunitygroupname] <> s.[wa_opportunitygroupname]
            OR (v.[wa_opportunitygroupname] IS NULL AND s.[wa_opportunitygroupname] IS NOT NULL)
        OR (v.[wa_opportunitygroupname] IS NOT NULL AND s.[wa_opportunitygroupname] IS NULL)
        OR v.[wa_opportunitysourceid] <> s.[wa_opportunitysourceid]
            OR (v.[wa_opportunitysourceid] IS NULL AND s.[wa_opportunitysourceid] IS NOT NULL)
        OR (v.[wa_opportunitysourceid] IS NOT NULL AND s.[wa_opportunitysourceid] IS NULL)
        OR v.[wa_opportunitysourceid_entitytype] <> s.[wa_opportunitysourceid_entitytype]
            OR (v.[wa_opportunitysourceid_entitytype] IS NULL AND s.[wa_opportunitysourceid_entitytype] IS NOT NULL)
        OR (v.[wa_opportunitysourceid_entitytype] IS NOT NULL AND s.[wa_opportunitysourceid_entitytype] IS NULL)
        OR v.[wa_opportunitysourceidname] <> s.[wa_opportunitysourceidname]
            OR (v.[wa_opportunitysourceidname] IS NULL AND s.[wa_opportunitysourceidname] IS NOT NULL)
        OR (v.[wa_opportunitysourceidname] IS NOT NULL AND s.[wa_opportunitysourceidname] IS NULL)
        OR v.[wa_productid] <> s.[wa_productid]
            OR (v.[wa_productid] IS NULL AND s.[wa_productid] IS NOT NULL)
        OR (v.[wa_productid] IS NOT NULL AND s.[wa_productid] IS NULL)
        OR v.[wa_productid_entitytype] <> s.[wa_productid_entitytype]
            OR (v.[wa_productid_entitytype] IS NULL AND s.[wa_productid_entitytype] IS NOT NULL)
        OR (v.[wa_productid_entitytype] IS NOT NULL AND s.[wa_productid_entitytype] IS NULL)
        OR v.[wa_productidname] <> s.[wa_productidname]
            OR (v.[wa_productidname] IS NULL AND s.[wa_productidname] IS NOT NULL)
        OR (v.[wa_productidname] IS NOT NULL AND s.[wa_productidname] IS NULL)
        )
        THEN 
            UPDATE SET
                [ThreadLogUpdateId] = @ThreadLogId
            

                
        WHEN NOT MATCHED BY TARGET 
            THEN INSERT
            ( 
            [Id]
            , [accountid]
            , [accountid_entitytype]
            , [accountidname]
            , [accountidyominame]
            , [actualclosedate]
            , [actualvalue]
            , [actualvalue_base]
            , [budgetamount]
            , [budgetamount_base]
            , [budgetstatus]
            , [campaignid]
            , [campaignid_entitytype]
            , [campaignidname]
            , [captureproposalfeedback]
            , [closeprobability]
            , [completefinalproposal]
            , [completeinternalreview]
            , [confirminterest]
            , [contactid]
            , [contactid_entitytype]
            , [contactidname]
            , [contactidyominame]
            , [createdby]
            , [createdby_entitytype]
            , [createdbyname]
            , [createdbyyominame]
            , [createdon]
            , [createdonbehalfby]
            , [createdonbehalfby_entitytype]
            , [createdonbehalfbyname]
            , [createdonbehalfbyyominame]
            , [currentsituation]
            , [customerid]
            , [customerid_entitytype]
            , [customeridname]
            , [customeridtype]
            , [customeridyominame]
            , [customerneed]
            , [customerpainpoints]
            , [decisionmaker]
            , [description]
            , [developproposal]
            , [discountamount]
            , [discountamount_base]
            , [discountpercentage]
            , [emailaddress]
            , [estimatedclosedate]
            , [estimatedvalue]
            , [estimatedvalue_base]
            , [evaluatefit]
            , [exchangerate]
            , [filedebrief]
            , [finaldecisiondate]
            , [freightamount]
            , [freightamount_base]
            , [identifycompetitors]
            , [identifycustomercontacts]
            , [identifypursuitteam]
            , [importsequencenumber]
            , [initialcommunication]
            , [isprivate]
            , [isrevenuesystemcalculated]
            , [lastonholdtime]
            , [llp_add]
            , [llp_agreedhandoverdate]
            , [llp_alltrucksapprovedandaccepted]
            , [llp_approvalstatus]
            , [llp_assetprice]
            , [llp_assetprice_base]
            , [llp_automaticallycreatedsfopp]
            , [llp_automaticallycreatedsiopp]
            , [llp_averageoverdueinlast2years]
            , [llp_bodybuildingcontractsigned]
            , [llp_bodybuildingcoordinatedby]
            , [llp_bodybuildinggeneralsupplierid]
            , [llp_bodybuildinggeneralsupplierid_entitytype]
            , [llp_bodybuildinggeneralsupplieridname]
            , [llp_bodybuildinggeneralsupplieridyominame]
            , [llp_bodybuildinghandoverdate]
            , [llp_bodywork]
            , [llp_buofvehicleid]
            , [llp_buofvehicleid_entitytype]
            , [llp_buofvehicleidname]
            , [llp_cdd]
            , [llp_checkedofcustomerneeds]
            , [llp_competitors]
            , [llp_competitorsinsuraceother]
            , [llp_competitorsinsurance]
            , [llp_competitorsinsuranceselection]
            , [llp_competitorsleasingother]
            , [llp_competitorsselection]
            , [llp_contractlenght]
            , [llp_contractlengthmonth]
            , [llp_contractsigned]
            , [llp_contractsignedby]
            , [llp_contractsignedby_entitytype]
            , [llp_contractsignedbyname]
            , [llp_contractsignedbyon]
            , [llp_contractsignedbyyominame]
            , [llp_contracttype]
            , [llp_countofofferedtrucks]
            , [llp_countofofferedtrucks_date]
            , [llp_countofofferedtrucks_state]
            , [llp_countrieswerefilled]
            , [llp_createdonreport]
            , [llp_createsportoffer]
            , [llp_creditapplicationapproved]
            , [llp_creditapplicationcreated]
            , [llp_creditprecheckdone]
            , [llp_currency]
            , [llp_currency_base]
            , [llp_currentfleetmileage]
            , [llp_currentfleetmileagekmyear]
            , [llp_customeracceptedtheoffer]
            , [llp_customerbillingaddress]
            , [llp_customeremail]
            , [llp_customername]
            , [llp_customerphone]
            , [llp_customerswerefilled]
            , [llp_deliverycompleted]
            , [llp_deliverydate]
            , [llp_dout]
            , [llp_downpayment]
            , [llp_dppercent]
            , [llp_estimatedbodybuildingcompletiondate]
            , [llp_estimateddeliverydate]
            , [llp_estimatedorderdate]
            , [llp_externalfinancing]
            , [llp_financing2]
            , [llp_financingapproved]
            , [llp_financingconfirmed]
            , [llp_financinghidden]
            , [llp_financingnoreasonother]
            , [llp_financingnothereason]
            , [llp_financingopportunitycreated]
            , [llp_gdprcheck]
            , [llp_htmlspread]
            , [llp_indicativeofferaccepted]
            , [llp_indicativeofferwassaved]
            , [llp_informationdirectlyfromcustomer]
            , [llp_informationfromjusticecz]
            , [llp_insurance2]
            , [llp_insurancehidden]
            , [llp_insuranceprice]
            , [llp_insuranceprice_base]
            , [llp_insuranceproductsselection]
            , [llp_insuranceproductswereselected]
            , [llp_insurenceoffersend]
            , [llp_insurersselection]
            , [llp_insurerswereselected]
            , [llp_integrationsportguid]
            , [llp_km]
            , [llp_knownrivaloffer]
            , [llp_leasingasset]
            , [llp_lockguid]
            , [llp_lossratiopercent]
            , [llp_margin]
            , [llp_maxage]
            , [llp_maxmileage]
            , [llp_maxprice]
            , [llp_maxprice_base]
            , [llp_meetingwithbodybuilder]
            , [llp_netsuitechange]
            , [llp_newpurchasemileagekmyear]
            , [llp_newpurchusemileage]
            , [llp_notifydrivecoach]
            , [llp_numberofitemsofobjectspecification]
            , [llp_numberofitemsofobjectspecification_date]
            , [llp_numberofitemsofobjectspecification_state]
            , [llp_numberoftrucks]
            , [llp_numberoftrucksinfleet]
            , [llp_objectspecificationcompleted]
            , [llp_offeraccepted]
            , [llp_offeracceptedbycustomer]
            , [llp_opportunitycountries_count]
            , [llp_opportunitycountries_weightsum]
            , [llp_opportunitycustomer_count]
            , [llp_opportunitycustomer_weightsum]
            , [llp_opportunityforfinancingwaslost]
            , [llp_opportunitynumber]
            , [llp_opportunitypreferableinsurer_count]
            , [llp_opportunitytype]
            , [llp_opportunitytypeofinsurance_count]
            , [llp_parentalbuid]
            , [llp_parentalbuid_entitytype]
            , [llp_parentalbuidname]
            , [llp_pdicomplete]
            , [llp_peakinlastyear]
            , [llp_preferableinsurerid]
            , [llp_preferableinsurerid_entitytype]
            , [llp_preferableinsureridname]
            , [llp_preferedfinancialproduct]
            , [llp_primaryquoteid]
            , [llp_primaryquoteid_entitytype]
            , [llp_primaryquoteidname]
            , [llp_proposalsentdate]
            , [llp_proposedprice]
            , [llp_proposedprice_base]
            , [llp_recordapproved]
            , [llp_regno]
            , [llp_remark]
            , [llp_reservevehicle]
            , [llp_service]
            , [llp_servicesactivated]
            , [llp_sfcategory]
            , [llp_sourceopportunityid]
            , [llp_sourceopportunityid_entitytype]
            , [llp_sourceopportunityidname]
            , [llp_spreadapplicationapproved]
            , [llp_spreadapplicationmarginreason]
            , [llp_subjecttbfinanced]
            , [llp_tradein]
            , [llp_tradeinrequestcompleted]
            , [llp_trucktype]
            , [llp_typeofinsuranceproduct]
            , [llp_typeoftransport]
            , [llp_typeoftransportselection]
            , [llp_urljusticecz]
            , [llp_utreservationapprovalrequired]
            , [llp_utreservationapproverhiddenid]
            , [llp_utreservationapproverhiddenid_entitytype]
            , [llp_utreservationapproverhiddenidname]
            , [llp_utreservationapproverhiddenidyominame]
            , [llp_utsalespersonid]
            , [llp_utsalespersonid_entitytype]
            , [llp_utsalespersonidname]
            , [llp_utsalespersonidyominame]
            , [llp_vehicleid]
            , [llp_vehicleid_entitytype]
            , [llp_vehicleidname]
            , [llp_vehicleprice]
            , [llp_vehicleprice_base]
            , [llp_vehicleregistrationnumber]
            , [llp_vin]
            , [llp_virtualaccount]
            , [llp_weightsumcountriesissue]
            , [llp_weightsumcustomersissue]
            , [modifiedby]
            , [modifiedby_entitytype]
            , [modifiedbyname]
            , [modifiedbyyominame]
            , [modifiedon]
            , [modifiedonbehalfby]
            , [modifiedonbehalfby_entitytype]
            , [modifiedonbehalfbyname]
            , [modifiedonbehalfbyyominame]
            , [msdyn_forecastcategory]
            , [name]
            , [need]
            , [onholdtime]
            , [opportunityid]
            , [opportunityratingcode]
            , [originatingleadid]
            , [originatingleadid_entitytype]
            , [originatingleadidname]
            , [originatingleadidyominame]
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
            , [parentaccountid]
            , [parentaccountid_entitytype]
            , [parentaccountidname]
            , [parentaccountidyominame]
            , [parentcontactid]
            , [parentcontactid_entitytype]
            , [parentcontactidname]
            , [parentcontactidyominame]
            , [participatesinworkflow]
            , [presentfinalproposal]
            , [presentproposal]
            , [pricelevelid]
            , [pricelevelid_entitytype]
            , [pricelevelidname]
            , [pricingerrorcode]
            , [prioritycode]
            , [processid]
            , [proposedsolution]
            , [purchaseprocess]
            , [purchasetimeframe]
            , [pursuitdecision]
            , [qualificationcomments]
            , [quotecomments]
            , [resolvefeedback]
            , [salesstage]
            , [salesstagecode]
            , [schedulefollowup_prospect]
            , [schedulefollowup_qualify]
            , [scheduleproposalmeeting]
            , [sendthankyounote]
            , [SinkCreatedOn]
            , [SinkModifiedOn]
            , [slaid]
            , [slaid_entitytype]
            , [slainvokedid]
            , [slainvokedid_entitytype]
            , [slainvokedidname]
            , [slaname]
            , [stageid]
            , [statecode]
            , [statuscode]
            , [stepid]
            , [stepname]
            , [teamsfollowed]
            , [timeline]
            , [timespentbymeonemailandmeetings]
            , [timezoneruleversionnumber]
            , [totalamount]
            , [totalamount_base]
            , [totalamountlessfreight]
            , [totalamountlessfreight_base]
            , [totaldiscountamount]
            , [totaldiscountamount_base]
            , [totallineitemamount]
            , [totallineitemamount_base]
            , [totallineitemdiscountamount]
            , [totallineitemdiscountamount_base]
            , [totaltax]
            , [totaltax_base]
            , [transactioncurrencyid]
            , [transactioncurrencyid_entitytype]
            , [transactioncurrencyidname]
            , [traversedpath]
            , [utcconversiontimezonecode]
            , [versionnumber]
            , [wa_brandid]
            , [wa_brandid_entitytype]
            , [wa_brandidname]
            , [wa_externalid]
            , [wa_opportunitygroup]
            , [wa_opportunitygroup_entitytype]
            , [wa_opportunitygroupname]
            , [wa_opportunitysourceid]
            , [wa_opportunitysourceid_entitytype]
            , [wa_opportunitysourceidname]
            , [wa_productid]
            , [wa_productid_entitytype]
            , [wa_productidname]
            , [DataSourceId]
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
            
    ) VALUES (
            s.[Id]
            , s.[accountid]
            , s.[accountid_entitytype]
            , s.[accountidname]
            , s.[accountidyominame]
            , s.[actualclosedate]
            , s.[actualvalue]
            , s.[actualvalue_base]
            , s.[budgetamount]
            , s.[budgetamount_base]
            , s.[budgetstatus]
            , s.[campaignid]
            , s.[campaignid_entitytype]
            , s.[campaignidname]
            , s.[captureproposalfeedback]
            , s.[closeprobability]
            , s.[completefinalproposal]
            , s.[completeinternalreview]
            , s.[confirminterest]
            , s.[contactid]
            , s.[contactid_entitytype]
            , s.[contactidname]
            , s.[contactidyominame]
            , s.[createdby]
            , s.[createdby_entitytype]
            , s.[createdbyname]
            , s.[createdbyyominame]
            , s.[createdon]
            , s.[createdonbehalfby]
            , s.[createdonbehalfby_entitytype]
            , s.[createdonbehalfbyname]
            , s.[createdonbehalfbyyominame]
            , s.[currentsituation]
            , s.[customerid]
            , s.[customerid_entitytype]
            , s.[customeridname]
            , s.[customeridtype]
            , s.[customeridyominame]
            , s.[customerneed]
            , s.[customerpainpoints]
            , s.[decisionmaker]
            , s.[description]
            , s.[developproposal]
            , s.[discountamount]
            , s.[discountamount_base]
            , s.[discountpercentage]
            , s.[emailaddress]
            , s.[estimatedclosedate]
            , s.[estimatedvalue]
            , s.[estimatedvalue_base]
            , s.[evaluatefit]
            , s.[exchangerate]
            , s.[filedebrief]
            , s.[finaldecisiondate]
            , s.[freightamount]
            , s.[freightamount_base]
            , s.[identifycompetitors]
            , s.[identifycustomercontacts]
            , s.[identifypursuitteam]
            , s.[importsequencenumber]
            , s.[initialcommunication]
            , s.[isprivate]
            , s.[isrevenuesystemcalculated]
            , s.[lastonholdtime]
            , s.[llp_add]
            , s.[llp_agreedhandoverdate]
            , s.[llp_alltrucksapprovedandaccepted]
            , s.[llp_approvalstatus]
            , s.[llp_assetprice]
            , s.[llp_assetprice_base]
            , s.[llp_automaticallycreatedsfopp]
            , s.[llp_automaticallycreatedsiopp]
            , s.[llp_averageoverdueinlast2years]
            , s.[llp_bodybuildingcontractsigned]
            , s.[llp_bodybuildingcoordinatedby]
            , s.[llp_bodybuildinggeneralsupplierid]
            , s.[llp_bodybuildinggeneralsupplierid_entitytype]
            , s.[llp_bodybuildinggeneralsupplieridname]
            , s.[llp_bodybuildinggeneralsupplieridyominame]
            , s.[llp_bodybuildinghandoverdate]
            , s.[llp_bodywork]
            , s.[llp_buofvehicleid]
            , s.[llp_buofvehicleid_entitytype]
            , s.[llp_buofvehicleidname]
            , s.[llp_cdd]
            , s.[llp_checkedofcustomerneeds]
            , s.[llp_competitors]
            , s.[llp_competitorsinsuraceother]
            , s.[llp_competitorsinsurance]
            , s.[llp_competitorsinsuranceselection]
            , s.[llp_competitorsleasingother]
            , s.[llp_competitorsselection]
            , s.[llp_contractlenght]
            , s.[llp_contractlengthmonth]
            , s.[llp_contractsigned]
            , s.[llp_contractsignedby]
            , s.[llp_contractsignedby_entitytype]
            , s.[llp_contractsignedbyname]
            , s.[llp_contractsignedbyon]
            , s.[llp_contractsignedbyyominame]
            , s.[llp_contracttype]
            , s.[llp_countofofferedtrucks]
            , s.[llp_countofofferedtrucks_date]
            , s.[llp_countofofferedtrucks_state]
            , s.[llp_countrieswerefilled]
            , s.[llp_createdonreport]
            , s.[llp_createsportoffer]
            , s.[llp_creditapplicationapproved]
            , s.[llp_creditapplicationcreated]
            , s.[llp_creditprecheckdone]
            , s.[llp_currency]
            , s.[llp_currency_base]
            , s.[llp_currentfleetmileage]
            , s.[llp_currentfleetmileagekmyear]
            , s.[llp_customeracceptedtheoffer]
            , s.[llp_customerbillingaddress]
            , s.[llp_customeremail]
            , s.[llp_customername]
            , s.[llp_customerphone]
            , s.[llp_customerswerefilled]
            , s.[llp_deliverycompleted]
            , s.[llp_deliverydate]
            , s.[llp_dout]
            , s.[llp_downpayment]
            , s.[llp_dppercent]
            , s.[llp_estimatedbodybuildingcompletiondate]
            , s.[llp_estimateddeliverydate]
            , s.[llp_estimatedorderdate]
            , s.[llp_externalfinancing]
            , s.[llp_financing2]
            , s.[llp_financingapproved]
            , s.[llp_financingconfirmed]
            , s.[llp_financinghidden]
            , s.[llp_financingnoreasonother]
            , s.[llp_financingnothereason]
            , s.[llp_financingopportunitycreated]
            , s.[llp_gdprcheck]
            , s.[llp_htmlspread]
            , s.[llp_indicativeofferaccepted]
            , s.[llp_indicativeofferwassaved]
            , s.[llp_informationdirectlyfromcustomer]
            , s.[llp_informationfromjusticecz]
            , s.[llp_insurance2]
            , s.[llp_insurancehidden]
            , s.[llp_insuranceprice]
            , s.[llp_insuranceprice_base]
            , s.[llp_insuranceproductsselection]
            , s.[llp_insuranceproductswereselected]
            , s.[llp_insurenceoffersend]
            , s.[llp_insurersselection]
            , s.[llp_insurerswereselected]
            , s.[llp_integrationsportguid]
            , s.[llp_km]
            , s.[llp_knownrivaloffer]
            , s.[llp_leasingasset]
            , s.[llp_lockguid]
            , s.[llp_lossratiopercent]
            , s.[llp_margin]
            , s.[llp_maxage]
            , s.[llp_maxmileage]
            , s.[llp_maxprice]
            , s.[llp_maxprice_base]
            , s.[llp_meetingwithbodybuilder]
            , s.[llp_netsuitechange]
            , s.[llp_newpurchasemileagekmyear]
            , s.[llp_newpurchusemileage]
            , s.[llp_notifydrivecoach]
            , s.[llp_numberofitemsofobjectspecification]
            , s.[llp_numberofitemsofobjectspecification_date]
            , s.[llp_numberofitemsofobjectspecification_state]
            , s.[llp_numberoftrucks]
            , s.[llp_numberoftrucksinfleet]
            , s.[llp_objectspecificationcompleted]
            , s.[llp_offeraccepted]
            , s.[llp_offeracceptedbycustomer]
            , s.[llp_opportunitycountries_count]
            , s.[llp_opportunitycountries_weightsum]
            , s.[llp_opportunitycustomer_count]
            , s.[llp_opportunitycustomer_weightsum]
            , s.[llp_opportunityforfinancingwaslost]
            , s.[llp_opportunitynumber]
            , s.[llp_opportunitypreferableinsurer_count]
            , s.[llp_opportunitytype]
            , s.[llp_opportunitytypeofinsurance_count]
            , s.[llp_parentalbuid]
            , s.[llp_parentalbuid_entitytype]
            , s.[llp_parentalbuidname]
            , s.[llp_pdicomplete]
            , s.[llp_peakinlastyear]
            , s.[llp_preferableinsurerid]
            , s.[llp_preferableinsurerid_entitytype]
            , s.[llp_preferableinsureridname]
            , s.[llp_preferedfinancialproduct]
            , s.[llp_primaryquoteid]
            , s.[llp_primaryquoteid_entitytype]
            , s.[llp_primaryquoteidname]
            , s.[llp_proposalsentdate]
            , s.[llp_proposedprice]
            , s.[llp_proposedprice_base]
            , s.[llp_recordapproved]
            , s.[llp_regno]
            , s.[llp_remark]
            , s.[llp_reservevehicle]
            , s.[llp_service]
            , s.[llp_servicesactivated]
            , s.[llp_sfcategory]
            , s.[llp_sourceopportunityid]
            , s.[llp_sourceopportunityid_entitytype]
            , s.[llp_sourceopportunityidname]
            , s.[llp_spreadapplicationapproved]
            , s.[llp_spreadapplicationmarginreason]
            , s.[llp_subjecttbfinanced]
            , s.[llp_tradein]
            , s.[llp_tradeinrequestcompleted]
            , s.[llp_trucktype]
            , s.[llp_typeofinsuranceproduct]
            , s.[llp_typeoftransport]
            , s.[llp_typeoftransportselection]
            , s.[llp_urljusticecz]
            , s.[llp_utreservationapprovalrequired]
            , s.[llp_utreservationapproverhiddenid]
            , s.[llp_utreservationapproverhiddenid_entitytype]
            , s.[llp_utreservationapproverhiddenidname]
            , s.[llp_utreservationapproverhiddenidyominame]
            , s.[llp_utsalespersonid]
            , s.[llp_utsalespersonid_entitytype]
            , s.[llp_utsalespersonidname]
            , s.[llp_utsalespersonidyominame]
            , s.[llp_vehicleid]
            , s.[llp_vehicleid_entitytype]
            , s.[llp_vehicleidname]
            , s.[llp_vehicleprice]
            , s.[llp_vehicleprice_base]
            , s.[llp_vehicleregistrationnumber]
            , s.[llp_vin]
            , s.[llp_virtualaccount]
            , s.[llp_weightsumcountriesissue]
            , s.[llp_weightsumcustomersissue]
            , s.[modifiedby]
            , s.[modifiedby_entitytype]
            , s.[modifiedbyname]
            , s.[modifiedbyyominame]
            , s.[modifiedon]
            , s.[modifiedonbehalfby]
            , s.[modifiedonbehalfby_entitytype]
            , s.[modifiedonbehalfbyname]
            , s.[modifiedonbehalfbyyominame]
            , s.[msdyn_forecastcategory]
            , s.[name]
            , s.[need]
            , s.[onholdtime]
            , s.[opportunityid]
            , s.[opportunityratingcode]
            , s.[originatingleadid]
            , s.[originatingleadid_entitytype]
            , s.[originatingleadidname]
            , s.[originatingleadidyominame]
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
            , s.[parentaccountid]
            , s.[parentaccountid_entitytype]
            , s.[parentaccountidname]
            , s.[parentaccountidyominame]
            , s.[parentcontactid]
            , s.[parentcontactid_entitytype]
            , s.[parentcontactidname]
            , s.[parentcontactidyominame]
            , s.[participatesinworkflow]
            , s.[presentfinalproposal]
            , s.[presentproposal]
            , s.[pricelevelid]
            , s.[pricelevelid_entitytype]
            , s.[pricelevelidname]
            , s.[pricingerrorcode]
            , s.[prioritycode]
            , s.[processid]
            , s.[proposedsolution]
            , s.[purchaseprocess]
            , s.[purchasetimeframe]
            , s.[pursuitdecision]
            , s.[qualificationcomments]
            , s.[quotecomments]
            , s.[resolvefeedback]
            , s.[salesstage]
            , s.[salesstagecode]
            , s.[schedulefollowup_prospect]
            , s.[schedulefollowup_qualify]
            , s.[scheduleproposalmeeting]
            , s.[sendthankyounote]
            , s.[SinkCreatedOn]
            , s.[SinkModifiedOn]
            , s.[slaid]
            , s.[slaid_entitytype]
            , s.[slainvokedid]
            , s.[slainvokedid_entitytype]
            , s.[slainvokedidname]
            , s.[slaname]
            , s.[stageid]
            , s.[statecode]
            , s.[statuscode]
            , s.[stepid]
            , s.[stepname]
            , s.[teamsfollowed]
            , s.[timeline]
            , s.[timespentbymeonemailandmeetings]
            , s.[timezoneruleversionnumber]
            , s.[totalamount]
            , s.[totalamount_base]
            , s.[totalamountlessfreight]
            , s.[totalamountlessfreight_base]
            , s.[totaldiscountamount]
            , s.[totaldiscountamount_base]
            , s.[totallineitemamount]
            , s.[totallineitemamount_base]
            , s.[totallineitemdiscountamount]
            , s.[totallineitemdiscountamount_base]
            , s.[totaltax]
            , s.[totaltax_base]
            , s.[transactioncurrencyid]
            , s.[transactioncurrencyid_entitytype]
            , s.[transactioncurrencyidname]
            , s.[traversedpath]
            , s.[utcconversiontimezonecode]
            , s.[versionnumber]
            , s.[wa_brandid]
            , s.[wa_brandid_entitytype]
            , s.[wa_brandidname]
            , s.[wa_externalid]
            , s.[wa_opportunitygroup]
            , s.[wa_opportunitygroup_entitytype]
            , s.[wa_opportunitygroupname]
            , s.[wa_opportunitysourceid]
            , s.[wa_opportunitysourceid_entitytype]
            , s.[wa_opportunitysourceidname]
            , s.[wa_productid]
            , s.[wa_productid_entitytype]
            , s.[wa_productidname]
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
    
    INSERT INTO [Vault].[CRMdboOpportunity] (
            [Id]
            , [accountid]
            , [accountid_entitytype]
            , [accountidname]
            , [accountidyominame]
            , [actualclosedate]
            , [actualvalue]
            , [actualvalue_base]
            , [budgetamount]
            , [budgetamount_base]
            , [budgetstatus]
            , [campaignid]
            , [campaignid_entitytype]
            , [campaignidname]
            , [captureproposalfeedback]
            , [closeprobability]
            , [completefinalproposal]
            , [completeinternalreview]
            , [confirminterest]
            , [contactid]
            , [contactid_entitytype]
            , [contactidname]
            , [contactidyominame]
            , [createdby]
            , [createdby_entitytype]
            , [createdbyname]
            , [createdbyyominame]
            , [createdon]
            , [createdonbehalfby]
            , [createdonbehalfby_entitytype]
            , [createdonbehalfbyname]
            , [createdonbehalfbyyominame]
            , [currentsituation]
            , [customerid]
            , [customerid_entitytype]
            , [customeridname]
            , [customeridtype]
            , [customeridyominame]
            , [customerneed]
            , [customerpainpoints]
            , [decisionmaker]
            , [description]
            , [developproposal]
            , [discountamount]
            , [discountamount_base]
            , [discountpercentage]
            , [emailaddress]
            , [estimatedclosedate]
            , [estimatedvalue]
            , [estimatedvalue_base]
            , [evaluatefit]
            , [exchangerate]
            , [filedebrief]
            , [finaldecisiondate]
            , [freightamount]
            , [freightamount_base]
            , [identifycompetitors]
            , [identifycustomercontacts]
            , [identifypursuitteam]
            , [importsequencenumber]
            , [initialcommunication]
            , [isprivate]
            , [isrevenuesystemcalculated]
            , [lastonholdtime]
            , [llp_add]
            , [llp_agreedhandoverdate]
            , [llp_alltrucksapprovedandaccepted]
            , [llp_approvalstatus]
            , [llp_assetprice]
            , [llp_assetprice_base]
            , [llp_automaticallycreatedsfopp]
            , [llp_automaticallycreatedsiopp]
            , [llp_averageoverdueinlast2years]
            , [llp_bodybuildingcontractsigned]
            , [llp_bodybuildingcoordinatedby]
            , [llp_bodybuildinggeneralsupplierid]
            , [llp_bodybuildinggeneralsupplierid_entitytype]
            , [llp_bodybuildinggeneralsupplieridname]
            , [llp_bodybuildinggeneralsupplieridyominame]
            , [llp_bodybuildinghandoverdate]
            , [llp_bodywork]
            , [llp_buofvehicleid]
            , [llp_buofvehicleid_entitytype]
            , [llp_buofvehicleidname]
            , [llp_cdd]
            , [llp_checkedofcustomerneeds]
            , [llp_competitors]
            , [llp_competitorsinsuraceother]
            , [llp_competitorsinsurance]
            , [llp_competitorsinsuranceselection]
            , [llp_competitorsleasingother]
            , [llp_competitorsselection]
            , [llp_contractlenght]
            , [llp_contractlengthmonth]
            , [llp_contractsigned]
            , [llp_contractsignedby]
            , [llp_contractsignedby_entitytype]
            , [llp_contractsignedbyname]
            , [llp_contractsignedbyon]
            , [llp_contractsignedbyyominame]
            , [llp_contracttype]
            , [llp_countofofferedtrucks]
            , [llp_countofofferedtrucks_date]
            , [llp_countofofferedtrucks_state]
            , [llp_countrieswerefilled]
            , [llp_createdonreport]
            , [llp_createsportoffer]
            , [llp_creditapplicationapproved]
            , [llp_creditapplicationcreated]
            , [llp_creditprecheckdone]
            , [llp_currency]
            , [llp_currency_base]
            , [llp_currentfleetmileage]
            , [llp_currentfleetmileagekmyear]
            , [llp_customeracceptedtheoffer]
            , [llp_customerbillingaddress]
            , [llp_customeremail]
            , [llp_customername]
            , [llp_customerphone]
            , [llp_customerswerefilled]
            , [llp_deliverycompleted]
            , [llp_deliverydate]
            , [llp_dout]
            , [llp_downpayment]
            , [llp_dppercent]
            , [llp_estimatedbodybuildingcompletiondate]
            , [llp_estimateddeliverydate]
            , [llp_estimatedorderdate]
            , [llp_externalfinancing]
            , [llp_financing2]
            , [llp_financingapproved]
            , [llp_financingconfirmed]
            , [llp_financinghidden]
            , [llp_financingnoreasonother]
            , [llp_financingnothereason]
            , [llp_financingopportunitycreated]
            , [llp_gdprcheck]
            , [llp_htmlspread]
            , [llp_indicativeofferaccepted]
            , [llp_indicativeofferwassaved]
            , [llp_informationdirectlyfromcustomer]
            , [llp_informationfromjusticecz]
            , [llp_insurance2]
            , [llp_insurancehidden]
            , [llp_insuranceprice]
            , [llp_insuranceprice_base]
            , [llp_insuranceproductsselection]
            , [llp_insuranceproductswereselected]
            , [llp_insurenceoffersend]
            , [llp_insurersselection]
            , [llp_insurerswereselected]
            , [llp_integrationsportguid]
            , [llp_km]
            , [llp_knownrivaloffer]
            , [llp_leasingasset]
            , [llp_lockguid]
            , [llp_lossratiopercent]
            , [llp_margin]
            , [llp_maxage]
            , [llp_maxmileage]
            , [llp_maxprice]
            , [llp_maxprice_base]
            , [llp_meetingwithbodybuilder]
            , [llp_netsuitechange]
            , [llp_newpurchasemileagekmyear]
            , [llp_newpurchusemileage]
            , [llp_notifydrivecoach]
            , [llp_numberofitemsofobjectspecification]
            , [llp_numberofitemsofobjectspecification_date]
            , [llp_numberofitemsofobjectspecification_state]
            , [llp_numberoftrucks]
            , [llp_numberoftrucksinfleet]
            , [llp_objectspecificationcompleted]
            , [llp_offeraccepted]
            , [llp_offeracceptedbycustomer]
            , [llp_opportunitycountries_count]
            , [llp_opportunitycountries_weightsum]
            , [llp_opportunitycustomer_count]
            , [llp_opportunitycustomer_weightsum]
            , [llp_opportunityforfinancingwaslost]
            , [llp_opportunitynumber]
            , [llp_opportunitypreferableinsurer_count]
            , [llp_opportunitytype]
            , [llp_opportunitytypeofinsurance_count]
            , [llp_parentalbuid]
            , [llp_parentalbuid_entitytype]
            , [llp_parentalbuidname]
            , [llp_pdicomplete]
            , [llp_peakinlastyear]
            , [llp_preferableinsurerid]
            , [llp_preferableinsurerid_entitytype]
            , [llp_preferableinsureridname]
            , [llp_preferedfinancialproduct]
            , [llp_primaryquoteid]
            , [llp_primaryquoteid_entitytype]
            , [llp_primaryquoteidname]
            , [llp_proposalsentdate]
            , [llp_proposedprice]
            , [llp_proposedprice_base]
            , [llp_recordapproved]
            , [llp_regno]
            , [llp_remark]
            , [llp_reservevehicle]
            , [llp_service]
            , [llp_servicesactivated]
            , [llp_sfcategory]
            , [llp_sourceopportunityid]
            , [llp_sourceopportunityid_entitytype]
            , [llp_sourceopportunityidname]
            , [llp_spreadapplicationapproved]
            , [llp_spreadapplicationmarginreason]
            , [llp_subjecttbfinanced]
            , [llp_tradein]
            , [llp_tradeinrequestcompleted]
            , [llp_trucktype]
            , [llp_typeofinsuranceproduct]
            , [llp_typeoftransport]
            , [llp_typeoftransportselection]
            , [llp_urljusticecz]
            , [llp_utreservationapprovalrequired]
            , [llp_utreservationapproverhiddenid]
            , [llp_utreservationapproverhiddenid_entitytype]
            , [llp_utreservationapproverhiddenidname]
            , [llp_utreservationapproverhiddenidyominame]
            , [llp_utsalespersonid]
            , [llp_utsalespersonid_entitytype]
            , [llp_utsalespersonidname]
            , [llp_utsalespersonidyominame]
            , [llp_vehicleid]
            , [llp_vehicleid_entitytype]
            , [llp_vehicleidname]
            , [llp_vehicleprice]
            , [llp_vehicleprice_base]
            , [llp_vehicleregistrationnumber]
            , [llp_vin]
            , [llp_virtualaccount]
            , [llp_weightsumcountriesissue]
            , [llp_weightsumcustomersissue]
            , [modifiedby]
            , [modifiedby_entitytype]
            , [modifiedbyname]
            , [modifiedbyyominame]
            , [modifiedon]
            , [modifiedonbehalfby]
            , [modifiedonbehalfby_entitytype]
            , [modifiedonbehalfbyname]
            , [modifiedonbehalfbyyominame]
            , [msdyn_forecastcategory]
            , [name]
            , [need]
            , [onholdtime]
            , [opportunityid]
            , [opportunityratingcode]
            , [originatingleadid]
            , [originatingleadid_entitytype]
            , [originatingleadidname]
            , [originatingleadidyominame]
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
            , [parentaccountid]
            , [parentaccountid_entitytype]
            , [parentaccountidname]
            , [parentaccountidyominame]
            , [parentcontactid]
            , [parentcontactid_entitytype]
            , [parentcontactidname]
            , [parentcontactidyominame]
            , [participatesinworkflow]
            , [presentfinalproposal]
            , [presentproposal]
            , [pricelevelid]
            , [pricelevelid_entitytype]
            , [pricelevelidname]
            , [pricingerrorcode]
            , [prioritycode]
            , [processid]
            , [proposedsolution]
            , [purchaseprocess]
            , [purchasetimeframe]
            , [pursuitdecision]
            , [qualificationcomments]
            , [quotecomments]
            , [resolvefeedback]
            , [salesstage]
            , [salesstagecode]
            , [schedulefollowup_prospect]
            , [schedulefollowup_qualify]
            , [scheduleproposalmeeting]
            , [sendthankyounote]
            , [SinkCreatedOn]
            , [SinkModifiedOn]
            , [slaid]
            , [slaid_entitytype]
            , [slainvokedid]
            , [slainvokedid_entitytype]
            , [slainvokedidname]
            , [slaname]
            , [stageid]
            , [statecode]
            , [statuscode]
            , [stepid]
            , [stepname]
            , [teamsfollowed]
            , [timeline]
            , [timespentbymeonemailandmeetings]
            , [timezoneruleversionnumber]
            , [totalamount]
            , [totalamount_base]
            , [totalamountlessfreight]
            , [totalamountlessfreight_base]
            , [totaldiscountamount]
            , [totaldiscountamount_base]
            , [totallineitemamount]
            , [totallineitemamount_base]
            , [totallineitemdiscountamount]
            , [totallineitemdiscountamount_base]
            , [totaltax]
            , [totaltax_base]
            , [transactioncurrencyid]
            , [transactioncurrencyid_entitytype]
            , [transactioncurrencyidname]
            , [traversedpath]
            , [utcconversiontimezonecode]
            , [versionnumber]
            , [wa_brandid]
            , [wa_brandid_entitytype]
            , [wa_brandidname]
            , [wa_externalid]
            , [wa_opportunitygroup]
            , [wa_opportunitygroup_entitytype]
            , [wa_opportunitygroupname]
            , [wa_opportunitysourceid]
            , [wa_opportunitysourceid_entitytype]
            , [wa_opportunitysourceidname]
            , [wa_productid]
            , [wa_productid_entitytype]
            , [wa_productidname]
            , [DataSourceId]
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
        
    ) 
    OUTPUT Inserted.ThreadLogUpdateId INTO @UpdateRowCounts
    SELECT

            s.[Id]
            , s.[accountid]
            , s.[accountid_entitytype]
            , s.[accountidname]
            , s.[accountidyominame]
            , s.[actualclosedate]
            , s.[actualvalue]
            , s.[actualvalue_base]
            , s.[budgetamount]
            , s.[budgetamount_base]
            , s.[budgetstatus]
            , s.[campaignid]
            , s.[campaignid_entitytype]
            , s.[campaignidname]
            , s.[captureproposalfeedback]
            , s.[closeprobability]
            , s.[completefinalproposal]
            , s.[completeinternalreview]
            , s.[confirminterest]
            , s.[contactid]
            , s.[contactid_entitytype]
            , s.[contactidname]
            , s.[contactidyominame]
            , s.[createdby]
            , s.[createdby_entitytype]
            , s.[createdbyname]
            , s.[createdbyyominame]
            , s.[createdon]
            , s.[createdonbehalfby]
            , s.[createdonbehalfby_entitytype]
            , s.[createdonbehalfbyname]
            , s.[createdonbehalfbyyominame]
            , s.[currentsituation]
            , s.[customerid]
            , s.[customerid_entitytype]
            , s.[customeridname]
            , s.[customeridtype]
            , s.[customeridyominame]
            , s.[customerneed]
            , s.[customerpainpoints]
            , s.[decisionmaker]
            , s.[description]
            , s.[developproposal]
            , s.[discountamount]
            , s.[discountamount_base]
            , s.[discountpercentage]
            , s.[emailaddress]
            , s.[estimatedclosedate]
            , s.[estimatedvalue]
            , s.[estimatedvalue_base]
            , s.[evaluatefit]
            , s.[exchangerate]
            , s.[filedebrief]
            , s.[finaldecisiondate]
            , s.[freightamount]
            , s.[freightamount_base]
            , s.[identifycompetitors]
            , s.[identifycustomercontacts]
            , s.[identifypursuitteam]
            , s.[importsequencenumber]
            , s.[initialcommunication]
            , s.[isprivate]
            , s.[isrevenuesystemcalculated]
            , s.[lastonholdtime]
            , s.[llp_add]
            , s.[llp_agreedhandoverdate]
            , s.[llp_alltrucksapprovedandaccepted]
            , s.[llp_approvalstatus]
            , s.[llp_assetprice]
            , s.[llp_assetprice_base]
            , s.[llp_automaticallycreatedsfopp]
            , s.[llp_automaticallycreatedsiopp]
            , s.[llp_averageoverdueinlast2years]
            , s.[llp_bodybuildingcontractsigned]
            , s.[llp_bodybuildingcoordinatedby]
            , s.[llp_bodybuildinggeneralsupplierid]
            , s.[llp_bodybuildinggeneralsupplierid_entitytype]
            , s.[llp_bodybuildinggeneralsupplieridname]
            , s.[llp_bodybuildinggeneralsupplieridyominame]
            , s.[llp_bodybuildinghandoverdate]
            , s.[llp_bodywork]
            , s.[llp_buofvehicleid]
            , s.[llp_buofvehicleid_entitytype]
            , s.[llp_buofvehicleidname]
            , s.[llp_cdd]
            , s.[llp_checkedofcustomerneeds]
            , s.[llp_competitors]
            , s.[llp_competitorsinsuraceother]
            , s.[llp_competitorsinsurance]
            , s.[llp_competitorsinsuranceselection]
            , s.[llp_competitorsleasingother]
            , s.[llp_competitorsselection]
            , s.[llp_contractlenght]
            , s.[llp_contractlengthmonth]
            , s.[llp_contractsigned]
            , s.[llp_contractsignedby]
            , s.[llp_contractsignedby_entitytype]
            , s.[llp_contractsignedbyname]
            , s.[llp_contractsignedbyon]
            , s.[llp_contractsignedbyyominame]
            , s.[llp_contracttype]
            , s.[llp_countofofferedtrucks]
            , s.[llp_countofofferedtrucks_date]
            , s.[llp_countofofferedtrucks_state]
            , s.[llp_countrieswerefilled]
            , s.[llp_createdonreport]
            , s.[llp_createsportoffer]
            , s.[llp_creditapplicationapproved]
            , s.[llp_creditapplicationcreated]
            , s.[llp_creditprecheckdone]
            , s.[llp_currency]
            , s.[llp_currency_base]
            , s.[llp_currentfleetmileage]
            , s.[llp_currentfleetmileagekmyear]
            , s.[llp_customeracceptedtheoffer]
            , s.[llp_customerbillingaddress]
            , s.[llp_customeremail]
            , s.[llp_customername]
            , s.[llp_customerphone]
            , s.[llp_customerswerefilled]
            , s.[llp_deliverycompleted]
            , s.[llp_deliverydate]
            , s.[llp_dout]
            , s.[llp_downpayment]
            , s.[llp_dppercent]
            , s.[llp_estimatedbodybuildingcompletiondate]
            , s.[llp_estimateddeliverydate]
            , s.[llp_estimatedorderdate]
            , s.[llp_externalfinancing]
            , s.[llp_financing2]
            , s.[llp_financingapproved]
            , s.[llp_financingconfirmed]
            , s.[llp_financinghidden]
            , s.[llp_financingnoreasonother]
            , s.[llp_financingnothereason]
            , s.[llp_financingopportunitycreated]
            , s.[llp_gdprcheck]
            , s.[llp_htmlspread]
            , s.[llp_indicativeofferaccepted]
            , s.[llp_indicativeofferwassaved]
            , s.[llp_informationdirectlyfromcustomer]
            , s.[llp_informationfromjusticecz]
            , s.[llp_insurance2]
            , s.[llp_insurancehidden]
            , s.[llp_insuranceprice]
            , s.[llp_insuranceprice_base]
            , s.[llp_insuranceproductsselection]
            , s.[llp_insuranceproductswereselected]
            , s.[llp_insurenceoffersend]
            , s.[llp_insurersselection]
            , s.[llp_insurerswereselected]
            , s.[llp_integrationsportguid]
            , s.[llp_km]
            , s.[llp_knownrivaloffer]
            , s.[llp_leasingasset]
            , s.[llp_lockguid]
            , s.[llp_lossratiopercent]
            , s.[llp_margin]
            , s.[llp_maxage]
            , s.[llp_maxmileage]
            , s.[llp_maxprice]
            , s.[llp_maxprice_base]
            , s.[llp_meetingwithbodybuilder]
            , s.[llp_netsuitechange]
            , s.[llp_newpurchasemileagekmyear]
            , s.[llp_newpurchusemileage]
            , s.[llp_notifydrivecoach]
            , s.[llp_numberofitemsofobjectspecification]
            , s.[llp_numberofitemsofobjectspecification_date]
            , s.[llp_numberofitemsofobjectspecification_state]
            , s.[llp_numberoftrucks]
            , s.[llp_numberoftrucksinfleet]
            , s.[llp_objectspecificationcompleted]
            , s.[llp_offeraccepted]
            , s.[llp_offeracceptedbycustomer]
            , s.[llp_opportunitycountries_count]
            , s.[llp_opportunitycountries_weightsum]
            , s.[llp_opportunitycustomer_count]
            , s.[llp_opportunitycustomer_weightsum]
            , s.[llp_opportunityforfinancingwaslost]
            , s.[llp_opportunitynumber]
            , s.[llp_opportunitypreferableinsurer_count]
            , s.[llp_opportunitytype]
            , s.[llp_opportunitytypeofinsurance_count]
            , s.[llp_parentalbuid]
            , s.[llp_parentalbuid_entitytype]
            , s.[llp_parentalbuidname]
            , s.[llp_pdicomplete]
            , s.[llp_peakinlastyear]
            , s.[llp_preferableinsurerid]
            , s.[llp_preferableinsurerid_entitytype]
            , s.[llp_preferableinsureridname]
            , s.[llp_preferedfinancialproduct]
            , s.[llp_primaryquoteid]
            , s.[llp_primaryquoteid_entitytype]
            , s.[llp_primaryquoteidname]
            , s.[llp_proposalsentdate]
            , s.[llp_proposedprice]
            , s.[llp_proposedprice_base]
            , s.[llp_recordapproved]
            , s.[llp_regno]
            , s.[llp_remark]
            , s.[llp_reservevehicle]
            , s.[llp_service]
            , s.[llp_servicesactivated]
            , s.[llp_sfcategory]
            , s.[llp_sourceopportunityid]
            , s.[llp_sourceopportunityid_entitytype]
            , s.[llp_sourceopportunityidname]
            , s.[llp_spreadapplicationapproved]
            , s.[llp_spreadapplicationmarginreason]
            , s.[llp_subjecttbfinanced]
            , s.[llp_tradein]
            , s.[llp_tradeinrequestcompleted]
            , s.[llp_trucktype]
            , s.[llp_typeofinsuranceproduct]
            , s.[llp_typeoftransport]
            , s.[llp_typeoftransportselection]
            , s.[llp_urljusticecz]
            , s.[llp_utreservationapprovalrequired]
            , s.[llp_utreservationapproverhiddenid]
            , s.[llp_utreservationapproverhiddenid_entitytype]
            , s.[llp_utreservationapproverhiddenidname]
            , s.[llp_utreservationapproverhiddenidyominame]
            , s.[llp_utsalespersonid]
            , s.[llp_utsalespersonid_entitytype]
            , s.[llp_utsalespersonidname]
            , s.[llp_utsalespersonidyominame]
            , s.[llp_vehicleid]
            , s.[llp_vehicleid_entitytype]
            , s.[llp_vehicleidname]
            , s.[llp_vehicleprice]
            , s.[llp_vehicleprice_base]
            , s.[llp_vehicleregistrationnumber]
            , s.[llp_vin]
            , s.[llp_virtualaccount]
            , s.[llp_weightsumcountriesissue]
            , s.[llp_weightsumcustomersissue]
            , s.[modifiedby]
            , s.[modifiedby_entitytype]
            , s.[modifiedbyname]
            , s.[modifiedbyyominame]
            , s.[modifiedon]
            , s.[modifiedonbehalfby]
            , s.[modifiedonbehalfby_entitytype]
            , s.[modifiedonbehalfbyname]
            , s.[modifiedonbehalfbyyominame]
            , s.[msdyn_forecastcategory]
            , s.[name]
            , s.[need]
            , s.[onholdtime]
            , s.[opportunityid]
            , s.[opportunityratingcode]
            , s.[originatingleadid]
            , s.[originatingleadid_entitytype]
            , s.[originatingleadidname]
            , s.[originatingleadidyominame]
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
            , s.[parentaccountid]
            , s.[parentaccountid_entitytype]
            , s.[parentaccountidname]
            , s.[parentaccountidyominame]
            , s.[parentcontactid]
            , s.[parentcontactid_entitytype]
            , s.[parentcontactidname]
            , s.[parentcontactidyominame]
            , s.[participatesinworkflow]
            , s.[presentfinalproposal]
            , s.[presentproposal]
            , s.[pricelevelid]
            , s.[pricelevelid_entitytype]
            , s.[pricelevelidname]
            , s.[pricingerrorcode]
            , s.[prioritycode]
            , s.[processid]
            , s.[proposedsolution]
            , s.[purchaseprocess]
            , s.[purchasetimeframe]
            , s.[pursuitdecision]
            , s.[qualificationcomments]
            , s.[quotecomments]
            , s.[resolvefeedback]
            , s.[salesstage]
            , s.[salesstagecode]
            , s.[schedulefollowup_prospect]
            , s.[schedulefollowup_qualify]
            , s.[scheduleproposalmeeting]
            , s.[sendthankyounote]
            , s.[SinkCreatedOn]
            , s.[SinkModifiedOn]
            , s.[slaid]
            , s.[slaid_entitytype]
            , s.[slainvokedid]
            , s.[slainvokedid_entitytype]
            , s.[slainvokedidname]
            , s.[slaname]
            , s.[stageid]
            , s.[statecode]
            , s.[statuscode]
            , s.[stepid]
            , s.[stepname]
            , s.[teamsfollowed]
            , s.[timeline]
            , s.[timespentbymeonemailandmeetings]
            , s.[timezoneruleversionnumber]
            , s.[totalamount]
            , s.[totalamount_base]
            , s.[totalamountlessfreight]
            , s.[totalamountlessfreight_base]
            , s.[totaldiscountamount]
            , s.[totaldiscountamount_base]
            , s.[totallineitemamount]
            , s.[totallineitemamount_base]
            , s.[totallineitemdiscountamount]
            , s.[totallineitemdiscountamount_base]
            , s.[totaltax]
            , s.[totaltax_base]
            , s.[transactioncurrencyid]
            , s.[transactioncurrencyid_entitytype]
            , s.[transactioncurrencyidname]
            , s.[traversedpath]
            , s.[utcconversiontimezonecode]
            , s.[versionnumber]
            , s.[wa_brandid]
            , s.[wa_brandid_entitytype]
            , s.[wa_brandidname]
            , s.[wa_externalid]
            , s.[wa_opportunitygroup]
            , s.[wa_opportunitygroup_entitytype]
            , s.[wa_opportunitygroupname]
            , s.[wa_opportunitysourceid]
            , s.[wa_opportunitysourceid_entitytype]
            , s.[wa_opportunitysourceidname]
            , s.[wa_productid]
            , s.[wa_productid_entitytype]
            , s.[wa_productidname]
            , s.[DataSourceId]
            , @ThreadLogId
            , -1
            , -1
            , N'U' -- update
    FROM Stage.CRMdboOpportunity AS s
    INNER JOIN Vault.CRMdboOpportunity AS v
        ON  s.[Id] = v.[Id] AND v.ThreadLogUpdateId = @ThreadLogId
    
    INSERT INTO [Vault].[CRMdboOpportunity] (
            [Id]
            , [accountid]
            , [accountid_entitytype]
            , [accountidname]
            , [accountidyominame]
            , [actualclosedate]
            , [actualvalue]
            , [actualvalue_base]
            , [budgetamount]
            , [budgetamount_base]
            , [budgetstatus]
            , [campaignid]
            , [campaignid_entitytype]
            , [campaignidname]
            , [captureproposalfeedback]
            , [closeprobability]
            , [completefinalproposal]
            , [completeinternalreview]
            , [confirminterest]
            , [contactid]
            , [contactid_entitytype]
            , [contactidname]
            , [contactidyominame]
            , [createdby]
            , [createdby_entitytype]
            , [createdbyname]
            , [createdbyyominame]
            , [createdon]
            , [createdonbehalfby]
            , [createdonbehalfby_entitytype]
            , [createdonbehalfbyname]
            , [createdonbehalfbyyominame]
            , [currentsituation]
            , [customerid]
            , [customerid_entitytype]
            , [customeridname]
            , [customeridtype]
            , [customeridyominame]
            , [customerneed]
            , [customerpainpoints]
            , [decisionmaker]
            , [description]
            , [developproposal]
            , [discountamount]
            , [discountamount_base]
            , [discountpercentage]
            , [emailaddress]
            , [estimatedclosedate]
            , [estimatedvalue]
            , [estimatedvalue_base]
            , [evaluatefit]
            , [exchangerate]
            , [filedebrief]
            , [finaldecisiondate]
            , [freightamount]
            , [freightamount_base]
            , [identifycompetitors]
            , [identifycustomercontacts]
            , [identifypursuitteam]
            , [importsequencenumber]
            , [initialcommunication]
            , [isprivate]
            , [isrevenuesystemcalculated]
            , [lastonholdtime]
            , [llp_add]
            , [llp_agreedhandoverdate]
            , [llp_alltrucksapprovedandaccepted]
            , [llp_approvalstatus]
            , [llp_assetprice]
            , [llp_assetprice_base]
            , [llp_automaticallycreatedsfopp]
            , [llp_automaticallycreatedsiopp]
            , [llp_averageoverdueinlast2years]
            , [llp_bodybuildingcontractsigned]
            , [llp_bodybuildingcoordinatedby]
            , [llp_bodybuildinggeneralsupplierid]
            , [llp_bodybuildinggeneralsupplierid_entitytype]
            , [llp_bodybuildinggeneralsupplieridname]
            , [llp_bodybuildinggeneralsupplieridyominame]
            , [llp_bodybuildinghandoverdate]
            , [llp_bodywork]
            , [llp_buofvehicleid]
            , [llp_buofvehicleid_entitytype]
            , [llp_buofvehicleidname]
            , [llp_cdd]
            , [llp_checkedofcustomerneeds]
            , [llp_competitors]
            , [llp_competitorsinsuraceother]
            , [llp_competitorsinsurance]
            , [llp_competitorsinsuranceselection]
            , [llp_competitorsleasingother]
            , [llp_competitorsselection]
            , [llp_contractlenght]
            , [llp_contractlengthmonth]
            , [llp_contractsigned]
            , [llp_contractsignedby]
            , [llp_contractsignedby_entitytype]
            , [llp_contractsignedbyname]
            , [llp_contractsignedbyon]
            , [llp_contractsignedbyyominame]
            , [llp_contracttype]
            , [llp_countofofferedtrucks]
            , [llp_countofofferedtrucks_date]
            , [llp_countofofferedtrucks_state]
            , [llp_countrieswerefilled]
            , [llp_createdonreport]
            , [llp_createsportoffer]
            , [llp_creditapplicationapproved]
            , [llp_creditapplicationcreated]
            , [llp_creditprecheckdone]
            , [llp_currency]
            , [llp_currency_base]
            , [llp_currentfleetmileage]
            , [llp_currentfleetmileagekmyear]
            , [llp_customeracceptedtheoffer]
            , [llp_customerbillingaddress]
            , [llp_customeremail]
            , [llp_customername]
            , [llp_customerphone]
            , [llp_customerswerefilled]
            , [llp_deliverycompleted]
            , [llp_deliverydate]
            , [llp_dout]
            , [llp_downpayment]
            , [llp_dppercent]
            , [llp_estimatedbodybuildingcompletiondate]
            , [llp_estimateddeliverydate]
            , [llp_estimatedorderdate]
            , [llp_externalfinancing]
            , [llp_financing2]
            , [llp_financingapproved]
            , [llp_financingconfirmed]
            , [llp_financinghidden]
            , [llp_financingnoreasonother]
            , [llp_financingnothereason]
            , [llp_financingopportunitycreated]
            , [llp_gdprcheck]
            , [llp_htmlspread]
            , [llp_indicativeofferaccepted]
            , [llp_indicativeofferwassaved]
            , [llp_informationdirectlyfromcustomer]
            , [llp_informationfromjusticecz]
            , [llp_insurance2]
            , [llp_insurancehidden]
            , [llp_insuranceprice]
            , [llp_insuranceprice_base]
            , [llp_insuranceproductsselection]
            , [llp_insuranceproductswereselected]
            , [llp_insurenceoffersend]
            , [llp_insurersselection]
            , [llp_insurerswereselected]
            , [llp_integrationsportguid]
            , [llp_km]
            , [llp_knownrivaloffer]
            , [llp_leasingasset]
            , [llp_lockguid]
            , [llp_lossratiopercent]
            , [llp_margin]
            , [llp_maxage]
            , [llp_maxmileage]
            , [llp_maxprice]
            , [llp_maxprice_base]
            , [llp_meetingwithbodybuilder]
            , [llp_netsuitechange]
            , [llp_newpurchasemileagekmyear]
            , [llp_newpurchusemileage]
            , [llp_notifydrivecoach]
            , [llp_numberofitemsofobjectspecification]
            , [llp_numberofitemsofobjectspecification_date]
            , [llp_numberofitemsofobjectspecification_state]
            , [llp_numberoftrucks]
            , [llp_numberoftrucksinfleet]
            , [llp_objectspecificationcompleted]
            , [llp_offeraccepted]
            , [llp_offeracceptedbycustomer]
            , [llp_opportunitycountries_count]
            , [llp_opportunitycountries_weightsum]
            , [llp_opportunitycustomer_count]
            , [llp_opportunitycustomer_weightsum]
            , [llp_opportunityforfinancingwaslost]
            , [llp_opportunitynumber]
            , [llp_opportunitypreferableinsurer_count]
            , [llp_opportunitytype]
            , [llp_opportunitytypeofinsurance_count]
            , [llp_parentalbuid]
            , [llp_parentalbuid_entitytype]
            , [llp_parentalbuidname]
            , [llp_pdicomplete]
            , [llp_peakinlastyear]
            , [llp_preferableinsurerid]
            , [llp_preferableinsurerid_entitytype]
            , [llp_preferableinsureridname]
            , [llp_preferedfinancialproduct]
            , [llp_primaryquoteid]
            , [llp_primaryquoteid_entitytype]
            , [llp_primaryquoteidname]
            , [llp_proposalsentdate]
            , [llp_proposedprice]
            , [llp_proposedprice_base]
            , [llp_recordapproved]
            , [llp_regno]
            , [llp_remark]
            , [llp_reservevehicle]
            , [llp_service]
            , [llp_servicesactivated]
            , [llp_sfcategory]
            , [llp_sourceopportunityid]
            , [llp_sourceopportunityid_entitytype]
            , [llp_sourceopportunityidname]
            , [llp_spreadapplicationapproved]
            , [llp_spreadapplicationmarginreason]
            , [llp_subjecttbfinanced]
            , [llp_tradein]
            , [llp_tradeinrequestcompleted]
            , [llp_trucktype]
            , [llp_typeofinsuranceproduct]
            , [llp_typeoftransport]
            , [llp_typeoftransportselection]
            , [llp_urljusticecz]
            , [llp_utreservationapprovalrequired]
            , [llp_utreservationapproverhiddenid]
            , [llp_utreservationapproverhiddenid_entitytype]
            , [llp_utreservationapproverhiddenidname]
            , [llp_utreservationapproverhiddenidyominame]
            , [llp_utsalespersonid]
            , [llp_utsalespersonid_entitytype]
            , [llp_utsalespersonidname]
            , [llp_utsalespersonidyominame]
            , [llp_vehicleid]
            , [llp_vehicleid_entitytype]
            , [llp_vehicleidname]
            , [llp_vehicleprice]
            , [llp_vehicleprice_base]
            , [llp_vehicleregistrationnumber]
            , [llp_vin]
            , [llp_virtualaccount]
            , [llp_weightsumcountriesissue]
            , [llp_weightsumcustomersissue]
            , [modifiedby]
            , [modifiedby_entitytype]
            , [modifiedbyname]
            , [modifiedbyyominame]
            , [modifiedon]
            , [modifiedonbehalfby]
            , [modifiedonbehalfby_entitytype]
            , [modifiedonbehalfbyname]
            , [modifiedonbehalfbyyominame]
            , [msdyn_forecastcategory]
            , [name]
            , [need]
            , [onholdtime]
            , [opportunityid]
            , [opportunityratingcode]
            , [originatingleadid]
            , [originatingleadid_entitytype]
            , [originatingleadidname]
            , [originatingleadidyominame]
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
            , [parentaccountid]
            , [parentaccountid_entitytype]
            , [parentaccountidname]
            , [parentaccountidyominame]
            , [parentcontactid]
            , [parentcontactid_entitytype]
            , [parentcontactidname]
            , [parentcontactidyominame]
            , [participatesinworkflow]
            , [presentfinalproposal]
            , [presentproposal]
            , [pricelevelid]
            , [pricelevelid_entitytype]
            , [pricelevelidname]
            , [pricingerrorcode]
            , [prioritycode]
            , [processid]
            , [proposedsolution]
            , [purchaseprocess]
            , [purchasetimeframe]
            , [pursuitdecision]
            , [qualificationcomments]
            , [quotecomments]
            , [resolvefeedback]
            , [salesstage]
            , [salesstagecode]
            , [schedulefollowup_prospect]
            , [schedulefollowup_qualify]
            , [scheduleproposalmeeting]
            , [sendthankyounote]
            , [SinkCreatedOn]
            , [SinkModifiedOn]
            , [slaid]
            , [slaid_entitytype]
            , [slainvokedid]
            , [slainvokedid_entitytype]
            , [slainvokedidname]
            , [slaname]
            , [stageid]
            , [statecode]
            , [statuscode]
            , [stepid]
            , [stepname]
            , [teamsfollowed]
            , [timeline]
            , [timespentbymeonemailandmeetings]
            , [timezoneruleversionnumber]
            , [totalamount]
            , [totalamount_base]
            , [totalamountlessfreight]
            , [totalamountlessfreight_base]
            , [totaldiscountamount]
            , [totaldiscountamount_base]
            , [totallineitemamount]
            , [totallineitemamount_base]
            , [totallineitemdiscountamount]
            , [totallineitemdiscountamount_base]
            , [totaltax]
            , [totaltax_base]
            , [transactioncurrencyid]
            , [transactioncurrencyid_entitytype]
            , [transactioncurrencyidname]
            , [traversedpath]
            , [utcconversiontimezonecode]
            , [versionnumber]
            , [wa_brandid]
            , [wa_brandid_entitytype]
            , [wa_brandidname]
            , [wa_externalid]
            , [wa_opportunitygroup]
            , [wa_opportunitygroup_entitytype]
            , [wa_opportunitygroupname]
            , [wa_opportunitysourceid]
            , [wa_opportunitysourceid_entitytype]
            , [wa_opportunitysourceidname]
            , [wa_productid]
            , [wa_productid_entitytype]
            , [wa_productidname]
            , [DataSourceId]
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
            
    ) 
    OUTPUT Inserted.ThreadLogDeleteId INTO @DeleteRowCounts
    SELECT
            v.[Id]
            , v.[accountid]
            , v.[accountid_entitytype]
            , v.[accountidname]
            , v.[accountidyominame]
            , v.[actualclosedate]
            , v.[actualvalue]
            , v.[actualvalue_base]
            , v.[budgetamount]
            , v.[budgetamount_base]
            , v.[budgetstatus]
            , v.[campaignid]
            , v.[campaignid_entitytype]
            , v.[campaignidname]
            , v.[captureproposalfeedback]
            , v.[closeprobability]
            , v.[completefinalproposal]
            , v.[completeinternalreview]
            , v.[confirminterest]
            , v.[contactid]
            , v.[contactid_entitytype]
            , v.[contactidname]
            , v.[contactidyominame]
            , v.[createdby]
            , v.[createdby_entitytype]
            , v.[createdbyname]
            , v.[createdbyyominame]
            , v.[createdon]
            , v.[createdonbehalfby]
            , v.[createdonbehalfby_entitytype]
            , v.[createdonbehalfbyname]
            , v.[createdonbehalfbyyominame]
            , v.[currentsituation]
            , v.[customerid]
            , v.[customerid_entitytype]
            , v.[customeridname]
            , v.[customeridtype]
            , v.[customeridyominame]
            , v.[customerneed]
            , v.[customerpainpoints]
            , v.[decisionmaker]
            , v.[description]
            , v.[developproposal]
            , v.[discountamount]
            , v.[discountamount_base]
            , v.[discountpercentage]
            , v.[emailaddress]
            , v.[estimatedclosedate]
            , v.[estimatedvalue]
            , v.[estimatedvalue_base]
            , v.[evaluatefit]
            , v.[exchangerate]
            , v.[filedebrief]
            , v.[finaldecisiondate]
            , v.[freightamount]
            , v.[freightamount_base]
            , v.[identifycompetitors]
            , v.[identifycustomercontacts]
            , v.[identifypursuitteam]
            , v.[importsequencenumber]
            , v.[initialcommunication]
            , v.[isprivate]
            , v.[isrevenuesystemcalculated]
            , v.[lastonholdtime]
            , v.[llp_add]
            , v.[llp_agreedhandoverdate]
            , v.[llp_alltrucksapprovedandaccepted]
            , v.[llp_approvalstatus]
            , v.[llp_assetprice]
            , v.[llp_assetprice_base]
            , v.[llp_automaticallycreatedsfopp]
            , v.[llp_automaticallycreatedsiopp]
            , v.[llp_averageoverdueinlast2years]
            , v.[llp_bodybuildingcontractsigned]
            , v.[llp_bodybuildingcoordinatedby]
            , v.[llp_bodybuildinggeneralsupplierid]
            , v.[llp_bodybuildinggeneralsupplierid_entitytype]
            , v.[llp_bodybuildinggeneralsupplieridname]
            , v.[llp_bodybuildinggeneralsupplieridyominame]
            , v.[llp_bodybuildinghandoverdate]
            , v.[llp_bodywork]
            , v.[llp_buofvehicleid]
            , v.[llp_buofvehicleid_entitytype]
            , v.[llp_buofvehicleidname]
            , v.[llp_cdd]
            , v.[llp_checkedofcustomerneeds]
            , v.[llp_competitors]
            , v.[llp_competitorsinsuraceother]
            , v.[llp_competitorsinsurance]
            , v.[llp_competitorsinsuranceselection]
            , v.[llp_competitorsleasingother]
            , v.[llp_competitorsselection]
            , v.[llp_contractlenght]
            , v.[llp_contractlengthmonth]
            , v.[llp_contractsigned]
            , v.[llp_contractsignedby]
            , v.[llp_contractsignedby_entitytype]
            , v.[llp_contractsignedbyname]
            , v.[llp_contractsignedbyon]
            , v.[llp_contractsignedbyyominame]
            , v.[llp_contracttype]
            , v.[llp_countofofferedtrucks]
            , v.[llp_countofofferedtrucks_date]
            , v.[llp_countofofferedtrucks_state]
            , v.[llp_countrieswerefilled]
            , v.[llp_createdonreport]
            , v.[llp_createsportoffer]
            , v.[llp_creditapplicationapproved]
            , v.[llp_creditapplicationcreated]
            , v.[llp_creditprecheckdone]
            , v.[llp_currency]
            , v.[llp_currency_base]
            , v.[llp_currentfleetmileage]
            , v.[llp_currentfleetmileagekmyear]
            , v.[llp_customeracceptedtheoffer]
            , v.[llp_customerbillingaddress]
            , v.[llp_customeremail]
            , v.[llp_customername]
            , v.[llp_customerphone]
            , v.[llp_customerswerefilled]
            , v.[llp_deliverycompleted]
            , v.[llp_deliverydate]
            , v.[llp_dout]
            , v.[llp_downpayment]
            , v.[llp_dppercent]
            , v.[llp_estimatedbodybuildingcompletiondate]
            , v.[llp_estimateddeliverydate]
            , v.[llp_estimatedorderdate]
            , v.[llp_externalfinancing]
            , v.[llp_financing2]
            , v.[llp_financingapproved]
            , v.[llp_financingconfirmed]
            , v.[llp_financinghidden]
            , v.[llp_financingnoreasonother]
            , v.[llp_financingnothereason]
            , v.[llp_financingopportunitycreated]
            , v.[llp_gdprcheck]
            , v.[llp_htmlspread]
            , v.[llp_indicativeofferaccepted]
            , v.[llp_indicativeofferwassaved]
            , v.[llp_informationdirectlyfromcustomer]
            , v.[llp_informationfromjusticecz]
            , v.[llp_insurance2]
            , v.[llp_insurancehidden]
            , v.[llp_insuranceprice]
            , v.[llp_insuranceprice_base]
            , v.[llp_insuranceproductsselection]
            , v.[llp_insuranceproductswereselected]
            , v.[llp_insurenceoffersend]
            , v.[llp_insurersselection]
            , v.[llp_insurerswereselected]
            , v.[llp_integrationsportguid]
            , v.[llp_km]
            , v.[llp_knownrivaloffer]
            , v.[llp_leasingasset]
            , v.[llp_lockguid]
            , v.[llp_lossratiopercent]
            , v.[llp_margin]
            , v.[llp_maxage]
            , v.[llp_maxmileage]
            , v.[llp_maxprice]
            , v.[llp_maxprice_base]
            , v.[llp_meetingwithbodybuilder]
            , v.[llp_netsuitechange]
            , v.[llp_newpurchasemileagekmyear]
            , v.[llp_newpurchusemileage]
            , v.[llp_notifydrivecoach]
            , v.[llp_numberofitemsofobjectspecification]
            , v.[llp_numberofitemsofobjectspecification_date]
            , v.[llp_numberofitemsofobjectspecification_state]
            , v.[llp_numberoftrucks]
            , v.[llp_numberoftrucksinfleet]
            , v.[llp_objectspecificationcompleted]
            , v.[llp_offeraccepted]
            , v.[llp_offeracceptedbycustomer]
            , v.[llp_opportunitycountries_count]
            , v.[llp_opportunitycountries_weightsum]
            , v.[llp_opportunitycustomer_count]
            , v.[llp_opportunitycustomer_weightsum]
            , v.[llp_opportunityforfinancingwaslost]
            , v.[llp_opportunitynumber]
            , v.[llp_opportunitypreferableinsurer_count]
            , v.[llp_opportunitytype]
            , v.[llp_opportunitytypeofinsurance_count]
            , v.[llp_parentalbuid]
            , v.[llp_parentalbuid_entitytype]
            , v.[llp_parentalbuidname]
            , v.[llp_pdicomplete]
            , v.[llp_peakinlastyear]
            , v.[llp_preferableinsurerid]
            , v.[llp_preferableinsurerid_entitytype]
            , v.[llp_preferableinsureridname]
            , v.[llp_preferedfinancialproduct]
            , v.[llp_primaryquoteid]
            , v.[llp_primaryquoteid_entitytype]
            , v.[llp_primaryquoteidname]
            , v.[llp_proposalsentdate]
            , v.[llp_proposedprice]
            , v.[llp_proposedprice_base]
            , v.[llp_recordapproved]
            , v.[llp_regno]
            , v.[llp_remark]
            , v.[llp_reservevehicle]
            , v.[llp_service]
            , v.[llp_servicesactivated]
            , v.[llp_sfcategory]
            , v.[llp_sourceopportunityid]
            , v.[llp_sourceopportunityid_entitytype]
            , v.[llp_sourceopportunityidname]
            , v.[llp_spreadapplicationapproved]
            , v.[llp_spreadapplicationmarginreason]
            , v.[llp_subjecttbfinanced]
            , v.[llp_tradein]
            , v.[llp_tradeinrequestcompleted]
            , v.[llp_trucktype]
            , v.[llp_typeofinsuranceproduct]
            , v.[llp_typeoftransport]
            , v.[llp_typeoftransportselection]
            , v.[llp_urljusticecz]
            , v.[llp_utreservationapprovalrequired]
            , v.[llp_utreservationapproverhiddenid]
            , v.[llp_utreservationapproverhiddenid_entitytype]
            , v.[llp_utreservationapproverhiddenidname]
            , v.[llp_utreservationapproverhiddenidyominame]
            , v.[llp_utsalespersonid]
            , v.[llp_utsalespersonid_entitytype]
            , v.[llp_utsalespersonidname]
            , v.[llp_utsalespersonidyominame]
            , v.[llp_vehicleid]
            , v.[llp_vehicleid_entitytype]
            , v.[llp_vehicleidname]
            , v.[llp_vehicleprice]
            , v.[llp_vehicleprice_base]
            , v.[llp_vehicleregistrationnumber]
            , v.[llp_vin]
            , v.[llp_virtualaccount]
            , v.[llp_weightsumcountriesissue]
            , v.[llp_weightsumcustomersissue]
            , v.[modifiedby]
            , v.[modifiedby_entitytype]
            , v.[modifiedbyname]
            , v.[modifiedbyyominame]
            , v.[modifiedon]
            , v.[modifiedonbehalfby]
            , v.[modifiedonbehalfby_entitytype]
            , v.[modifiedonbehalfbyname]
            , v.[modifiedonbehalfbyyominame]
            , v.[msdyn_forecastcategory]
            , v.[name]
            , v.[need]
            , v.[onholdtime]
            , v.[opportunityid]
            , v.[opportunityratingcode]
            , v.[originatingleadid]
            , v.[originatingleadid_entitytype]
            , v.[originatingleadidname]
            , v.[originatingleadidyominame]
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
            , v.[parentaccountid]
            , v.[parentaccountid_entitytype]
            , v.[parentaccountidname]
            , v.[parentaccountidyominame]
            , v.[parentcontactid]
            , v.[parentcontactid_entitytype]
            , v.[parentcontactidname]
            , v.[parentcontactidyominame]
            , v.[participatesinworkflow]
            , v.[presentfinalproposal]
            , v.[presentproposal]
            , v.[pricelevelid]
            , v.[pricelevelid_entitytype]
            , v.[pricelevelidname]
            , v.[pricingerrorcode]
            , v.[prioritycode]
            , v.[processid]
            , v.[proposedsolution]
            , v.[purchaseprocess]
            , v.[purchasetimeframe]
            , v.[pursuitdecision]
            , v.[qualificationcomments]
            , v.[quotecomments]
            , v.[resolvefeedback]
            , v.[salesstage]
            , v.[salesstagecode]
            , v.[schedulefollowup_prospect]
            , v.[schedulefollowup_qualify]
            , v.[scheduleproposalmeeting]
            , v.[sendthankyounote]
            , v.[SinkCreatedOn]
            , v.[SinkModifiedOn]
            , v.[slaid]
            , v.[slaid_entitytype]
            , v.[slainvokedid]
            , v.[slainvokedid_entitytype]
            , v.[slainvokedidname]
            , v.[slaname]
            , v.[stageid]
            , v.[statecode]
            , v.[statuscode]
            , v.[stepid]
            , v.[stepname]
            , v.[teamsfollowed]
            , v.[timeline]
            , v.[timespentbymeonemailandmeetings]
            , v.[timezoneruleversionnumber]
            , v.[totalamount]
            , v.[totalamount_base]
            , v.[totalamountlessfreight]
            , v.[totalamountlessfreight_base]
            , v.[totaldiscountamount]
            , v.[totaldiscountamount_base]
            , v.[totallineitemamount]
            , v.[totallineitemamount_base]
            , v.[totallineitemdiscountamount]
            , v.[totallineitemdiscountamount_base]
            , v.[totaltax]
            , v.[totaltax_base]
            , v.[transactioncurrencyid]
            , v.[transactioncurrencyid_entitytype]
            , v.[transactioncurrencyidname]
            , v.[traversedpath]
            , v.[utcconversiontimezonecode]
            , v.[versionnumber]
            , v.[wa_brandid]
            , v.[wa_brandid_entitytype]
            , v.[wa_brandidname]
            , v.[wa_externalid]
            , v.[wa_opportunitygroup]
            , v.[wa_opportunitygroup_entitytype]
            , v.[wa_opportunitygroupname]
            , v.[wa_opportunitysourceid]
            , v.[wa_opportunitysourceid_entitytype]
            , v.[wa_opportunitysourceidname]
            , v.[wa_productid]
            , v.[wa_productid_entitytype]
            , v.[wa_productidname]
            , v.[DataSourceId]
            , @ThreadLogId
            , -1
            , -1
            , N'D' -- update
    FROM Vault.CRMdboOpportunity AS v
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
                , TableFinalRowCount = (SELECT COUNT(*) FROM [Vault].[CRMdboOpportunity] WITH (NOLOCK))
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
