Stored Procedure Vault.uspLoadCERTdboOrders {#spVaultuspLoadCERTdboOrders}
-------------------------------------------

Definition of Stored procedure:

``` {.sql}
CREATE PROCEDURE [Vault].[uspLoadCERTdboOrders] 
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
            SET TableInitialRowCount = (SELECT COUNT(*) FROM [Vault].[CERTdboOrders] WITH (NOLOCK))
        WHERE ThreadLogId = @ThreadLogId;

            BEGIN TRANSACTION;

    
        MERGE INTO [Vault].[CERTdboOrders] AS v
        USING [Stage].[CERTdboOrders] AS s
            ON ( s.[IDD] = v.[IDD]AND s.[DataSourceId] = v.[DataSourceId]
     AND v.[ThreadLogDeleteId] = -1 AND v.[ThreadLogUpdateId] = -1 AND v.[ChangeOperation] <> N'D'
    )

        WHEN MATCHED AND
            (
            v.[AccrualsDescrDIS] <> s.[AccrualsDescrDIS]
            OR (v.[AccrualsDescrDIS] IS NULL AND s.[AccrualsDescrDIS] IS NOT NULL)
        OR (v.[AccrualsDescrDIS] IS NOT NULL AND s.[AccrualsDescrDIS] IS NULL)
        OR v.[AccrualsDIS] <> s.[AccrualsDIS]
            OR (v.[AccrualsDIS] IS NULL AND s.[AccrualsDIS] IS NOT NULL)
        OR (v.[AccrualsDIS] IS NOT NULL AND s.[AccrualsDIS] IS NULL)
        OR v.[ActualDealerDate] <> s.[ActualDealerDate]
            OR (v.[ActualDealerDate] IS NULL AND s.[ActualDealerDate] IS NOT NULL)
        OR (v.[ActualDealerDate] IS NOT NULL AND s.[ActualDealerDate] IS NULL)
        OR v.[AdvancePayment] <> s.[AdvancePayment]
            OR (v.[AdvancePayment] IS NULL AND s.[AdvancePayment] IS NOT NULL)
        OR (v.[AdvancePayment] IS NOT NULL AND s.[AdvancePayment] IS NULL)
        OR v.[BodyCategory] <> s.[BodyCategory]
            OR (v.[BodyCategory] IS NULL AND s.[BodyCategory] IS NOT NULL)
        OR (v.[BodyCategory] IS NOT NULL AND s.[BodyCategory] IS NULL)
        OR v.[BodyColour] <> s.[BodyColour]
            OR (v.[BodyColour] IS NULL AND s.[BodyColour] IS NOT NULL)
        OR (v.[BodyColour] IS NOT NULL AND s.[BodyColour] IS NULL)
        OR v.[BodyInvDate] <> s.[BodyInvDate]
            OR (v.[BodyInvDate] IS NULL AND s.[BodyInvDate] IS NOT NULL)
        OR (v.[BodyInvDate] IS NOT NULL AND s.[BodyInvDate] IS NULL)
        OR v.[BodyPrice] <> s.[BodyPrice]
            OR (v.[BodyPrice] IS NULL AND s.[BodyPrice] IS NOT NULL)
        OR (v.[BodyPrice] IS NOT NULL AND s.[BodyPrice] IS NULL)
        OR v.[BodyReInvoiceNr] <> s.[BodyReInvoiceNr]
            OR (v.[BodyReInvoiceNr] IS NULL AND s.[BodyReInvoiceNr] IS NOT NULL)
        OR (v.[BodyReInvoiceNr] IS NOT NULL AND s.[BodyReInvoiceNr] IS NULL)
        OR v.[BodyReivoicingDate] <> s.[BodyReivoicingDate]
            OR (v.[BodyReivoicingDate] IS NULL AND s.[BodyReivoicingDate] IS NOT NULL)
        OR (v.[BodyReivoicingDate] IS NOT NULL AND s.[BodyReivoicingDate] IS NULL)
        OR v.[BodyWarantyMonthNr] <> s.[BodyWarantyMonthNr]
            OR (v.[BodyWarantyMonthNr] IS NULL AND s.[BodyWarantyMonthNr] IS NOT NULL)
        OR (v.[BodyWarantyMonthNr] IS NOT NULL AND s.[BodyWarantyMonthNr] IS NULL)
        OR v.[BodyWorkDescription] <> s.[BodyWorkDescription]
            OR (v.[BodyWorkDescription] IS NULL AND s.[BodyWorkDescription] IS NOT NULL)
        OR (v.[BodyWorkDescription] IS NOT NULL AND s.[BodyWorkDescription] IS NULL)
        OR v.[CancelationMoment] <> s.[CancelationMoment]
            OR (v.[CancelationMoment] IS NULL AND s.[CancelationMoment] IS NOT NULL)
        OR (v.[CancelationMoment] IS NOT NULL AND s.[CancelationMoment] IS NULL)
        OR v.[CanceledDealsHistory] <> s.[CanceledDealsHistory]
            OR (v.[CanceledDealsHistory] IS NULL AND s.[CanceledDealsHistory] IS NOT NULL)
        OR (v.[CanceledDealsHistory] IS NOT NULL AND s.[CanceledDealsHistory] IS NULL)
        OR v.[CASTspecifPackage] <> s.[CASTspecifPackage]
            OR (v.[CASTspecifPackage] IS NULL AND s.[CASTspecifPackage] IS NOT NULL)
        OR (v.[CASTspecifPackage] IS NOT NULL AND s.[CASTspecifPackage] IS NULL)
        OR v.[CDD2] <> s.[CDD2]
            OR (v.[CDD2] IS NULL AND s.[CDD2] IS NOT NULL)
        OR (v.[CDD2] IS NOT NULL AND s.[CDD2] IS NULL)
        OR v.[ConfirmedDelDealerDate] <> s.[ConfirmedDelDealerDate]
            OR (v.[ConfirmedDelDealerDate] IS NULL AND s.[ConfirmedDelDealerDate] IS NOT NULL)
        OR (v.[ConfirmedDelDealerDate] IS NOT NULL AND s.[ConfirmedDelDealerDate] IS NULL)
        OR v.[ContractedInOrder] <> s.[ContractedInOrder]
            OR (v.[ContractedInOrder] IS NULL AND s.[ContractedInOrder] IS NOT NULL)
        OR (v.[ContractedInOrder] IS NOT NULL AND s.[ContractedInOrder] IS NULL)
        OR v.[ContractNumber] <> s.[ContractNumber]
            OR (v.[ContractNumber] IS NULL AND s.[ContractNumber] IS NOT NULL)
        OR (v.[ContractNumber] IS NOT NULL AND s.[ContractNumber] IS NULL)
        OR v.[Country] <> s.[Country]
            OR (v.[Country] IS NULL AND s.[Country] IS NOT NULL)
        OR (v.[Country] IS NOT NULL AND s.[Country] IS NULL)
        OR v.[CountryToCountryBodyPrice] <> s.[CountryToCountryBodyPrice]
            OR (v.[CountryToCountryBodyPrice] IS NULL AND s.[CountryToCountryBodyPrice] IS NOT NULL)
        OR (v.[CountryToCountryBodyPrice] IS NOT NULL AND s.[CountryToCountryBodyPrice] IS NULL)
        OR v.[CountryToCountryInvoiceDay] <> s.[CountryToCountryInvoiceDay]
            OR (v.[CountryToCountryInvoiceDay] IS NULL AND s.[CountryToCountryInvoiceDay] IS NOT NULL)
        OR (v.[CountryToCountryInvoiceDay] IS NOT NULL AND s.[CountryToCountryInvoiceDay] IS NULL)
        OR v.[CountryToCountryInvoiceNr] <> s.[CountryToCountryInvoiceNr]
            OR (v.[CountryToCountryInvoiceNr] IS NULL AND s.[CountryToCountryInvoiceNr] IS NOT NULL)
        OR (v.[CountryToCountryInvoiceNr] IS NOT NULL AND s.[CountryToCountryInvoiceNr] IS NULL)
        OR v.[CountryToCountryInvoicePrice] <> s.[CountryToCountryInvoicePrice]
            OR (v.[CountryToCountryInvoicePrice] IS NULL AND s.[CountryToCountryInvoicePrice] IS NOT NULL)
        OR (v.[CountryToCountryInvoicePrice] IS NOT NULL AND s.[CountryToCountryInvoicePrice] IS NULL)
        OR v.[CountryToCountryInvoiceRequestSendDate] <> s.[CountryToCountryInvoiceRequestSendDate]
            OR (v.[CountryToCountryInvoiceRequestSendDate] IS NULL AND s.[CountryToCountryInvoiceRequestSendDate] IS NOT NULL)
        OR (v.[CountryToCountryInvoiceRequestSendDate] IS NOT NULL AND s.[CountryToCountryInvoiceRequestSendDate] IS NULL)
        OR v.[CountryToCountryInvoiceWay] <> s.[CountryToCountryInvoiceWay]
            OR (v.[CountryToCountryInvoiceWay] IS NULL AND s.[CountryToCountryInvoiceWay] IS NOT NULL)
        OR (v.[CountryToCountryInvoiceWay] IS NOT NULL AND s.[CountryToCountryInvoiceWay] IS NULL)
        OR v.[CreditAmount] <> s.[CreditAmount]
            OR (v.[CreditAmount] IS NULL AND s.[CreditAmount] IS NOT NULL)
        OR (v.[CreditAmount] IS NOT NULL AND s.[CreditAmount] IS NULL)
        OR v.[CreditDate] <> s.[CreditDate]
            OR (v.[CreditDate] IS NULL AND s.[CreditDate] IS NOT NULL)
        OR (v.[CreditDate] IS NOT NULL AND s.[CreditDate] IS NULL)
        OR v.[CreditNr] <> s.[CreditNr]
            OR (v.[CreditNr] IS NULL AND s.[CreditNr] IS NOT NULL)
        OR (v.[CreditNr] IS NOT NULL AND s.[CreditNr] IS NULL)
        OR v.[CTC_HandOverProtocol] <> s.[CTC_HandOverProtocol]
            OR v.[CTC_InvoCust] <> s.[CTC_InvoCust]
            OR (v.[CTC_InvoCust] IS NULL AND s.[CTC_InvoCust] IS NOT NULL)
        OR (v.[CTC_InvoCust] IS NOT NULL AND s.[CTC_InvoCust] IS NULL)
        OR v.[CTC_InvoiceRequest] <> s.[CTC_InvoiceRequest]
            OR v.[CustomerListPrice] <> s.[CustomerListPrice]
            OR (v.[CustomerListPrice] IS NULL AND s.[CustomerListPrice] IS NOT NULL)
        OR (v.[CustomerListPrice] IS NOT NULL AND s.[CustomerListPrice] IS NULL)
        OR v.[CustomerPriceForecast] <> s.[CustomerPriceForecast]
            OR (v.[CustomerPriceForecast] IS NULL AND s.[CustomerPriceForecast] IS NOT NULL)
        OR (v.[CustomerPriceForecast] IS NOT NULL AND s.[CustomerPriceForecast] IS NULL)
        OR v.[CustomerPriceInvoicedCZK] <> s.[CustomerPriceInvoicedCZK]
            OR (v.[CustomerPriceInvoicedCZK] IS NULL AND s.[CustomerPriceInvoicedCZK] IS NOT NULL)
        OR (v.[CustomerPriceInvoicedCZK] IS NOT NULL AND s.[CustomerPriceInvoicedCZK] IS NULL)
        OR v.[CustomerPriceInvoicedEUR] <> s.[CustomerPriceInvoicedEUR]
            OR (v.[CustomerPriceInvoicedEUR] IS NULL AND s.[CustomerPriceInvoicedEUR] IS NOT NULL)
        OR (v.[CustomerPriceInvoicedEUR] IS NOT NULL AND s.[CustomerPriceInvoicedEUR] IS NULL)
        OR v.[DamageDescFromCMR] <> s.[DamageDescFromCMR]
            OR (v.[DamageDescFromCMR] IS NULL AND s.[DamageDescFromCMR] IS NOT NULL)
        OR (v.[DamageDescFromCMR] IS NOT NULL AND s.[DamageDescFromCMR] IS NULL)
        OR v.[DateOUT] <> s.[DateOUT]
            OR (v.[DateOUT] IS NULL AND s.[DateOUT] IS NOT NULL)
        OR (v.[DateOUT] IS NOT NULL AND s.[DateOUT] IS NULL)
        OR v.[DealerCostForecast] <> s.[DealerCostForecast]
            OR (v.[DealerCostForecast] IS NULL AND s.[DealerCostForecast] IS NOT NULL)
        OR (v.[DealerCostForecast] IS NOT NULL AND s.[DealerCostForecast] IS NULL)
        OR v.[DealerCostInvoicedCZK] <> s.[DealerCostInvoicedCZK]
            OR (v.[DealerCostInvoicedCZK] IS NULL AND s.[DealerCostInvoicedCZK] IS NOT NULL)
        OR (v.[DealerCostInvoicedCZK] IS NOT NULL AND s.[DealerCostInvoicedCZK] IS NULL)
        OR v.[DealerCostInvoicedEUR] <> s.[DealerCostInvoicedEUR]
            OR (v.[DealerCostInvoicedEUR] IS NULL AND s.[DealerCostInvoicedEUR] IS NOT NULL)
        OR (v.[DealerCostInvoicedEUR] IS NOT NULL AND s.[DealerCostInvoicedEUR] IS NULL)
        OR v.[DealerFond] <> s.[DealerFond]
            OR (v.[DealerFond] IS NULL AND s.[DealerFond] IS NOT NULL)
        OR (v.[DealerFond] IS NOT NULL AND s.[DealerFond] IS NULL)
        OR v.[DealerMarginScalaCZK] <> s.[DealerMarginScalaCZK]
            OR (v.[DealerMarginScalaCZK] IS NULL AND s.[DealerMarginScalaCZK] IS NOT NULL)
        OR (v.[DealerMarginScalaCZK] IS NOT NULL AND s.[DealerMarginScalaCZK] IS NULL)
        OR v.[DealerMarginScalaEUR] <> s.[DealerMarginScalaEUR]
            OR (v.[DealerMarginScalaEUR] IS NULL AND s.[DealerMarginScalaEUR] IS NOT NULL)
        OR (v.[DealerMarginScalaEUR] IS NOT NULL AND s.[DealerMarginScalaEUR] IS NULL)
        OR v.[DealRefNu] <> s.[DealRefNu]
            OR (v.[DealRefNu] IS NULL AND s.[DealRefNu] IS NOT NULL)
        OR (v.[DealRefNu] IS NOT NULL AND s.[DealRefNu] IS NULL)
        OR v.[DeliveryAddressFull] <> s.[DeliveryAddressFull]
            OR (v.[DeliveryAddressFull] IS NULL AND s.[DeliveryAddressFull] IS NOT NULL)
        OR (v.[DeliveryAddressFull] IS NOT NULL AND s.[DeliveryAddressFull] IS NULL)
        OR v.[DeliveryCustomerDate] <> s.[DeliveryCustomerDate]
            OR (v.[DeliveryCustomerDate] IS NULL AND s.[DeliveryCustomerDate] IS NOT NULL)
        OR (v.[DeliveryCustomerDate] IS NOT NULL AND s.[DeliveryCustomerDate] IS NULL)
        OR v.[DeliveryDealerDate] <> s.[DeliveryDealerDate]
            OR (v.[DeliveryDealerDate] IS NULL AND s.[DeliveryDealerDate] IS NOT NULL)
        OR (v.[DeliveryDealerDate] IS NOT NULL AND s.[DeliveryDealerDate] IS NULL)
        OR v.[DeliveryEndCustDate] <> s.[DeliveryEndCustDate]
            OR (v.[DeliveryEndCustDate] IS NULL AND s.[DeliveryEndCustDate] IS NOT NULL)
        OR (v.[DeliveryEndCustDate] IS NOT NULL AND s.[DeliveryEndCustDate] IS NULL)
        OR v.[DepositAmount] <> s.[DepositAmount]
            OR (v.[DepositAmount] IS NULL AND s.[DepositAmount] IS NOT NULL)
        OR (v.[DepositAmount] IS NOT NULL AND s.[DepositAmount] IS NULL)
        OR v.[DepositDate] <> s.[DepositDate]
            OR (v.[DepositDate] IS NULL AND s.[DepositDate] IS NOT NULL)
        OR (v.[DepositDate] IS NOT NULL AND s.[DepositDate] IS NULL)
        OR v.[DepositNr] <> s.[DepositNr]
            OR (v.[DepositNr] IS NULL AND s.[DepositNr] IS NOT NULL)
        OR (v.[DepositNr] IS NOT NULL AND s.[DepositNr] IS NULL)
        OR v.[DlrPriceChecked] <> s.[DlrPriceChecked]
            OR v.[DXF] <> s.[DXF]
            OR v.[EngineNumber] <> s.[EngineNumber]
            OR (v.[EngineNumber] IS NULL AND s.[EngineNumber] IS NOT NULL)
        OR (v.[EngineNumber] IS NOT NULL AND s.[EngineNumber] IS NULL)
        OR v.[EPC_lenght] <> s.[EPC_lenght]
            OR (v.[EPC_lenght] IS NULL AND s.[EPC_lenght] IS NOT NULL)
        OR (v.[EPC_lenght] IS NOT NULL AND s.[EPC_lenght] IS NULL)
        OR v.[ExchRateAtDCD] <> s.[ExchRateAtDCD]
            OR (v.[ExchRateAtDCD] IS NULL AND s.[ExchRateAtDCD] IS NOT NULL)
        OR (v.[ExchRateAtDCD] IS NOT NULL AND s.[ExchRateAtDCD] IS NULL)
        OR v.[ExwExtraDiscount] <> s.[ExwExtraDiscount]
            OR (v.[ExwExtraDiscount] IS NULL AND s.[ExwExtraDiscount] IS NOT NULL)
        OR (v.[ExwExtraDiscount] IS NOT NULL AND s.[ExwExtraDiscount] IS NULL)
        OR v.[ExwFleetDiscount] <> s.[ExwFleetDiscount]
            OR (v.[ExwFleetDiscount] IS NULL AND s.[ExwFleetDiscount] IS NOT NULL)
        OR (v.[ExwFleetDiscount] IS NOT NULL AND s.[ExwFleetDiscount] IS NULL)
        OR v.[ExwInvDate] <> s.[ExwInvDate]
            OR (v.[ExwInvDate] IS NULL AND s.[ExwInvDate] IS NOT NULL)
        OR (v.[ExwInvDate] IS NOT NULL AND s.[ExwInvDate] IS NULL)
        OR v.[EXWListPriceForecast] <> s.[EXWListPriceForecast]
            OR (v.[EXWListPriceForecast] IS NULL AND s.[EXWListPriceForecast] IS NOT NULL)
        OR (v.[EXWListPriceForecast] IS NOT NULL AND s.[EXWListPriceForecast] IS NULL)
        OR v.[ExworksInvoiceNu] <> s.[ExworksInvoiceNu]
            OR (v.[ExworksInvoiceNu] IS NULL AND s.[ExworksInvoiceNu] IS NOT NULL)
        OR (v.[ExworksInvoiceNu] IS NOT NULL AND s.[ExworksInvoiceNu] IS NULL)
        OR v.[ExworksListPrice] <> s.[ExworksListPrice]
            OR (v.[ExworksListPrice] IS NULL AND s.[ExworksListPrice] IS NOT NULL)
        OR (v.[ExworksListPrice] IS NOT NULL AND s.[ExworksListPrice] IS NULL)
        OR v.[ExworksPrice] <> s.[ExworksPrice]
            OR (v.[ExworksPrice] IS NULL AND s.[ExworksPrice] IS NOT NULL)
        OR (v.[ExworksPrice] IS NOT NULL AND s.[ExworksPrice] IS NULL)
        OR v.[ExwPriceOKYesNo] <> s.[ExwPriceOKYesNo]
            OR v.[ExwSurcharge] <> s.[ExwSurcharge]
            OR (v.[ExwSurcharge] IS NULL AND s.[ExwSurcharge] IS NOT NULL)
        OR (v.[ExwSurcharge] IS NOT NULL AND s.[ExwSurcharge] IS NULL)
        OR v.[EXWsurchargeForecast] <> s.[EXWsurchargeForecast]
            OR (v.[EXWsurchargeForecast] IS NULL AND s.[EXWsurchargeForecast] IS NOT NULL)
        OR (v.[EXWsurchargeForecast] IS NOT NULL AND s.[EXWsurchargeForecast] IS NULL)
        OR v.[FleetSupportRequest] <> s.[FleetSupportRequest]
            OR (v.[FleetSupportRequest] IS NULL AND s.[FleetSupportRequest] IS NOT NULL)
        OR (v.[FleetSupportRequest] IS NOT NULL AND s.[FleetSupportRequest] IS NULL)
        OR v.[FleetSuppSVASamount] <> s.[FleetSuppSVASamount]
            OR (v.[FleetSuppSVASamount] IS NULL AND s.[FleetSuppSVASamount] IS NOT NULL)
        OR (v.[FleetSuppSVASamount] IS NOT NULL AND s.[FleetSuppSVASamount] IS NULL)
        OR v.[FleetSuppSVASdescript] <> s.[FleetSuppSVASdescript]
            OR (v.[FleetSuppSVASdescript] IS NULL AND s.[FleetSuppSVASdescript] IS NOT NULL)
        OR (v.[FleetSuppSVASdescript] IS NOT NULL AND s.[FleetSuppSVASdescript] IS NULL)
        OR v.[FromBodybuilderDelDate] <> s.[FromBodybuilderDelDate]
            OR (v.[FromBodybuilderDelDate] IS NULL AND s.[FromBodybuilderDelDate] IS NOT NULL)
        OR (v.[FromBodybuilderDelDate] IS NOT NULL AND s.[FromBodybuilderDelDate] IS NULL)
        OR v.[FuelLevelFromCMR] <> s.[FuelLevelFromCMR]
            OR (v.[FuelLevelFromCMR] IS NULL AND s.[FuelLevelFromCMR] IS NOT NULL)
        OR (v.[FuelLevelFromCMR] IS NOT NULL AND s.[FuelLevelFromCMR] IS NULL)
        OR v.[HighServiceLevel] <> s.[HighServiceLevel]
            OR (v.[HighServiceLevel] IS NULL AND s.[HighServiceLevel] IS NOT NULL)
        OR (v.[HighServiceLevel] IS NOT NULL AND s.[HighServiceLevel] IS NULL)
        OR v.[ChassisNumber] <> s.[ChassisNumber]
            OR (v.[ChassisNumber] IS NULL AND s.[ChassisNumber] IS NOT NULL)
        OR (v.[ChassisNumber] IS NOT NULL AND s.[ChassisNumber] IS NULL)
        OR v.[ChassisType] <> s.[ChassisType]
            OR (v.[ChassisType] IS NULL AND s.[ChassisType] IS NOT NULL)
        OR (v.[ChassisType] IS NOT NULL AND s.[ChassisType] IS NULL)
        OR v.[ChassisWeight] <> s.[ChassisWeight]
            OR (v.[ChassisWeight] IS NULL AND s.[ChassisWeight] IS NOT NULL)
        OR (v.[ChassisWeight] IS NOT NULL AND s.[ChassisWeight] IS NULL)
        OR v.[ID_Application] <> s.[ID_Application]
            OR (v.[ID_Application] IS NULL AND s.[ID_Application] IS NOT NULL)
        OR (v.[ID_Application] IS NOT NULL AND s.[ID_Application] IS NULL)
        OR v.[ID_Bodybuilder] <> s.[ID_Bodybuilder]
            OR (v.[ID_Bodybuilder] IS NULL AND s.[ID_Bodybuilder] IS NOT NULL)
        OR (v.[ID_Bodybuilder] IS NOT NULL AND s.[ID_Bodybuilder] IS NULL)
        OR v.[ID_BodyPriceCurrency] <> s.[ID_BodyPriceCurrency]
            OR (v.[ID_BodyPriceCurrency] IS NULL AND s.[ID_BodyPriceCurrency] IS NOT NULL)
        OR (v.[ID_BodyPriceCurrency] IS NOT NULL AND s.[ID_BodyPriceCurrency] IS NULL)
        OR v.[ID_BodySegment] <> s.[ID_BodySegment]
            OR (v.[ID_BodySegment] IS NULL AND s.[ID_BodySegment] IS NOT NULL)
        OR (v.[ID_BodySegment] IS NOT NULL AND s.[ID_BodySegment] IS NULL)
        OR v.[ID_Campaign] <> s.[ID_Campaign]
            OR (v.[ID_Campaign] IS NULL AND s.[ID_Campaign] IS NOT NULL)
        OR (v.[ID_Campaign] IS NOT NULL AND s.[ID_Campaign] IS NULL)
        OR v.[ID_CurrentTruckLocation] <> s.[ID_CurrentTruckLocation]
            OR (v.[ID_CurrentTruckLocation] IS NULL AND s.[ID_CurrentTruckLocation] IS NOT NULL)
        OR (v.[ID_CurrentTruckLocation] IS NOT NULL AND s.[ID_CurrentTruckLocation] IS NULL)
        OR v.[ID_Customer] <> s.[ID_Customer]
            OR (v.[ID_Customer] IS NULL AND s.[ID_Customer] IS NOT NULL)
        OR (v.[ID_Customer] IS NOT NULL AND s.[ID_Customer] IS NULL)
        OR v.[ID_Destinace] <> s.[ID_Destinace]
            OR (v.[ID_Destinace] IS NULL AND s.[ID_Destinace] IS NOT NULL)
        OR (v.[ID_Destinace] IS NOT NULL AND s.[ID_Destinace] IS NULL)
        OR v.[ID_EcolutionAnalyse] <> s.[ID_EcolutionAnalyse]
            OR (v.[ID_EcolutionAnalyse] IS NULL AND s.[ID_EcolutionAnalyse] IS NOT NULL)
        OR (v.[ID_EcolutionAnalyse] IS NOT NULL AND s.[ID_EcolutionAnalyse] IS NULL)
        OR v.[ID_ImporterDiscounCode] <> s.[ID_ImporterDiscounCode]
            OR (v.[ID_ImporterDiscounCode] IS NULL AND s.[ID_ImporterDiscounCode] IS NOT NULL)
        OR (v.[ID_ImporterDiscounCode] IS NOT NULL AND s.[ID_ImporterDiscounCode] IS NULL)
        OR v.[ID_InvoiceOwnerCntry] <> s.[ID_InvoiceOwnerCntry]
            OR (v.[ID_InvoiceOwnerCntry] IS NULL AND s.[ID_InvoiceOwnerCntry] IS NOT NULL)
        OR (v.[ID_InvoiceOwnerCntry] IS NOT NULL AND s.[ID_InvoiceOwnerCntry] IS NULL)
        OR v.[ID_LeasingCompany] <> s.[ID_LeasingCompany]
            OR (v.[ID_LeasingCompany] IS NULL AND s.[ID_LeasingCompany] IS NOT NULL)
        OR (v.[ID_LeasingCompany] IS NOT NULL AND s.[ID_LeasingCompany] IS NULL)
        OR v.[ID_LeasingCurrency] <> s.[ID_LeasingCurrency]
            OR (v.[ID_LeasingCurrency] IS NULL AND s.[ID_LeasingCurrency] IS NOT NULL)
        OR (v.[ID_LeasingCurrency] IS NOT NULL AND s.[ID_LeasingCurrency] IS NULL)
        OR v.[ID_OldStatus] <> s.[ID_OldStatus]
            OR (v.[ID_OldStatus] IS NULL AND s.[ID_OldStatus] IS NOT NULL)
        OR (v.[ID_OldStatus] IS NOT NULL AND s.[ID_OldStatus] IS NULL)
        OR v.[ID_Operations] <> s.[ID_Operations]
            OR (v.[ID_Operations] IS NULL AND s.[ID_Operations] IS NOT NULL)
        OR (v.[ID_Operations] IS NOT NULL AND s.[ID_Operations] IS NULL)
        OR v.[ID_PPS] <> s.[ID_PPS]
            OR (v.[ID_PPS] IS NULL AND s.[ID_PPS] IS NOT NULL)
        OR (v.[ID_PPS] IS NOT NULL AND s.[ID_PPS] IS NULL)
        OR v.[ID_PrevReservSman] <> s.[ID_PrevReservSman]
            OR (v.[ID_PrevReservSman] IS NULL AND s.[ID_PrevReservSman] IS NOT NULL)
        OR (v.[ID_PrevReservSman] IS NOT NULL AND s.[ID_PrevReservSman] IS NULL)
        OR v.[ID_PuvodniCustomer] <> s.[ID_PuvodniCustomer]
            OR (v.[ID_PuvodniCustomer] IS NULL AND s.[ID_PuvodniCustomer] IS NOT NULL)
        OR (v.[ID_PuvodniCustomer] IS NOT NULL AND s.[ID_PuvodniCustomer] IS NULL)
        OR v.[ID_PuvodniUser] <> s.[ID_PuvodniUser]
            OR (v.[ID_PuvodniUser] IS NULL AND s.[ID_PuvodniUser] IS NOT NULL)
        OR (v.[ID_PuvodniUser] IS NOT NULL AND s.[ID_PuvodniUser] IS NULL)
        OR v.[ID_ReservationUser] <> s.[ID_ReservationUser]
            OR (v.[ID_ReservationUser] IS NULL AND s.[ID_ReservationUser] IS NOT NULL)
        OR (v.[ID_ReservationUser] IS NOT NULL AND s.[ID_ReservationUser] IS NULL)
        OR v.[ID_ServiceContract] <> s.[ID_ServiceContract]
            OR (v.[ID_ServiceContract] IS NULL AND s.[ID_ServiceContract] IS NOT NULL)
        OR (v.[ID_ServiceContract] IS NOT NULL AND s.[ID_ServiceContract] IS NULL)
        OR v.[ID_ServiceContrAmountCurr] <> s.[ID_ServiceContrAmountCurr]
            OR (v.[ID_ServiceContrAmountCurr] IS NULL AND s.[ID_ServiceContrAmountCurr] IS NOT NULL)
        OR (v.[ID_ServiceContrAmountCurr] IS NOT NULL AND s.[ID_ServiceContrAmountCurr] IS NULL)
        OR v.[ID_Status] <> s.[ID_Status]
            OR (v.[ID_Status] IS NULL AND s.[ID_Status] IS NOT NULL)
        OR (v.[ID_Status] IS NOT NULL AND s.[ID_Status] IS NULL)
        OR v.[ID_TPrequester] <> s.[ID_TPrequester]
            OR (v.[ID_TPrequester] IS NULL AND s.[ID_TPrequester] IS NOT NULL)
        OR (v.[ID_TPrequester] IS NOT NULL AND s.[ID_TPrequester] IS NULL)
        OR v.[ID_User] <> s.[ID_User]
            OR (v.[ID_User] IS NULL AND s.[ID_User] IS NOT NULL)
        OR (v.[ID_User] IS NOT NULL AND s.[ID_User] IS NULL)
        OR v.[ID_userWhoMovedPDD] <> s.[ID_userWhoMovedPDD]
            OR (v.[ID_userWhoMovedPDD] IS NULL AND s.[ID_userWhoMovedPDD] IS NOT NULL)
        OR (v.[ID_userWhoMovedPDD] IS NOT NULL AND s.[ID_userWhoMovedPDD] IS NULL)
        OR v.[ImpDiscount] <> s.[ImpDiscount]
            OR (v.[ImpDiscount] IS NULL AND s.[ImpDiscount] IS NOT NULL)
        OR (v.[ImpDiscount] IS NOT NULL AND s.[ImpDiscount] IS NULL)
        OR v.[ImporterCosts] <> s.[ImporterCosts]
            OR (v.[ImporterCosts] IS NULL AND s.[ImporterCosts] IS NOT NULL)
        OR (v.[ImporterCosts] IS NOT NULL AND s.[ImporterCosts] IS NULL)
        OR v.[ImporterInvPrice] <> s.[ImporterInvPrice]
            OR (v.[ImporterInvPrice] IS NULL AND s.[ImporterInvPrice] IS NOT NULL)
        OR (v.[ImporterInvPrice] IS NOT NULL AND s.[ImporterInvPrice] IS NULL)
        OR v.[ImporterListPrice] <> s.[ImporterListPrice]
            OR (v.[ImporterListPrice] IS NULL AND s.[ImporterListPrice] IS NOT NULL)
        OR (v.[ImporterListPrice] IS NOT NULL AND s.[ImporterListPrice] IS NULL)
        OR v.[ImporterPrice] <> s.[ImporterPrice]
            OR (v.[ImporterPrice] IS NULL AND s.[ImporterPrice] IS NOT NULL)
        OR (v.[ImporterPrice] IS NOT NULL AND s.[ImporterPrice] IS NULL)
        OR v.[IntrastatDate] <> s.[IntrastatDate]
            OR (v.[IntrastatDate] IS NULL AND s.[IntrastatDate] IS NOT NULL)
        OR (v.[IntrastatDate] IS NOT NULL AND s.[IntrastatDate] IS NULL)
        OR v.[InvoiceRqSend] <> s.[InvoiceRqSend]
            OR v.[InvToCustDate] <> s.[InvToCustDate]
            OR (v.[InvToCustDate] IS NULL AND s.[InvToCustDate] IS NOT NULL)
        OR (v.[InvToCustDate] IS NOT NULL AND s.[InvToCustDate] IS NULL)
        OR v.[LastAddressChange] <> s.[LastAddressChange]
            OR (v.[LastAddressChange] IS NULL AND s.[LastAddressChange] IS NOT NULL)
        OR (v.[LastAddressChange] IS NOT NULL AND s.[LastAddressChange] IS NULL)
        OR v.[LeasingConfirmDate] <> s.[LeasingConfirmDate]
            OR (v.[LeasingConfirmDate] IS NULL AND s.[LeasingConfirmDate] IS NOT NULL)
        OR (v.[LeasingConfirmDate] IS NOT NULL AND s.[LeasingConfirmDate] IS NULL)
        OR v.[OLAF] <> s.[OLAF]
            OR (v.[OLAF] IS NULL AND s.[OLAF] IS NOT NULL)
        OR (v.[OLAF] IS NOT NULL AND s.[OLAF] IS NULL)
        OR v.[OrderSendDate] <> s.[OrderSendDate]
            OR (v.[OrderSendDate] IS NULL AND s.[OrderSendDate] IS NOT NULL)
        OR (v.[OrderSendDate] IS NOT NULL AND s.[OrderSendDate] IS NULL)
        OR v.[OriginalPromisedDeliveryDate] <> s.[OriginalPromisedDeliveryDate]
            OR (v.[OriginalPromisedDeliveryDate] IS NULL AND s.[OriginalPromisedDeliveryDate] IS NOT NULL)
        OR (v.[OriginalPromisedDeliveryDate] IS NOT NULL AND s.[OriginalPromisedDeliveryDate] IS NULL)
        OR v.[OurOrderNu] <> s.[OurOrderNu]
            OR (v.[OurOrderNu] IS NULL AND s.[OurOrderNu] IS NOT NULL)
        OR (v.[OurOrderNu] IS NOT NULL AND s.[OurOrderNu] IS NULL)
        OR v.[OvertakenBy] <> s.[OvertakenBy]
            OR (v.[OvertakenBy] IS NULL AND s.[OvertakenBy] IS NOT NULL)
        OR (v.[OvertakenBy] IS NOT NULL AND s.[OvertakenBy] IS NULL)
        OR v.[OvertakingDate] <> s.[OvertakingDate]
            OR (v.[OvertakingDate] IS NULL AND s.[OvertakingDate] IS NOT NULL)
        OR (v.[OvertakingDate] IS NOT NULL AND s.[OvertakingDate] IS NULL)
        OR v.[PicturesAvailable] <> s.[PicturesAvailable]
            OR (v.[PicturesAvailable] IS NULL AND s.[PicturesAvailable] IS NOT NULL)
        OR (v.[PicturesAvailable] IS NOT NULL AND s.[PicturesAvailable] IS NULL)
        OR v.[PreviousPromisedDeliveryDate] <> s.[PreviousPromisedDeliveryDate]
            OR (v.[PreviousPromisedDeliveryDate] IS NULL AND s.[PreviousPromisedDeliveryDate] IS NOT NULL)
        OR (v.[PreviousPromisedDeliveryDate] IS NOT NULL AND s.[PreviousPromisedDeliveryDate] IS NULL)
        OR v.[PreviousReservTill] <> s.[PreviousReservTill]
            OR (v.[PreviousReservTill] IS NULL AND s.[PreviousReservTill] IS NOT NULL)
        OR (v.[PreviousReservTill] IS NOT NULL AND s.[PreviousReservTill] IS NULL)
        OR v.[PreviousSalesDate] <> s.[PreviousSalesDate]
            OR (v.[PreviousSalesDate] IS NULL AND s.[PreviousSalesDate] IS NOT NULL)
        OR (v.[PreviousSalesDate] IS NOT NULL AND s.[PreviousSalesDate] IS NULL)
        OR v.[ProdPeriod] <> s.[ProdPeriod]
            OR (v.[ProdPeriod] IS NULL AND s.[ProdPeriod] IS NOT NULL)
        OR (v.[ProdPeriod] IS NOT NULL AND s.[ProdPeriod] IS NULL)
        OR v.[Prodplant] <> s.[Prodplant]
            OR (v.[Prodplant] IS NULL AND s.[Prodplant] IS NOT NULL)
        OR (v.[Prodplant] IS NOT NULL AND s.[Prodplant] IS NULL)
        OR v.[PromisedDeliveryDate] <> s.[PromisedDeliveryDate]
            OR (v.[PromisedDeliveryDate] IS NULL AND s.[PromisedDeliveryDate] IS NOT NULL)
        OR (v.[PromisedDeliveryDate] IS NOT NULL AND s.[PromisedDeliveryDate] IS NULL)
        OR v.[Remark] <> s.[Remark]
            OR (v.[Remark] IS NULL AND s.[Remark] IS NOT NULL)
        OR (v.[Remark] IS NOT NULL AND s.[Remark] IS NULL)
        OR v.[RemarkInsurence] <> s.[RemarkInsurence]
            OR (v.[RemarkInsurence] IS NULL AND s.[RemarkInsurence] IS NOT NULL)
        OR (v.[RemarkInsurence] IS NOT NULL AND s.[RemarkInsurence] IS NULL)
        OR v.[ReservationRemark] <> s.[ReservationRemark]
            OR (v.[ReservationRemark] IS NULL AND s.[ReservationRemark] IS NOT NULL)
        OR (v.[ReservationRemark] IS NOT NULL AND s.[ReservationRemark] IS NULL)
        OR v.[ReservationSince] <> s.[ReservationSince]
            OR (v.[ReservationSince] IS NULL AND s.[ReservationSince] IS NOT NULL)
        OR (v.[ReservationSince] IS NOT NULL AND s.[ReservationSince] IS NULL)
        OR v.[ReservationTill] <> s.[ReservationTill]
            OR (v.[ReservationTill] IS NULL AND s.[ReservationTill] IS NOT NULL)
        OR (v.[ReservationTill] IS NOT NULL AND s.[ReservationTill] IS NULL)
        OR v.[RVG_amount] <> s.[RVG_amount]
            OR (v.[RVG_amount] IS NULL AND s.[RVG_amount] IS NOT NULL)
        OR (v.[RVG_amount] IS NOT NULL AND s.[RVG_amount] IS NULL)
        OR v.[RVG_approved] <> s.[RVG_approved]
            OR (v.[RVG_approved] IS NULL AND s.[RVG_approved] IS NOT NULL)
        OR (v.[RVG_approved] IS NOT NULL AND s.[RVG_approved] IS NULL)
        OR v.[RVG_BuyBackDate] <> s.[RVG_BuyBackDate]
            OR (v.[RVG_BuyBackDate] IS NULL AND s.[RVG_BuyBackDate] IS NOT NULL)
        OR (v.[RVG_BuyBackDate] IS NOT NULL AND s.[RVG_BuyBackDate] IS NULL)
        OR v.[RVG_contracted] <> s.[RVG_contracted]
            OR v.[RVG_Currency] <> s.[RVG_Currency]
            OR (v.[RVG_Currency] IS NULL AND s.[RVG_Currency] IS NOT NULL)
        OR (v.[RVG_Currency] IS NOT NULL AND s.[RVG_Currency] IS NULL)
        OR v.[RVG_maxOdometer] <> s.[RVG_maxOdometer]
            OR (v.[RVG_maxOdometer] IS NULL AND s.[RVG_maxOdometer] IS NOT NULL)
        OR (v.[RVG_maxOdometer] IS NOT NULL AND s.[RVG_maxOdometer] IS NULL)
        OR v.[SaleableRENT] <> s.[SaleableRENT]
            OR v.[SalesContractNr] <> s.[SalesContractNr]
            OR (v.[SalesContractNr] IS NULL AND s.[SalesContractNr] IS NOT NULL)
        OR (v.[SalesContractNr] IS NOT NULL AND s.[SalesContractNr] IS NULL)
        OR v.[SalesDate] <> s.[SalesDate]
            OR (v.[SalesDate] IS NULL AND s.[SalesDate] IS NOT NULL)
        OR (v.[SalesDate] IS NOT NULL AND s.[SalesDate] IS NULL)
        OR v.[ScaniaOrderNu] <> s.[ScaniaOrderNu]
            OR (v.[ScaniaOrderNu] IS NULL AND s.[ScaniaOrderNu] IS NOT NULL)
        OR (v.[ScaniaOrderNu] IS NOT NULL AND s.[ScaniaOrderNu] IS NULL)
        OR v.[Selector] <> s.[Selector]
            OR v.[ServiceContrAmount] <> s.[ServiceContrAmount]
            OR (v.[ServiceContrAmount] IS NULL AND s.[ServiceContrAmount] IS NOT NULL)
        OR (v.[ServiceContrAmount] IS NOT NULL AND s.[ServiceContrAmount] IS NULL)
        OR v.[ServiceContrPaidFrMrg] <> s.[ServiceContrPaidFrMrg]
            OR (v.[ServiceContrPaidFrMrg] IS NULL AND s.[ServiceContrPaidFrMrg] IS NOT NULL)
        OR (v.[ServiceContrPaidFrMrg] IS NOT NULL AND s.[ServiceContrPaidFrMrg] IS NULL)
        OR v.[SpecifDefiniteDate] <> s.[SpecifDefiniteDate]
            OR (v.[SpecifDefiniteDate] IS NULL AND s.[SpecifDefiniteDate] IS NOT NULL)
        OR (v.[SpecifDefiniteDate] IS NOT NULL AND s.[SpecifDefiniteDate] IS NULL)
        OR v.[SPZ] <> s.[SPZ]
            OR (v.[SPZ] IS NULL AND s.[SPZ] IS NOT NULL)
        OR (v.[SPZ] IS NOT NULL AND s.[SPZ] IS NULL)
        OR v.[StartOfWarrantyDate] <> s.[StartOfWarrantyDate]
            OR (v.[StartOfWarrantyDate] IS NULL AND s.[StartOfWarrantyDate] IS NOT NULL)
        OR (v.[StartOfWarrantyDate] IS NOT NULL AND s.[StartOfWarrantyDate] IS NULL)
        OR v.[StatusChangeDate] <> s.[StatusChangeDate]
            OR (v.[StatusChangeDate] IS NULL AND s.[StatusChangeDate] IS NOT NULL)
        OR (v.[StatusChangeDate] IS NOT NULL AND s.[StatusChangeDate] IS NULL)
        OR v.[SupportDoFabriky] <> s.[SupportDoFabriky]
            OR v.[ToBodybuilderDelDate] <> s.[ToBodybuilderDelDate]
            OR (v.[ToBodybuilderDelDate] IS NULL AND s.[ToBodybuilderDelDate] IS NOT NULL)
        OR (v.[ToBodybuilderDelDate] IS NOT NULL AND s.[ToBodybuilderDelDate] IS NULL)
        OR v.[TotalCredit] <> s.[TotalCredit]
            OR (v.[TotalCredit] IS NULL AND s.[TotalCredit] IS NOT NULL)
        OR (v.[TotalCredit] IS NOT NULL AND s.[TotalCredit] IS NULL)
        OR v.[TPreqDate] <> s.[TPreqDate]
            OR (v.[TPreqDate] IS NULL AND s.[TPreqDate] IS NOT NULL)
        OR (v.[TPreqDate] IS NOT NULL AND s.[TPreqDate] IS NULL)
        OR v.[TPreqRemark] <> s.[TPreqRemark]
            OR (v.[TPreqRemark] IS NULL AND s.[TPreqRemark] IS NOT NULL)
        OR (v.[TPreqRemark] IS NOT NULL AND s.[TPreqRemark] IS NULL)
        OR v.[TPtakingOver] <> s.[TPtakingOver]
            OR (v.[TPtakingOver] IS NULL AND s.[TPtakingOver] IS NOT NULL)
        OR (v.[TPtakingOver] IS NOT NULL AND s.[TPtakingOver] IS NULL)
        OR v.[TruckLocationChangeDate] <> s.[TruckLocationChangeDate]
            OR (v.[TruckLocationChangeDate] IS NULL AND s.[TruckLocationChangeDate] IS NOT NULL)
        OR (v.[TruckLocationChangeDate] IS NOT NULL AND s.[TruckLocationChangeDate] IS NULL)
        OR v.[TruckLocationChangeHistory] <> s.[TruckLocationChangeHistory]
            OR (v.[TruckLocationChangeHistory] IS NULL AND s.[TruckLocationChangeHistory] IS NOT NULL)
        OR (v.[TruckLocationChangeHistory] IS NOT NULL AND s.[TruckLocationChangeHistory] IS NULL)
        OR v.[Used] <> s.[Used]
            OR v.[VATreference] <> s.[VATreference]
            OR (v.[VATreference] IS NULL AND s.[VATreference] IS NOT NULL)
        OR (v.[VATreference] IS NOT NULL AND s.[VATreference] IS NULL)
        OR v.[VehicleLocation] <> s.[VehicleLocation]
            OR (v.[VehicleLocation] IS NULL AND s.[VehicleLocation] IS NOT NULL)
        OR (v.[VehicleLocation] IS NOT NULL AND s.[VehicleLocation] IS NULL)
        OR v.[VersionCesowOrderID] <> s.[VersionCesowOrderID]
            OR (v.[VersionCesowOrderID] IS NULL AND s.[VersionCesowOrderID] IS NOT NULL)
        OR (v.[VersionCesowOrderID] IS NOT NULL AND s.[VersionCesowOrderID] IS NULL)
        OR v.[VIN] <> s.[VIN]
            OR (v.[VIN] IS NULL AND s.[VIN] IS NOT NULL)
        OR (v.[VIN] IS NOT NULL AND s.[VIN] IS NULL)
        OR v.[ZachovatCenu] <> s.[ZachovatCenu]
            OR v.[ZTPnumber] <> s.[ZTPnumber]
            OR (v.[ZTPnumber] IS NULL AND s.[ZTPnumber] IS NOT NULL)
        OR (v.[ZTPnumber] IS NOT NULL AND s.[ZTPnumber] IS NULL)
        )
        THEN 
            UPDATE SET
                [ThreadLogUpdateId] = @ThreadLogId
            

                
        WHEN NOT MATCHED BY TARGET 
            THEN INSERT
            ( 
            [IDD]
            , [AccrualsDescrDIS]
            , [AccrualsDIS]
            , [ActualDealerDate]
            , [AdvancePayment]
            , [BodyCategory]
            , [BodyColour]
            , [BodyInvDate]
            , [BodyPrice]
            , [BodyReInvoiceNr]
            , [BodyReivoicingDate]
            , [BodyWarantyMonthNr]
            , [BodyWorkDescription]
            , [CancelationMoment]
            , [CanceledDealsHistory]
            , [CASTspecifPackage]
            , [CDD2]
            , [ConfirmedDelDealerDate]
            , [ContractedInOrder]
            , [ContractNumber]
            , [Country]
            , [CountryToCountryBodyPrice]
            , [CountryToCountryInvoiceDay]
            , [CountryToCountryInvoiceNr]
            , [CountryToCountryInvoicePrice]
            , [CountryToCountryInvoiceRequestSendDate]
            , [CountryToCountryInvoiceWay]
            , [CreditAmount]
            , [CreditDate]
            , [CreditNr]
            , [CTC_HandOverProtocol]
            , [CTC_InvoCust]
            , [CTC_InvoiceRequest]
            , [CustomerListPrice]
            , [CustomerPriceForecast]
            , [CustomerPriceInvoicedCZK]
            , [CustomerPriceInvoicedEUR]
            , [DamageDescFromCMR]
            , [DateOUT]
            , [DealerCostForecast]
            , [DealerCostInvoicedCZK]
            , [DealerCostInvoicedEUR]
            , [DealerFond]
            , [DealerMarginScalaCZK]
            , [DealerMarginScalaEUR]
            , [DealRefNu]
            , [DeliveryAddressFull]
            , [DeliveryCustomerDate]
            , [DeliveryDealerDate]
            , [DeliveryEndCustDate]
            , [DepositAmount]
            , [DepositDate]
            , [DepositNr]
            , [DlrPriceChecked]
            , [DXF]
            , [EngineNumber]
            , [EPC_lenght]
            , [ExchRateAtDCD]
            , [ExwExtraDiscount]
            , [ExwFleetDiscount]
            , [ExwInvDate]
            , [EXWListPriceForecast]
            , [ExworksInvoiceNu]
            , [ExworksListPrice]
            , [ExworksPrice]
            , [ExwPriceOKYesNo]
            , [ExwSurcharge]
            , [EXWsurchargeForecast]
            , [FleetSupportRequest]
            , [FleetSuppSVASamount]
            , [FleetSuppSVASdescript]
            , [FromBodybuilderDelDate]
            , [FuelLevelFromCMR]
            , [HighServiceLevel]
            , [ChassisNumber]
            , [ChassisType]
            , [ChassisWeight]
            , [ID_Application]
            , [ID_Bodybuilder]
            , [ID_BodyPriceCurrency]
            , [ID_BodySegment]
            , [ID_Campaign]
            , [ID_CurrentTruckLocation]
            , [ID_Customer]
            , [ID_Destinace]
            , [ID_EcolutionAnalyse]
            , [ID_ImporterDiscounCode]
            , [ID_InvoiceOwnerCntry]
            , [ID_LeasingCompany]
            , [ID_LeasingCurrency]
            , [ID_OldStatus]
            , [ID_Operations]
            , [ID_PPS]
            , [ID_PrevReservSman]
            , [ID_PuvodniCustomer]
            , [ID_PuvodniUser]
            , [ID_ReservationUser]
            , [ID_ServiceContract]
            , [ID_ServiceContrAmountCurr]
            , [ID_Status]
            , [ID_TPrequester]
            , [ID_User]
            , [ID_userWhoMovedPDD]
            , [ImpDiscount]
            , [ImporterCosts]
            , [ImporterInvPrice]
            , [ImporterListPrice]
            , [ImporterPrice]
            , [IntrastatDate]
            , [InvoiceRqSend]
            , [InvToCustDate]
            , [LastAddressChange]
            , [LeasingConfirmDate]
            , [OLAF]
            , [OrderSendDate]
            , [OriginalPromisedDeliveryDate]
            , [OurOrderNu]
            , [OvertakenBy]
            , [OvertakingDate]
            , [PicturesAvailable]
            , [PreviousPromisedDeliveryDate]
            , [PreviousReservTill]
            , [PreviousSalesDate]
            , [ProdPeriod]
            , [Prodplant]
            , [PromisedDeliveryDate]
            , [Remark]
            , [RemarkInsurence]
            , [ReservationRemark]
            , [ReservationSince]
            , [ReservationTill]
            , [RVG_amount]
            , [RVG_approved]
            , [RVG_BuyBackDate]
            , [RVG_contracted]
            , [RVG_Currency]
            , [RVG_maxOdometer]
            , [SaleableRENT]
            , [SalesContractNr]
            , [SalesDate]
            , [ScaniaOrderNu]
            , [Selector]
            , [ServiceContrAmount]
            , [ServiceContrPaidFrMrg]
            , [SpecifDefiniteDate]
            , [SPZ]
            , [StartOfWarrantyDate]
            , [StatusChangeDate]
            , [STOCKRemark]
            , [SupportDoFabriky]
            , [ToBodybuilderDelDate]
            , [TotalCredit]
            , [TPreqDate]
            , [TPreqRemark]
            , [TPtakingOver]
            , [TruckLocationChangeDate]
            , [TruckLocationChangeHistory]
            , [Used]
            , [VATreference]
            , [VehicleLocation]
            , [VersionCesowOrderID]
            , [VIN]
            , [ZachovatCenu]
            , [ZTPnumber]
            , [DataSourceId]
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
            
    ) VALUES (
            s.[IDD]
            , s.[AccrualsDescrDIS]
            , s.[AccrualsDIS]
            , s.[ActualDealerDate]
            , s.[AdvancePayment]
            , s.[BodyCategory]
            , s.[BodyColour]
            , s.[BodyInvDate]
            , s.[BodyPrice]
            , s.[BodyReInvoiceNr]
            , s.[BodyReivoicingDate]
            , s.[BodyWarantyMonthNr]
            , s.[BodyWorkDescription]
            , s.[CancelationMoment]
            , s.[CanceledDealsHistory]
            , s.[CASTspecifPackage]
            , s.[CDD2]
            , s.[ConfirmedDelDealerDate]
            , s.[ContractedInOrder]
            , s.[ContractNumber]
            , s.[Country]
            , s.[CountryToCountryBodyPrice]
            , s.[CountryToCountryInvoiceDay]
            , s.[CountryToCountryInvoiceNr]
            , s.[CountryToCountryInvoicePrice]
            , s.[CountryToCountryInvoiceRequestSendDate]
            , s.[CountryToCountryInvoiceWay]
            , s.[CreditAmount]
            , s.[CreditDate]
            , s.[CreditNr]
            , s.[CTC_HandOverProtocol]
            , s.[CTC_InvoCust]
            , s.[CTC_InvoiceRequest]
            , s.[CustomerListPrice]
            , s.[CustomerPriceForecast]
            , s.[CustomerPriceInvoicedCZK]
            , s.[CustomerPriceInvoicedEUR]
            , s.[DamageDescFromCMR]
            , s.[DateOUT]
            , s.[DealerCostForecast]
            , s.[DealerCostInvoicedCZK]
            , s.[DealerCostInvoicedEUR]
            , s.[DealerFond]
            , s.[DealerMarginScalaCZK]
            , s.[DealerMarginScalaEUR]
            , s.[DealRefNu]
            , s.[DeliveryAddressFull]
            , s.[DeliveryCustomerDate]
            , s.[DeliveryDealerDate]
            , s.[DeliveryEndCustDate]
            , s.[DepositAmount]
            , s.[DepositDate]
            , s.[DepositNr]
            , s.[DlrPriceChecked]
            , s.[DXF]
            , s.[EngineNumber]
            , s.[EPC_lenght]
            , s.[ExchRateAtDCD]
            , s.[ExwExtraDiscount]
            , s.[ExwFleetDiscount]
            , s.[ExwInvDate]
            , s.[EXWListPriceForecast]
            , s.[ExworksInvoiceNu]
            , s.[ExworksListPrice]
            , s.[ExworksPrice]
            , s.[ExwPriceOKYesNo]
            , s.[ExwSurcharge]
            , s.[EXWsurchargeForecast]
            , s.[FleetSupportRequest]
            , s.[FleetSuppSVASamount]
            , s.[FleetSuppSVASdescript]
            , s.[FromBodybuilderDelDate]
            , s.[FuelLevelFromCMR]
            , s.[HighServiceLevel]
            , s.[ChassisNumber]
            , s.[ChassisType]
            , s.[ChassisWeight]
            , s.[ID_Application]
            , s.[ID_Bodybuilder]
            , s.[ID_BodyPriceCurrency]
            , s.[ID_BodySegment]
            , s.[ID_Campaign]
            , s.[ID_CurrentTruckLocation]
            , s.[ID_Customer]
            , s.[ID_Destinace]
            , s.[ID_EcolutionAnalyse]
            , s.[ID_ImporterDiscounCode]
            , s.[ID_InvoiceOwnerCntry]
            , s.[ID_LeasingCompany]
            , s.[ID_LeasingCurrency]
            , s.[ID_OldStatus]
            , s.[ID_Operations]
            , s.[ID_PPS]
            , s.[ID_PrevReservSman]
            , s.[ID_PuvodniCustomer]
            , s.[ID_PuvodniUser]
            , s.[ID_ReservationUser]
            , s.[ID_ServiceContract]
            , s.[ID_ServiceContrAmountCurr]
            , s.[ID_Status]
            , s.[ID_TPrequester]
            , s.[ID_User]
            , s.[ID_userWhoMovedPDD]
            , s.[ImpDiscount]
            , s.[ImporterCosts]
            , s.[ImporterInvPrice]
            , s.[ImporterListPrice]
            , s.[ImporterPrice]
            , s.[IntrastatDate]
            , s.[InvoiceRqSend]
            , s.[InvToCustDate]
            , s.[LastAddressChange]
            , s.[LeasingConfirmDate]
            , s.[OLAF]
            , s.[OrderSendDate]
            , s.[OriginalPromisedDeliveryDate]
            , s.[OurOrderNu]
            , s.[OvertakenBy]
            , s.[OvertakingDate]
            , s.[PicturesAvailable]
            , s.[PreviousPromisedDeliveryDate]
            , s.[PreviousReservTill]
            , s.[PreviousSalesDate]
            , s.[ProdPeriod]
            , s.[Prodplant]
            , s.[PromisedDeliveryDate]
            , s.[Remark]
            , s.[RemarkInsurence]
            , s.[ReservationRemark]
            , s.[ReservationSince]
            , s.[ReservationTill]
            , s.[RVG_amount]
            , s.[RVG_approved]
            , s.[RVG_BuyBackDate]
            , s.[RVG_contracted]
            , s.[RVG_Currency]
            , s.[RVG_maxOdometer]
            , s.[SaleableRENT]
            , s.[SalesContractNr]
            , s.[SalesDate]
            , s.[ScaniaOrderNu]
            , s.[Selector]
            , s.[ServiceContrAmount]
            , s.[ServiceContrPaidFrMrg]
            , s.[SpecifDefiniteDate]
            , s.[SPZ]
            , s.[StartOfWarrantyDate]
            , s.[StatusChangeDate]
            , s.[STOCKRemark]
            , s.[SupportDoFabriky]
            , s.[ToBodybuilderDelDate]
            , s.[TotalCredit]
            , s.[TPreqDate]
            , s.[TPreqRemark]
            , s.[TPtakingOver]
            , s.[TruckLocationChangeDate]
            , s.[TruckLocationChangeHistory]
            , s.[Used]
            , s.[VATreference]
            , s.[VehicleLocation]
            , s.[VersionCesowOrderID]
            , s.[VIN]
            , s.[ZachovatCenu]
            , s.[ZTPnumber]
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
    
    INSERT INTO [Vault].[CERTdboOrders] (
            [IDD]
            , [AccrualsDescrDIS]
            , [AccrualsDIS]
            , [ActualDealerDate]
            , [AdvancePayment]
            , [BodyCategory]
            , [BodyColour]
            , [BodyInvDate]
            , [BodyPrice]
            , [BodyReInvoiceNr]
            , [BodyReivoicingDate]
            , [BodyWarantyMonthNr]
            , [BodyWorkDescription]
            , [CancelationMoment]
            , [CanceledDealsHistory]
            , [CASTspecifPackage]
            , [CDD2]
            , [ConfirmedDelDealerDate]
            , [ContractedInOrder]
            , [ContractNumber]
            , [Country]
            , [CountryToCountryBodyPrice]
            , [CountryToCountryInvoiceDay]
            , [CountryToCountryInvoiceNr]
            , [CountryToCountryInvoicePrice]
            , [CountryToCountryInvoiceRequestSendDate]
            , [CountryToCountryInvoiceWay]
            , [CreditAmount]
            , [CreditDate]
            , [CreditNr]
            , [CTC_HandOverProtocol]
            , [CTC_InvoCust]
            , [CTC_InvoiceRequest]
            , [CustomerListPrice]
            , [CustomerPriceForecast]
            , [CustomerPriceInvoicedCZK]
            , [CustomerPriceInvoicedEUR]
            , [DamageDescFromCMR]
            , [DateOUT]
            , [DealerCostForecast]
            , [DealerCostInvoicedCZK]
            , [DealerCostInvoicedEUR]
            , [DealerFond]
            , [DealerMarginScalaCZK]
            , [DealerMarginScalaEUR]
            , [DealRefNu]
            , [DeliveryAddressFull]
            , [DeliveryCustomerDate]
            , [DeliveryDealerDate]
            , [DeliveryEndCustDate]
            , [DepositAmount]
            , [DepositDate]
            , [DepositNr]
            , [DlrPriceChecked]
            , [DXF]
            , [EngineNumber]
            , [EPC_lenght]
            , [ExchRateAtDCD]
            , [ExwExtraDiscount]
            , [ExwFleetDiscount]
            , [ExwInvDate]
            , [EXWListPriceForecast]
            , [ExworksInvoiceNu]
            , [ExworksListPrice]
            , [ExworksPrice]
            , [ExwPriceOKYesNo]
            , [ExwSurcharge]
            , [EXWsurchargeForecast]
            , [FleetSupportRequest]
            , [FleetSuppSVASamount]
            , [FleetSuppSVASdescript]
            , [FromBodybuilderDelDate]
            , [FuelLevelFromCMR]
            , [HighServiceLevel]
            , [ChassisNumber]
            , [ChassisType]
            , [ChassisWeight]
            , [ID_Application]
            , [ID_Bodybuilder]
            , [ID_BodyPriceCurrency]
            , [ID_BodySegment]
            , [ID_Campaign]
            , [ID_CurrentTruckLocation]
            , [ID_Customer]
            , [ID_Destinace]
            , [ID_EcolutionAnalyse]
            , [ID_ImporterDiscounCode]
            , [ID_InvoiceOwnerCntry]
            , [ID_LeasingCompany]
            , [ID_LeasingCurrency]
            , [ID_OldStatus]
            , [ID_Operations]
            , [ID_PPS]
            , [ID_PrevReservSman]
            , [ID_PuvodniCustomer]
            , [ID_PuvodniUser]
            , [ID_ReservationUser]
            , [ID_ServiceContract]
            , [ID_ServiceContrAmountCurr]
            , [ID_Status]
            , [ID_TPrequester]
            , [ID_User]
            , [ID_userWhoMovedPDD]
            , [ImpDiscount]
            , [ImporterCosts]
            , [ImporterInvPrice]
            , [ImporterListPrice]
            , [ImporterPrice]
            , [IntrastatDate]
            , [InvoiceRqSend]
            , [InvToCustDate]
            , [LastAddressChange]
            , [LeasingConfirmDate]
            , [OLAF]
            , [OrderSendDate]
            , [OriginalPromisedDeliveryDate]
            , [OurOrderNu]
            , [OvertakenBy]
            , [OvertakingDate]
            , [PicturesAvailable]
            , [PreviousPromisedDeliveryDate]
            , [PreviousReservTill]
            , [PreviousSalesDate]
            , [ProdPeriod]
            , [Prodplant]
            , [PromisedDeliveryDate]
            , [Remark]
            , [RemarkInsurence]
            , [ReservationRemark]
            , [ReservationSince]
            , [ReservationTill]
            , [RVG_amount]
            , [RVG_approved]
            , [RVG_BuyBackDate]
            , [RVG_contracted]
            , [RVG_Currency]
            , [RVG_maxOdometer]
            , [SaleableRENT]
            , [SalesContractNr]
            , [SalesDate]
            , [ScaniaOrderNu]
            , [Selector]
            , [ServiceContrAmount]
            , [ServiceContrPaidFrMrg]
            , [SpecifDefiniteDate]
            , [SPZ]
            , [StartOfWarrantyDate]
            , [StatusChangeDate]
            , [STOCKRemark]
            , [SupportDoFabriky]
            , [ToBodybuilderDelDate]
            , [TotalCredit]
            , [TPreqDate]
            , [TPreqRemark]
            , [TPtakingOver]
            , [TruckLocationChangeDate]
            , [TruckLocationChangeHistory]
            , [Used]
            , [VATreference]
            , [VehicleLocation]
            , [VersionCesowOrderID]
            , [VIN]
            , [ZachovatCenu]
            , [ZTPnumber]
            , [DataSourceId]
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
        
    ) 
    OUTPUT Inserted.ThreadLogUpdateId INTO @UpdateRowCounts
    SELECT

            s.[IDD]
            , s.[AccrualsDescrDIS]
            , s.[AccrualsDIS]
            , s.[ActualDealerDate]
            , s.[AdvancePayment]
            , s.[BodyCategory]
            , s.[BodyColour]
            , s.[BodyInvDate]
            , s.[BodyPrice]
            , s.[BodyReInvoiceNr]
            , s.[BodyReivoicingDate]
            , s.[BodyWarantyMonthNr]
            , s.[BodyWorkDescription]
            , s.[CancelationMoment]
            , s.[CanceledDealsHistory]
            , s.[CASTspecifPackage]
            , s.[CDD2]
            , s.[ConfirmedDelDealerDate]
            , s.[ContractedInOrder]
            , s.[ContractNumber]
            , s.[Country]
            , s.[CountryToCountryBodyPrice]
            , s.[CountryToCountryInvoiceDay]
            , s.[CountryToCountryInvoiceNr]
            , s.[CountryToCountryInvoicePrice]
            , s.[CountryToCountryInvoiceRequestSendDate]
            , s.[CountryToCountryInvoiceWay]
            , s.[CreditAmount]
            , s.[CreditDate]
            , s.[CreditNr]
            , s.[CTC_HandOverProtocol]
            , s.[CTC_InvoCust]
            , s.[CTC_InvoiceRequest]
            , s.[CustomerListPrice]
            , s.[CustomerPriceForecast]
            , s.[CustomerPriceInvoicedCZK]
            , s.[CustomerPriceInvoicedEUR]
            , s.[DamageDescFromCMR]
            , s.[DateOUT]
            , s.[DealerCostForecast]
            , s.[DealerCostInvoicedCZK]
            , s.[DealerCostInvoicedEUR]
            , s.[DealerFond]
            , s.[DealerMarginScalaCZK]
            , s.[DealerMarginScalaEUR]
            , s.[DealRefNu]
            , s.[DeliveryAddressFull]
            , s.[DeliveryCustomerDate]
            , s.[DeliveryDealerDate]
            , s.[DeliveryEndCustDate]
            , s.[DepositAmount]
            , s.[DepositDate]
            , s.[DepositNr]
            , s.[DlrPriceChecked]
            , s.[DXF]
            , s.[EngineNumber]
            , s.[EPC_lenght]
            , s.[ExchRateAtDCD]
            , s.[ExwExtraDiscount]
            , s.[ExwFleetDiscount]
            , s.[ExwInvDate]
            , s.[EXWListPriceForecast]
            , s.[ExworksInvoiceNu]
            , s.[ExworksListPrice]
            , s.[ExworksPrice]
            , s.[ExwPriceOKYesNo]
            , s.[ExwSurcharge]
            , s.[EXWsurchargeForecast]
            , s.[FleetSupportRequest]
            , s.[FleetSuppSVASamount]
            , s.[FleetSuppSVASdescript]
            , s.[FromBodybuilderDelDate]
            , s.[FuelLevelFromCMR]
            , s.[HighServiceLevel]
            , s.[ChassisNumber]
            , s.[ChassisType]
            , s.[ChassisWeight]
            , s.[ID_Application]
            , s.[ID_Bodybuilder]
            , s.[ID_BodyPriceCurrency]
            , s.[ID_BodySegment]
            , s.[ID_Campaign]
            , s.[ID_CurrentTruckLocation]
            , s.[ID_Customer]
            , s.[ID_Destinace]
            , s.[ID_EcolutionAnalyse]
            , s.[ID_ImporterDiscounCode]
            , s.[ID_InvoiceOwnerCntry]
            , s.[ID_LeasingCompany]
            , s.[ID_LeasingCurrency]
            , s.[ID_OldStatus]
            , s.[ID_Operations]
            , s.[ID_PPS]
            , s.[ID_PrevReservSman]
            , s.[ID_PuvodniCustomer]
            , s.[ID_PuvodniUser]
            , s.[ID_ReservationUser]
            , s.[ID_ServiceContract]
            , s.[ID_ServiceContrAmountCurr]
            , s.[ID_Status]
            , s.[ID_TPrequester]
            , s.[ID_User]
            , s.[ID_userWhoMovedPDD]
            , s.[ImpDiscount]
            , s.[ImporterCosts]
            , s.[ImporterInvPrice]
            , s.[ImporterListPrice]
            , s.[ImporterPrice]
            , s.[IntrastatDate]
            , s.[InvoiceRqSend]
            , s.[InvToCustDate]
            , s.[LastAddressChange]
            , s.[LeasingConfirmDate]
            , s.[OLAF]
            , s.[OrderSendDate]
            , s.[OriginalPromisedDeliveryDate]
            , s.[OurOrderNu]
            , s.[OvertakenBy]
            , s.[OvertakingDate]
            , s.[PicturesAvailable]
            , s.[PreviousPromisedDeliveryDate]
            , s.[PreviousReservTill]
            , s.[PreviousSalesDate]
            , s.[ProdPeriod]
            , s.[Prodplant]
            , s.[PromisedDeliveryDate]
            , s.[Remark]
            , s.[RemarkInsurence]
            , s.[ReservationRemark]
            , s.[ReservationSince]
            , s.[ReservationTill]
            , s.[RVG_amount]
            , s.[RVG_approved]
            , s.[RVG_BuyBackDate]
            , s.[RVG_contracted]
            , s.[RVG_Currency]
            , s.[RVG_maxOdometer]
            , s.[SaleableRENT]
            , s.[SalesContractNr]
            , s.[SalesDate]
            , s.[ScaniaOrderNu]
            , s.[Selector]
            , s.[ServiceContrAmount]
            , s.[ServiceContrPaidFrMrg]
            , s.[SpecifDefiniteDate]
            , s.[SPZ]
            , s.[StartOfWarrantyDate]
            , s.[StatusChangeDate]
            , s.[STOCKRemark]
            , s.[SupportDoFabriky]
            , s.[ToBodybuilderDelDate]
            , s.[TotalCredit]
            , s.[TPreqDate]
            , s.[TPreqRemark]
            , s.[TPtakingOver]
            , s.[TruckLocationChangeDate]
            , s.[TruckLocationChangeHistory]
            , s.[Used]
            , s.[VATreference]
            , s.[VehicleLocation]
            , s.[VersionCesowOrderID]
            , s.[VIN]
            , s.[ZachovatCenu]
            , s.[ZTPnumber]
            , s.[DataSourceId]
            , @ThreadLogId
            , -1
            , -1
            , N'U' -- update
    FROM Stage.CERTdboOrders AS s
    INNER JOIN Vault.CERTdboOrders AS v
        ON  s.[IDD] = v.[IDD] AND v.ThreadLogUpdateId = @ThreadLogId
    
    INSERT INTO [Vault].[CERTdboOrders] (
            [IDD]
            , [AccrualsDescrDIS]
            , [AccrualsDIS]
            , [ActualDealerDate]
            , [AdvancePayment]
            , [BodyCategory]
            , [BodyColour]
            , [BodyInvDate]
            , [BodyPrice]
            , [BodyReInvoiceNr]
            , [BodyReivoicingDate]
            , [BodyWarantyMonthNr]
            , [BodyWorkDescription]
            , [CancelationMoment]
            , [CanceledDealsHistory]
            , [CASTspecifPackage]
            , [CDD2]
            , [ConfirmedDelDealerDate]
            , [ContractedInOrder]
            , [ContractNumber]
            , [Country]
            , [CountryToCountryBodyPrice]
            , [CountryToCountryInvoiceDay]
            , [CountryToCountryInvoiceNr]
            , [CountryToCountryInvoicePrice]
            , [CountryToCountryInvoiceRequestSendDate]
            , [CountryToCountryInvoiceWay]
            , [CreditAmount]
            , [CreditDate]
            , [CreditNr]
            , [CTC_HandOverProtocol]
            , [CTC_InvoCust]
            , [CTC_InvoiceRequest]
            , [CustomerListPrice]
            , [CustomerPriceForecast]
            , [CustomerPriceInvoicedCZK]
            , [CustomerPriceInvoicedEUR]
            , [DamageDescFromCMR]
            , [DateOUT]
            , [DealerCostForecast]
            , [DealerCostInvoicedCZK]
            , [DealerCostInvoicedEUR]
            , [DealerFond]
            , [DealerMarginScalaCZK]
            , [DealerMarginScalaEUR]
            , [DealRefNu]
            , [DeliveryAddressFull]
            , [DeliveryCustomerDate]
            , [DeliveryDealerDate]
            , [DeliveryEndCustDate]
            , [DepositAmount]
            , [DepositDate]
            , [DepositNr]
            , [DlrPriceChecked]
            , [DXF]
            , [EngineNumber]
            , [EPC_lenght]
            , [ExchRateAtDCD]
            , [ExwExtraDiscount]
            , [ExwFleetDiscount]
            , [ExwInvDate]
            , [EXWListPriceForecast]
            , [ExworksInvoiceNu]
            , [ExworksListPrice]
            , [ExworksPrice]
            , [ExwPriceOKYesNo]
            , [ExwSurcharge]
            , [EXWsurchargeForecast]
            , [FleetSupportRequest]
            , [FleetSuppSVASamount]
            , [FleetSuppSVASdescript]
            , [FromBodybuilderDelDate]
            , [FuelLevelFromCMR]
            , [HighServiceLevel]
            , [ChassisNumber]
            , [ChassisType]
            , [ChassisWeight]
            , [ID_Application]
            , [ID_Bodybuilder]
            , [ID_BodyPriceCurrency]
            , [ID_BodySegment]
            , [ID_Campaign]
            , [ID_CurrentTruckLocation]
            , [ID_Customer]
            , [ID_Destinace]
            , [ID_EcolutionAnalyse]
            , [ID_ImporterDiscounCode]
            , [ID_InvoiceOwnerCntry]
            , [ID_LeasingCompany]
            , [ID_LeasingCurrency]
            , [ID_OldStatus]
            , [ID_Operations]
            , [ID_PPS]
            , [ID_PrevReservSman]
            , [ID_PuvodniCustomer]
            , [ID_PuvodniUser]
            , [ID_ReservationUser]
            , [ID_ServiceContract]
            , [ID_ServiceContrAmountCurr]
            , [ID_Status]
            , [ID_TPrequester]
            , [ID_User]
            , [ID_userWhoMovedPDD]
            , [ImpDiscount]
            , [ImporterCosts]
            , [ImporterInvPrice]
            , [ImporterListPrice]
            , [ImporterPrice]
            , [IntrastatDate]
            , [InvoiceRqSend]
            , [InvToCustDate]
            , [LastAddressChange]
            , [LeasingConfirmDate]
            , [OLAF]
            , [OrderSendDate]
            , [OriginalPromisedDeliveryDate]
            , [OurOrderNu]
            , [OvertakenBy]
            , [OvertakingDate]
            , [PicturesAvailable]
            , [PreviousPromisedDeliveryDate]
            , [PreviousReservTill]
            , [PreviousSalesDate]
            , [ProdPeriod]
            , [Prodplant]
            , [PromisedDeliveryDate]
            , [Remark]
            , [RemarkInsurence]
            , [ReservationRemark]
            , [ReservationSince]
            , [ReservationTill]
            , [RVG_amount]
            , [RVG_approved]
            , [RVG_BuyBackDate]
            , [RVG_contracted]
            , [RVG_Currency]
            , [RVG_maxOdometer]
            , [SaleableRENT]
            , [SalesContractNr]
            , [SalesDate]
            , [ScaniaOrderNu]
            , [Selector]
            , [ServiceContrAmount]
            , [ServiceContrPaidFrMrg]
            , [SpecifDefiniteDate]
            , [SPZ]
            , [StartOfWarrantyDate]
            , [StatusChangeDate]
            , [STOCKRemark]
            , [SupportDoFabriky]
            , [ToBodybuilderDelDate]
            , [TotalCredit]
            , [TPreqDate]
            , [TPreqRemark]
            , [TPtakingOver]
            , [TruckLocationChangeDate]
            , [TruckLocationChangeHistory]
            , [Used]
            , [VATreference]
            , [VehicleLocation]
            , [VersionCesowOrderID]
            , [VIN]
            , [ZachovatCenu]
            , [ZTPnumber]
            , [DataSourceId]
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
            
    ) 
    OUTPUT Inserted.ThreadLogDeleteId INTO @DeleteRowCounts
    SELECT
            v.[IDD]
            , v.[AccrualsDescrDIS]
            , v.[AccrualsDIS]
            , v.[ActualDealerDate]
            , v.[AdvancePayment]
            , v.[BodyCategory]
            , v.[BodyColour]
            , v.[BodyInvDate]
            , v.[BodyPrice]
            , v.[BodyReInvoiceNr]
            , v.[BodyReivoicingDate]
            , v.[BodyWarantyMonthNr]
            , v.[BodyWorkDescription]
            , v.[CancelationMoment]
            , v.[CanceledDealsHistory]
            , v.[CASTspecifPackage]
            , v.[CDD2]
            , v.[ConfirmedDelDealerDate]
            , v.[ContractedInOrder]
            , v.[ContractNumber]
            , v.[Country]
            , v.[CountryToCountryBodyPrice]
            , v.[CountryToCountryInvoiceDay]
            , v.[CountryToCountryInvoiceNr]
            , v.[CountryToCountryInvoicePrice]
            , v.[CountryToCountryInvoiceRequestSendDate]
            , v.[CountryToCountryInvoiceWay]
            , v.[CreditAmount]
            , v.[CreditDate]
            , v.[CreditNr]
            , v.[CTC_HandOverProtocol]
            , v.[CTC_InvoCust]
            , v.[CTC_InvoiceRequest]
            , v.[CustomerListPrice]
            , v.[CustomerPriceForecast]
            , v.[CustomerPriceInvoicedCZK]
            , v.[CustomerPriceInvoicedEUR]
            , v.[DamageDescFromCMR]
            , v.[DateOUT]
            , v.[DealerCostForecast]
            , v.[DealerCostInvoicedCZK]
            , v.[DealerCostInvoicedEUR]
            , v.[DealerFond]
            , v.[DealerMarginScalaCZK]
            , v.[DealerMarginScalaEUR]
            , v.[DealRefNu]
            , v.[DeliveryAddressFull]
            , v.[DeliveryCustomerDate]
            , v.[DeliveryDealerDate]
            , v.[DeliveryEndCustDate]
            , v.[DepositAmount]
            , v.[DepositDate]
            , v.[DepositNr]
            , v.[DlrPriceChecked]
            , v.[DXF]
            , v.[EngineNumber]
            , v.[EPC_lenght]
            , v.[ExchRateAtDCD]
            , v.[ExwExtraDiscount]
            , v.[ExwFleetDiscount]
            , v.[ExwInvDate]
            , v.[EXWListPriceForecast]
            , v.[ExworksInvoiceNu]
            , v.[ExworksListPrice]
            , v.[ExworksPrice]
            , v.[ExwPriceOKYesNo]
            , v.[ExwSurcharge]
            , v.[EXWsurchargeForecast]
            , v.[FleetSupportRequest]
            , v.[FleetSuppSVASamount]
            , v.[FleetSuppSVASdescript]
            , v.[FromBodybuilderDelDate]
            , v.[FuelLevelFromCMR]
            , v.[HighServiceLevel]
            , v.[ChassisNumber]
            , v.[ChassisType]
            , v.[ChassisWeight]
            , v.[ID_Application]
            , v.[ID_Bodybuilder]
            , v.[ID_BodyPriceCurrency]
            , v.[ID_BodySegment]
            , v.[ID_Campaign]
            , v.[ID_CurrentTruckLocation]
            , v.[ID_Customer]
            , v.[ID_Destinace]
            , v.[ID_EcolutionAnalyse]
            , v.[ID_ImporterDiscounCode]
            , v.[ID_InvoiceOwnerCntry]
            , v.[ID_LeasingCompany]
            , v.[ID_LeasingCurrency]
            , v.[ID_OldStatus]
            , v.[ID_Operations]
            , v.[ID_PPS]
            , v.[ID_PrevReservSman]
            , v.[ID_PuvodniCustomer]
            , v.[ID_PuvodniUser]
            , v.[ID_ReservationUser]
            , v.[ID_ServiceContract]
            , v.[ID_ServiceContrAmountCurr]
            , v.[ID_Status]
            , v.[ID_TPrequester]
            , v.[ID_User]
            , v.[ID_userWhoMovedPDD]
            , v.[ImpDiscount]
            , v.[ImporterCosts]
            , v.[ImporterInvPrice]
            , v.[ImporterListPrice]
            , v.[ImporterPrice]
            , v.[IntrastatDate]
            , v.[InvoiceRqSend]
            , v.[InvToCustDate]
            , v.[LastAddressChange]
            , v.[LeasingConfirmDate]
            , v.[OLAF]
            , v.[OrderSendDate]
            , v.[OriginalPromisedDeliveryDate]
            , v.[OurOrderNu]
            , v.[OvertakenBy]
            , v.[OvertakingDate]
            , v.[PicturesAvailable]
            , v.[PreviousPromisedDeliveryDate]
            , v.[PreviousReservTill]
            , v.[PreviousSalesDate]
            , v.[ProdPeriod]
            , v.[Prodplant]
            , v.[PromisedDeliveryDate]
            , v.[Remark]
            , v.[RemarkInsurence]
            , v.[ReservationRemark]
            , v.[ReservationSince]
            , v.[ReservationTill]
            , v.[RVG_amount]
            , v.[RVG_approved]
            , v.[RVG_BuyBackDate]
            , v.[RVG_contracted]
            , v.[RVG_Currency]
            , v.[RVG_maxOdometer]
            , v.[SaleableRENT]
            , v.[SalesContractNr]
            , v.[SalesDate]
            , v.[ScaniaOrderNu]
            , v.[Selector]
            , v.[ServiceContrAmount]
            , v.[ServiceContrPaidFrMrg]
            , v.[SpecifDefiniteDate]
            , v.[SPZ]
            , v.[StartOfWarrantyDate]
            , v.[StatusChangeDate]
            , v.[STOCKRemark]
            , v.[SupportDoFabriky]
            , v.[ToBodybuilderDelDate]
            , v.[TotalCredit]
            , v.[TPreqDate]
            , v.[TPreqRemark]
            , v.[TPtakingOver]
            , v.[TruckLocationChangeDate]
            , v.[TruckLocationChangeHistory]
            , v.[Used]
            , v.[VATreference]
            , v.[VehicleLocation]
            , v.[VersionCesowOrderID]
            , v.[VIN]
            , v.[ZachovatCenu]
            , v.[ZTPnumber]
            , v.[DataSourceId]
            , @ThreadLogId
            , -1
            , -1
            , N'D' -- update
    FROM Vault.CERTdboOrders AS v
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
                , TableFinalRowCount = (SELECT COUNT(*) FROM [Vault].[CERTdboOrders] WITH (NOLOCK))
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
