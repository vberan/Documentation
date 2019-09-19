Table Stage.CERTdboOrders {#tblStageCERTdboOrders}
-------------------------

Description:

Stage table CERTdboOrders.

List of dependent objects:

-   \[Stage.uspLoadCERTdboOrders\]\[spStageuspLoadCERTdboOrders\]

-   \[Vault.uspLoadCERTdboOrders\]\[spVaultuspLoadCERTdboOrders\]

  ----------------------------------------------------------------------------------------------------------------
  Id    Column Name                              Data Type        Allow   Description
                                                                  Nulls   
  ----- ---------------------------------------- ---------------- ------- ----------------------------------------
  1     AccrualsDescrDIS                         nvarchar(120)    Yes     Column AccrualsDescrDIS from
                                                                          CERT.dbo.Orders

  2     AccrualsDIS                              real             Yes     Column AccrualsDIS from CERT.dbo.Orders

  3     ActualDealerDate                         smalldatetime    Yes     Column ActualDealerDate from
                                                                          CERT.dbo.Orders

  4     AdvancePayment                           int              Yes     Column AdvancePayment from
                                                                          CERT.dbo.Orders

  5     BodyCategory                             nvarchar(200)    Yes     Column BodyCategory from CERT.dbo.Orders

  6     BodyColour                               nvarchar(200)    Yes     Column BodyColour from CERT.dbo.Orders

  7     BodyInvDate                              smalldatetime    Yes     Column BodyInvDate from CERT.dbo.Orders

  8     BodyPrice                                int              Yes     Column BodyPrice from CERT.dbo.Orders

  9     BodyReInvoiceNr                          int              Yes     Column BodyReInvoiceNr from
                                                                          CERT.dbo.Orders

  10    BodyReivoicingDate                       smalldatetime    Yes     Column BodyReivoicingDate from
                                                                          CERT.dbo.Orders

  11    BodyWarantyMonthNr                       tinyint          Yes     Column BodyWarantyMonthNr from
                                                                          CERT.dbo.Orders

  12    BodyWorkDescription                      nvarchar(max)    Yes     Column BodyWorkDescription from
                                                                          CERT.dbo.Orders

  13    CancelationMoment                        smalldatetime    Yes     Column CancelationMoment from
                                                                          CERT.dbo.Orders

  14    CanceledDealsHistory                     nvarchar(max)    Yes     Column CanceledDealsHistory from
                                                                          CERT.dbo.Orders

  15    CASTspecifPackage                        nvarchar(200)    Yes     Column CASTspecifPackage from
                                                                          CERT.dbo.Orders

  16    CDD2                                     datetime         Yes     Column CDD2 from CERT.dbo.Orders

  17    ConfirmedDelDealerDate                   smalldatetime    Yes     Column ConfirmedDelDealerDate from
                                                                          CERT.dbo.Orders

  18    ContractedInOrder                        char(3)          Yes     Column ContractedInOrder from
                                                                          CERT.dbo.Orders

  19    ContractNumber                           nvarchar(40)     Yes     Column ContractNumber from
                                                                          CERT.dbo.Orders

  20    Country                                  nvarchar(12)     Yes     Column Country from CERT.dbo.Orders

  21    CountryToCountryBodyPrice                int              Yes     Column CountryToCountryBodyPrice from
                                                                          CERT.dbo.Orders

  22    CountryToCountryInvoiceDay               smalldatetime    Yes     Column CountryToCountryInvoiceDay from
                                                                          CERT.dbo.Orders

  23    CountryToCountryInvoiceNr                nvarchar(200)    Yes     Column CountryToCountryInvoiceNr from
                                                                          CERT.dbo.Orders

  24    CountryToCountryInvoicePrice             int              Yes     Column CountryToCountryInvoicePrice from
                                                                          CERT.dbo.Orders

  25    CountryToCountryInvoiceRequestSendDate   smalldatetime    Yes     Column
                                                                          CountryToCountryInvoiceRequestSendDate
                                                                          from CERT.dbo.Orders

  26    CountryToCountryInvoiceWay               nvarchar(200)    Yes     Column CountryToCountryInvoiceWay from
                                                                          CERT.dbo.Orders

  27    CreditAmount                             int              Yes     Column CreditAmount from CERT.dbo.Orders

  28    CreditDate                               smalldatetime    Yes     Column CreditDate from CERT.dbo.Orders

  29    CreditNr                                 nvarchar(200)    Yes     Column CreditNr from CERT.dbo.Orders

  30    CTC\_HandOverProtocol                    bit              Yes     Column CTC\_HandOverProtocol from
                                                                          CERT.dbo.Orders

  31    CTC\_InvoCust                            nvarchar(40)     Yes     Column CTC\_InvoCust from
                                                                          CERT.dbo.Orders

  32    CTC\_InvoiceRequest                      bit              Yes     Column CTC\_InvoiceRequest from
                                                                          CERT.dbo.Orders

  33    CustomerListPrice                        real             Yes     Column CustomerListPrice from
                                                                          CERT.dbo.Orders

  34    CustomerPriceForecast                    real             Yes     Column CustomerPriceForecast from
                                                                          CERT.dbo.Orders

  35    CustomerPriceInvoicedCZK                 int              Yes     Column CustomerPriceInvoicedCZK from
                                                                          CERT.dbo.Orders

  36    CustomerPriceInvoicedEUR                 int              Yes     Column CustomerPriceInvoicedEUR from
                                                                          CERT.dbo.Orders

  37    DamageDescFromCMR                        nvarchar(240)    Yes     Column DamageDescFromCMR from
                                                                          CERT.dbo.Orders

  38    DateOUT                                  smalldatetime    Yes     Column DateOUT from CERT.dbo.Orders

  39    DealerCostForecast                       real             Yes     Column DealerCostForecast from
                                                                          CERT.dbo.Orders

  40    DealerCostInvoicedCZK                    int              Yes     Column DealerCostInvoicedCZK from
                                                                          CERT.dbo.Orders

  41    DealerCostInvoicedEUR                    int              Yes     Column DealerCostInvoicedEUR from
                                                                          CERT.dbo.Orders

  42    DealerFond                               real             Yes     Column DealerFond from CERT.dbo.Orders

  43    DealerMarginScalaCZK                     int              Yes     Column DealerMarginScalaCZK from
                                                                          CERT.dbo.Orders

  44    DealerMarginScalaEUR                     int              Yes     Column DealerMarginScalaEUR from
                                                                          CERT.dbo.Orders

  45    DealRefNu                                nvarchar(64)     Yes     Column DealRefNu from CERT.dbo.Orders

  46    DeliveryAddressFull                      varchar(255)     Yes     Column DeliveryAddressFull from
                                                                          CERT.dbo.Orders

  47    DeliveryCustomerDate                     smalldatetime    Yes     Column DeliveryCustomerDate from
                                                                          CERT.dbo.Orders

  48    DeliveryDealerDate                       smalldatetime    Yes     Column DeliveryDealerDate from
                                                                          CERT.dbo.Orders

  49    DeliveryEndCustDate                      smalldatetime    Yes     Column DeliveryEndCustDate from
                                                                          CERT.dbo.Orders

  50    DepositAmount                            int              Yes     Column DepositAmount from
                                                                          CERT.dbo.Orders

  51    DepositDate                              smalldatetime    Yes     Column DepositDate from CERT.dbo.Orders

  52    DepositNr                                nvarchar(200)    Yes     Column DepositNr from CERT.dbo.Orders

  53    DlrPriceChecked                          bit              Yes     Column DlrPriceChecked from
                                                                          CERT.dbo.Orders

  54    DXF                                      bit              Yes     Column DXF from CERT.dbo.Orders

  55    EngineNumber                             int              Yes     Column EngineNumber from CERT.dbo.Orders

  56    EPC\_lenght                              tinyint          Yes     Column EPC\_lenght from CERT.dbo.Orders

  57    ExchRateAtDCD                            real             Yes     Column ExchRateAtDCD from
                                                                          CERT.dbo.Orders

  58    ExwExtraDiscount                         int              Yes     Column ExwExtraDiscount from
                                                                          CERT.dbo.Orders

  59    ExwFleetDiscount                         int              Yes     Column ExwFleetDiscount from
                                                                          CERT.dbo.Orders

  60    ExwInvDate                               smalldatetime    Yes     Column ExwInvDate from CERT.dbo.Orders

  61    EXWListPriceForecast                     int              Yes     Column EXWListPriceForecast from
                                                                          CERT.dbo.Orders

  62    ExworksInvoiceNu                         nvarchar(200)    Yes     Column ExworksInvoiceNu from
                                                                          CERT.dbo.Orders

  63    ExworksListPrice                         int              Yes     Column ExworksListPrice from
                                                                          CERT.dbo.Orders

  64    ExworksPrice                             int              Yes     Column ExworksPrice from CERT.dbo.Orders

  65    ExwPriceOKYesNo                          bit              Yes     Column ExwPriceOKYesNo from
                                                                          CERT.dbo.Orders

  66    ExwSurcharge                             smallint         Yes     Column ExwSurcharge from CERT.dbo.Orders

  67    EXWsurchargeForecast                     smallint         Yes     Column EXWsurchargeForecast from
                                                                          CERT.dbo.Orders

  68    FleetSupportRequest                      smallint         Yes     Column FleetSupportRequest from
                                                                          CERT.dbo.Orders

  69    FleetSuppSVASamount                      int              Yes     Column FleetSuppSVASamount from
                                                                          CERT.dbo.Orders

  70    FleetSuppSVASdescript                    varchar(15)      Yes     Column FleetSuppSVASdescript from
                                                                          CERT.dbo.Orders

  71    FromBodybuilderDelDate                   smalldatetime    Yes     Column FromBodybuilderDelDate from
                                                                          CERT.dbo.Orders

  72    FuelLevelFromCMR                         nvarchar(40)     Yes     Column FuelLevelFromCMR from
                                                                          CERT.dbo.Orders

  73    HighServiceLevel                         char(6)          Yes     Column HighServiceLevel from
                                                                          CERT.dbo.Orders

  74    ChassisNumber                            int              Yes     Column ChassisNumber from
                                                                          CERT.dbo.Orders

  75    ChassisType                              nvarchar(200)    Yes     Column ChassisType from CERT.dbo.Orders

  76    ChassisWeight                            smallint         Yes     Column ChassisWeight from
                                                                          CERT.dbo.Orders

  77    ID\_Application                          tinyint          Yes     Column ID\_Application from
                                                                          CERT.dbo.Orders

  78    ID\_Bodybuilder                          smallint         Yes     Column ID\_Bodybuilder from
                                                                          CERT.dbo.Orders

  79    ID\_BodyPriceCurrency                    tinyint          Yes     Column ID\_BodyPriceCurrency from
                                                                          CERT.dbo.Orders

  80    ID\_BodySegment                          tinyint          Yes     Column ID\_BodySegment from
                                                                          CERT.dbo.Orders

  81    ID\_Campaign                             tinyint          Yes     Column ID\_Campaign from CERT.dbo.Orders

  82    ID\_CurrentTruckLocation                 tinyint          Yes     Column ID\_CurrentTruckLocation from
                                                                          CERT.dbo.Orders

  83    ID\_Customer                             int              Yes     Column ID\_Customer from CERT.dbo.Orders

  84    ID\_Destinace                            tinyint          Yes     Column ID\_Destinace from
                                                                          CERT.dbo.Orders

  85    ID\_EcolutionAnalyse                     varchar(10)      Yes     Column ID\_EcolutionAnalyse from
                                                                          CERT.dbo.Orders

  86    ID\_ImporterDiscounCode                  int              Yes     Column ID\_ImporterDiscounCode from
                                                                          CERT.dbo.Orders

  87    ID\_InvoiceOwnerCntry                    tinyint          Yes     Column ID\_InvoiceOwnerCntry from
                                                                          CERT.dbo.Orders

  88    ID\_LeasingCompany                       tinyint          Yes     Column ID\_LeasingCompany from
                                                                          CERT.dbo.Orders

  89    ID\_LeasingCurrency                      tinyint          Yes     Column ID\_LeasingCurrency from
                                                                          CERT.dbo.Orders

  90    ID\_OldStatus                            tinyint          Yes     Column ID\_OldStatus from
                                                                          CERT.dbo.Orders

  91    ID\_Operations                           tinyint          Yes     Column ID\_Operations from
                                                                          CERT.dbo.Orders

  92    ID\_PPS                                  smallint         Yes     Column ID\_PPS from CERT.dbo.Orders

  93    ID\_PrevReservSman                       smallint         Yes     Column ID\_PrevReservSman from
                                                                          CERT.dbo.Orders

  94    ID\_PuvodniCustomer                      smallint         Yes     Column ID\_PuvodniCustomer from
                                                                          CERT.dbo.Orders

  95    ID\_PuvodniUser                          smallint         Yes     Column ID\_PuvodniUser from
                                                                          CERT.dbo.Orders

  96    ID\_ReservationUser                      smallint         Yes     Column ID\_ReservationUser from
                                                                          CERT.dbo.Orders

  97    ID\_ServiceContract                      tinyint          Yes     Column ID\_ServiceContract from
                                                                          CERT.dbo.Orders

  98    ID\_ServiceContrAmountCurr               tinyint          Yes     Column ID\_ServiceContrAmountCurr from
                                                                          CERT.dbo.Orders

  99    ID\_Status                               tinyint          Yes     Column ID\_Status from CERT.dbo.Orders

  100   ID\_TPrequester                          smallint         Yes     Column ID\_TPrequester from
                                                                          CERT.dbo.Orders

  101   ID\_User                                 smallint         Yes     Column ID\_User from CERT.dbo.Orders

  102   ID\_userWhoMovedPDD                      smallint         Yes     Column ID\_userWhoMovedPDD from
                                                                          CERT.dbo.Orders

  103   IDD                                      int              Yes     Column IDD from CERT.dbo.Orders

  104   ImpDiscount                              float            Yes     Column ImpDiscount from CERT.dbo.Orders

  105   ImporterCosts                            smallint         Yes     Column ImporterCosts from
                                                                          CERT.dbo.Orders

  106   ImporterInvPrice                         real             Yes     Column ImporterInvPrice from
                                                                          CERT.dbo.Orders

  107   ImporterListPrice                        real             Yes     Column ImporterListPrice from
                                                                          CERT.dbo.Orders

  108   ImporterPrice                            int              Yes     Column ImporterPrice from
                                                                          CERT.dbo.Orders

  109   IntrastatDate                            smalldatetime    Yes     Column IntrastatDate from
                                                                          CERT.dbo.Orders

  110   InvoiceRqSend                            bit              Yes     Column InvoiceRqSend from
                                                                          CERT.dbo.Orders

  111   InvToCustDate                            smalldatetime    Yes     Column InvToCustDate from
                                                                          CERT.dbo.Orders

  112   LastAddressChange                        smalldatetime    Yes     Column LastAddressChange from
                                                                          CERT.dbo.Orders

  113   LeasingConfirmDate                       smalldatetime    Yes     Column LeasingConfirmDate from
                                                                          CERT.dbo.Orders

  114   OLAF                                     real             Yes     Column OLAF from CERT.dbo.Orders

  115   OrderSendDate                            smalldatetime    Yes     Column OrderSendDate from
                                                                          CERT.dbo.Orders

  116   OriginalPromisedDeliveryDate             smalldatetime    Yes     Column OriginalPromisedDeliveryDate from
                                                                          CERT.dbo.Orders

  117   OurOrderNu                               nvarchar(40)     Yes     Column OurOrderNu from CERT.dbo.Orders

  118   OvertakenBy                              nvarchar(200)    Yes     Column OvertakenBy from CERT.dbo.Orders

  119   OvertakingDate                           smalldatetime    Yes     Column OvertakingDate from
                                                                          CERT.dbo.Orders

  120   PicturesAvailable                        smallint         Yes     Column PicturesAvailable from
                                                                          CERT.dbo.Orders

  121   PreviousPromisedDeliveryDate             smalldatetime    Yes     Column PreviousPromisedDeliveryDate from
                                                                          CERT.dbo.Orders

  122   PreviousReservTill                       smalldatetime    Yes     Column PreviousReservTill from
                                                                          CERT.dbo.Orders

  123   PreviousSalesDate                        smalldatetime    Yes     Column PreviousSalesDate from
                                                                          CERT.dbo.Orders

  124   ProdPeriod                               smallint         Yes     Column ProdPeriod from CERT.dbo.Orders

  125   Prodplant                                nvarchar(12)     Yes     Column Prodplant from CERT.dbo.Orders

  126   PromisedDeliveryDate                     smalldatetime    Yes     Column PromisedDeliveryDate from
                                                                          CERT.dbo.Orders

  127   Remark                                   nvarchar(2000)   Yes     Column Remark from CERT.dbo.Orders

  128   RemarkInsurence                          nvarchar(200)    Yes     Column RemarkInsurence from
                                                                          CERT.dbo.Orders

  129   ReservationRemark                        nvarchar(max)    Yes     Column ReservationRemark from
                                                                          CERT.dbo.Orders

  130   ReservationSince                         smalldatetime    Yes     Column ReservationSince from
                                                                          CERT.dbo.Orders

  131   ReservationTill                          smalldatetime    Yes     Column ReservationTill from
                                                                          CERT.dbo.Orders

  132   RVG\_amount                              int              Yes     Column RVG\_amount from CERT.dbo.Orders

  133   RVG\_approved                            int              Yes     Column RVG\_approved from
                                                                          CERT.dbo.Orders

  134   RVG\_BuyBackDate                         datetime         Yes     Column RVG\_BuyBackDate from
                                                                          CERT.dbo.Orders

  135   RVG\_contracted                          bit              Yes     Column RVG\_contracted from
                                                                          CERT.dbo.Orders

  136   RVG\_Currency                            tinyint          Yes     Column RVG\_Currency from
                                                                          CERT.dbo.Orders

  137   RVG\_maxOdometer                         int              Yes     Column RVG\_maxOdometer from
                                                                          CERT.dbo.Orders

  138   SaleableRENT                             bit              Yes     Column SaleableRENT from CERT.dbo.Orders

  139   SalesContractNr                          nvarchar(40)     Yes     Column SalesContractNr from
                                                                          CERT.dbo.Orders

  140   SalesDate                                smalldatetime    Yes     Column SalesDate from CERT.dbo.Orders

  141   ScaniaOrderNu                            nvarchar(80)     Yes     Column ScaniaOrderNu from
                                                                          CERT.dbo.Orders

  142   Selector                                 bit              Yes     Column Selector from CERT.dbo.Orders

  143   ServiceContrAmount                       real             Yes     Column ServiceContrAmount from
                                                                          CERT.dbo.Orders

  144   ServiceContrPaidFrMrg                    char(3)          Yes     Column ServiceContrPaidFrMrg from
                                                                          CERT.dbo.Orders

  145   SpecifDefiniteDate                       smalldatetime    Yes     Column SpecifDefiniteDate from
                                                                          CERT.dbo.Orders

  146   SPZ                                      varchar(15)      Yes     Column SPZ from CERT.dbo.Orders

  147   StartOfWarrantyDate                      smalldatetime    Yes     Column StartOfWarrantyDate from
                                                                          CERT.dbo.Orders

  148   StatusChangeDate                         smalldatetime    Yes     Column StatusChangeDate from
                                                                          CERT.dbo.Orders

  149   STOCKRemark                              text             Yes     Column STOCKRemark from CERT.dbo.Orders

  150   SupportDoFabriky                         bit              Yes     Column SupportDoFabriky from
                                                                          CERT.dbo.Orders

  151   ToBodybuilderDelDate                     smalldatetime    Yes     Column ToBodybuilderDelDate from
                                                                          CERT.dbo.Orders

  152   TotalCredit                              smallint         Yes     Column TotalCredit from CERT.dbo.Orders

  153   TPreqDate                                smalldatetime    Yes     Column TPreqDate from CERT.dbo.Orders

  154   TPreqRemark                              nvarchar(max)    Yes     Column TPreqRemark from CERT.dbo.Orders

  155   TPtakingOver                             nvarchar(200)    Yes     Column TPtakingOver from CERT.dbo.Orders

  156   TruckLocationChangeDate                  smalldatetime    Yes     Column TruckLocationChangeDate from
                                                                          CERT.dbo.Orders

  157   TruckLocationChangeHistory               nvarchar(max)    Yes     Column TruckLocationChangeHistory from
                                                                          CERT.dbo.Orders

  158   Used                                     bit              Yes     Column Used from CERT.dbo.Orders

  159   VATreference                             varchar(15)      Yes     Column VATreference from CERT.dbo.Orders

  160   VehicleLocation                          varchar(50)      Yes     Column VehicleLocation from
                                                                          CERT.dbo.Orders

  161   VersionCesowOrderID                      varchar(10)      Yes     Column VersionCesowOrderID from
                                                                          CERT.dbo.Orders

  162   VIN                                      varchar(17)      Yes     Column VIN from CERT.dbo.Orders

  163   ZachovatCenu                             bit              Yes     Column ZachovatCenu from CERT.dbo.Orders

  164   ZTPnumber                                nvarchar(80)     Yes     Column ZTPnumber from CERT.dbo.Orders

  165   DataSourceId                             int              Yes     Id of the data source the row comes from

  166   ThreadLogId                              int              Yes     Id of ThreadLog which inserted the row
  ----------------------------------------------------------------------------------------------------------------

\[Back to table list\]\[listoftables\]
