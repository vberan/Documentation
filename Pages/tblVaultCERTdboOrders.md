Table Vault.CERTdboOrders {#tblVaultCERTdboOrders}
-------------------------

Description:

Vault table CERTdboOrders.

List of dependent objects:

-   \[Vault.uspLoadCERTdboOrders\]\[spVaultuspLoadCERTdboOrders\]

-   \[Dw.vCERTdboOrdersActual\]\[viewDwvCERTdboOrdersActual\]

  ----------------------------------------------------------------------------------------------------------------
  Id    Column Name                              Data Type        Allow   Description
                                                                  Nulls   
  ----- ---------------------------------------- ---------------- ------- ----------------------------------------
  1     AccrualsDescrDIS                         nvarchar(120)    Yes     Column AccrualsDescrDIS from
                                                                          Stage.CERTdboOrders

  2     AccrualsDIS                              real             Yes     Column AccrualsDIS from
                                                                          Stage.CERTdboOrders

  3     ActualDealerDate                         smalldatetime    Yes     Column ActualDealerDate from
                                                                          Stage.CERTdboOrders

  4     AdvancePayment                           int              Yes     Column AdvancePayment from
                                                                          Stage.CERTdboOrders

  5     BodyCategory                             nvarchar(200)    Yes     Column BodyCategory from
                                                                          Stage.CERTdboOrders

  6     BodyColour                               nvarchar(200)    Yes     Column BodyColour from
                                                                          Stage.CERTdboOrders

  7     BodyInvDate                              smalldatetime    Yes     Column BodyInvDate from
                                                                          Stage.CERTdboOrders

  8     BodyPrice                                int              Yes     Column BodyPrice from
                                                                          Stage.CERTdboOrders

  9     BodyReInvoiceNr                          int              Yes     Column BodyReInvoiceNr from
                                                                          Stage.CERTdboOrders

  10    BodyReivoicingDate                       smalldatetime    Yes     Column BodyReivoicingDate from
                                                                          Stage.CERTdboOrders

  11    BodyWarantyMonthNr                       tinyint          Yes     Column BodyWarantyMonthNr from
                                                                          Stage.CERTdboOrders

  12    BodyWorkDescription                      nvarchar(max)    Yes     Column BodyWorkDescription from
                                                                          Stage.CERTdboOrders

  13    CancelationMoment                        smalldatetime    Yes     Column CancelationMoment from
                                                                          Stage.CERTdboOrders

  14    CanceledDealsHistory                     nvarchar(max)    Yes     Column CanceledDealsHistory from
                                                                          Stage.CERTdboOrders

  15    CASTspecifPackage                        nvarchar(200)    Yes     Column CASTspecifPackage from
                                                                          Stage.CERTdboOrders

  16    CDD2                                     datetime         Yes     Column CDD2 from Stage.CERTdboOrders

  17    ConfirmedDelDealerDate                   smalldatetime    Yes     Column ConfirmedDelDealerDate from
                                                                          Stage.CERTdboOrders

  18    ContractedInOrder                        char(3)          Yes     Column ContractedInOrder from
                                                                          Stage.CERTdboOrders

  19    ContractNumber                           nvarchar(40)     Yes     Column ContractNumber from
                                                                          Stage.CERTdboOrders

  20    Country                                  nvarchar(12)     Yes     Column Country from Stage.CERTdboOrders

  21    CountryToCountryBodyPrice                int              Yes     Column CountryToCountryBodyPrice from
                                                                          Stage.CERTdboOrders

  22    CountryToCountryInvoiceDay               smalldatetime    Yes     Column CountryToCountryInvoiceDay from
                                                                          Stage.CERTdboOrders

  23    CountryToCountryInvoiceNr                nvarchar(200)    Yes     Column CountryToCountryInvoiceNr from
                                                                          Stage.CERTdboOrders

  24    CountryToCountryInvoicePrice             int              Yes     Column CountryToCountryInvoicePrice from
                                                                          Stage.CERTdboOrders

  25    CountryToCountryInvoiceRequestSendDate   smalldatetime    Yes     Column
                                                                          CountryToCountryInvoiceRequestSendDate
                                                                          from Stage.CERTdboOrders

  26    CountryToCountryInvoiceWay               nvarchar(200)    Yes     Column CountryToCountryInvoiceWay from
                                                                          Stage.CERTdboOrders

  27    CreditAmount                             int              Yes     Column CreditAmount from
                                                                          Stage.CERTdboOrders

  28    CreditDate                               smalldatetime    Yes     Column CreditDate from
                                                                          Stage.CERTdboOrders

  29    CreditNr                                 nvarchar(200)    Yes     Column CreditNr from Stage.CERTdboOrders

  30    CTC\_HandOverProtocol                    bit              Yes     Column CTC\_HandOverProtocol from
                                                                          Stage.CERTdboOrders

  31    CTC\_InvoCust                            nvarchar(40)     Yes     Column CTC\_InvoCust from
                                                                          Stage.CERTdboOrders

  32    CTC\_InvoiceRequest                      bit              Yes     Column CTC\_InvoiceRequest from
                                                                          Stage.CERTdboOrders

  33    CustomerListPrice                        real             Yes     Column CustomerListPrice from
                                                                          Stage.CERTdboOrders

  34    CustomerPriceForecast                    real             Yes     Column CustomerPriceForecast from
                                                                          Stage.CERTdboOrders

  35    CustomerPriceInvoicedCZK                 int              Yes     Column CustomerPriceInvoicedCZK from
                                                                          Stage.CERTdboOrders

  36    CustomerPriceInvoicedEUR                 int              Yes     Column CustomerPriceInvoicedEUR from
                                                                          Stage.CERTdboOrders

  37    DamageDescFromCMR                        nvarchar(240)    Yes     Column DamageDescFromCMR from
                                                                          Stage.CERTdboOrders

  38    DateOUT                                  smalldatetime    Yes     Column DateOUT from Stage.CERTdboOrders

  39    DealerCostForecast                       real             Yes     Column DealerCostForecast from
                                                                          Stage.CERTdboOrders

  40    DealerCostInvoicedCZK                    int              Yes     Column DealerCostInvoicedCZK from
                                                                          Stage.CERTdboOrders

  41    DealerCostInvoicedEUR                    int              Yes     Column DealerCostInvoicedEUR from
                                                                          Stage.CERTdboOrders

  42    DealerFond                               real             Yes     Column DealerFond from
                                                                          Stage.CERTdboOrders

  43    DealerMarginScalaCZK                     int              Yes     Column DealerMarginScalaCZK from
                                                                          Stage.CERTdboOrders

  44    DealerMarginScalaEUR                     int              Yes     Column DealerMarginScalaEUR from
                                                                          Stage.CERTdboOrders

  45    DealRefNu                                nvarchar(64)     Yes     Column DealRefNu from
                                                                          Stage.CERTdboOrders

  46    DeliveryAddressFull                      varchar(255)     Yes     Column DeliveryAddressFull from
                                                                          Stage.CERTdboOrders

  47    DeliveryCustomerDate                     smalldatetime    Yes     Column DeliveryCustomerDate from
                                                                          Stage.CERTdboOrders

  48    DeliveryDealerDate                       smalldatetime    Yes     Column DeliveryDealerDate from
                                                                          Stage.CERTdboOrders

  49    DeliveryEndCustDate                      smalldatetime    Yes     Column DeliveryEndCustDate from
                                                                          Stage.CERTdboOrders

  50    DepositAmount                            int              Yes     Column DepositAmount from
                                                                          Stage.CERTdboOrders

  51    DepositDate                              smalldatetime    Yes     Column DepositDate from
                                                                          Stage.CERTdboOrders

  52    DepositNr                                nvarchar(200)    Yes     Column DepositNr from
                                                                          Stage.CERTdboOrders

  53    DlrPriceChecked                          bit              Yes     Column DlrPriceChecked from
                                                                          Stage.CERTdboOrders

  54    DXF                                      bit              Yes     Column DXF from Stage.CERTdboOrders

  55    EngineNumber                             int              Yes     Column EngineNumber from
                                                                          Stage.CERTdboOrders

  56    EPC\_lenght                              tinyint          Yes     Column EPC\_lenght from
                                                                          Stage.CERTdboOrders

  57    ExchRateAtDCD                            real             Yes     Column ExchRateAtDCD from
                                                                          Stage.CERTdboOrders

  58    ExwExtraDiscount                         int              Yes     Column ExwExtraDiscount from
                                                                          Stage.CERTdboOrders

  59    ExwFleetDiscount                         int              Yes     Column ExwFleetDiscount from
                                                                          Stage.CERTdboOrders

  60    ExwInvDate                               smalldatetime    Yes     Column ExwInvDate from
                                                                          Stage.CERTdboOrders

  61    EXWListPriceForecast                     int              Yes     Column EXWListPriceForecast from
                                                                          Stage.CERTdboOrders

  62    ExworksInvoiceNu                         nvarchar(200)    Yes     Column ExworksInvoiceNu from
                                                                          Stage.CERTdboOrders

  63    ExworksListPrice                         int              Yes     Column ExworksListPrice from
                                                                          Stage.CERTdboOrders

  64    ExworksPrice                             int              Yes     Column ExworksPrice from
                                                                          Stage.CERTdboOrders

  65    ExwPriceOKYesNo                          bit              Yes     Column ExwPriceOKYesNo from
                                                                          Stage.CERTdboOrders

  66    ExwSurcharge                             smallint         Yes     Column ExwSurcharge from
                                                                          Stage.CERTdboOrders

  67    EXWsurchargeForecast                     smallint         Yes     Column EXWsurchargeForecast from
                                                                          Stage.CERTdboOrders

  68    FleetSupportRequest                      smallint         Yes     Column FleetSupportRequest from
                                                                          Stage.CERTdboOrders

  69    FleetSuppSVASamount                      int              Yes     Column FleetSuppSVASamount from
                                                                          Stage.CERTdboOrders

  70    FleetSuppSVASdescript                    varchar(15)      Yes     Column FleetSuppSVASdescript from
                                                                          Stage.CERTdboOrders

  71    FromBodybuilderDelDate                   smalldatetime    Yes     Column FromBodybuilderDelDate from
                                                                          Stage.CERTdboOrders

  72    FuelLevelFromCMR                         nvarchar(40)     Yes     Column FuelLevelFromCMR from
                                                                          Stage.CERTdboOrders

  73    HighServiceLevel                         char(6)          Yes     Column HighServiceLevel from
                                                                          Stage.CERTdboOrders

  74    ChassisNumber                            int              Yes     Column ChassisNumber from
                                                                          Stage.CERTdboOrders

  75    ChassisType                              nvarchar(200)    Yes     Column ChassisType from
                                                                          Stage.CERTdboOrders

  76    ChassisWeight                            smallint         Yes     Column ChassisWeight from
                                                                          Stage.CERTdboOrders

  77    ID\_Application                          tinyint          Yes     Column ID\_Application from
                                                                          Stage.CERTdboOrders

  78    ID\_Bodybuilder                          smallint         Yes     Column ID\_Bodybuilder from
                                                                          Stage.CERTdboOrders

  79    ID\_BodyPriceCurrency                    tinyint          Yes     Column ID\_BodyPriceCurrency from
                                                                          Stage.CERTdboOrders

  80    ID\_BodySegment                          tinyint          Yes     Column ID\_BodySegment from
                                                                          Stage.CERTdboOrders

  81    ID\_Campaign                             tinyint          Yes     Column ID\_Campaign from
                                                                          Stage.CERTdboOrders

  82    ID\_CurrentTruckLocation                 tinyint          Yes     Column ID\_CurrentTruckLocation from
                                                                          Stage.CERTdboOrders

  83    ID\_Customer                             int              Yes     Column ID\_Customer from
                                                                          Stage.CERTdboOrders

  84    ID\_Destinace                            tinyint          Yes     Column ID\_Destinace from
                                                                          Stage.CERTdboOrders

  85    ID\_EcolutionAnalyse                     varchar(10)      Yes     Column ID\_EcolutionAnalyse from
                                                                          Stage.CERTdboOrders

  86    ID\_ImporterDiscounCode                  int              Yes     Column ID\_ImporterDiscounCode from
                                                                          Stage.CERTdboOrders

  87    ID\_InvoiceOwnerCntry                    tinyint          Yes     Column ID\_InvoiceOwnerCntry from
                                                                          Stage.CERTdboOrders

  88    ID\_LeasingCompany                       tinyint          Yes     Column ID\_LeasingCompany from
                                                                          Stage.CERTdboOrders

  89    ID\_LeasingCurrency                      tinyint          Yes     Column ID\_LeasingCurrency from
                                                                          Stage.CERTdboOrders

  90    ID\_OldStatus                            tinyint          Yes     Column ID\_OldStatus from
                                                                          Stage.CERTdboOrders

  91    ID\_Operations                           tinyint          Yes     Column ID\_Operations from
                                                                          Stage.CERTdboOrders

  92    ID\_PPS                                  smallint         Yes     Column ID\_PPS from Stage.CERTdboOrders

  93    ID\_PrevReservSman                       smallint         Yes     Column ID\_PrevReservSman from
                                                                          Stage.CERTdboOrders

  94    ID\_PuvodniCustomer                      smallint         Yes     Column ID\_PuvodniCustomer from
                                                                          Stage.CERTdboOrders

  95    ID\_PuvodniUser                          smallint         Yes     Column ID\_PuvodniUser from
                                                                          Stage.CERTdboOrders

  96    ID\_ReservationUser                      smallint         Yes     Column ID\_ReservationUser from
                                                                          Stage.CERTdboOrders

  97    ID\_ServiceContract                      tinyint          Yes     Column ID\_ServiceContract from
                                                                          Stage.CERTdboOrders

  98    ID\_ServiceContrAmountCurr               tinyint          Yes     Column ID\_ServiceContrAmountCurr from
                                                                          Stage.CERTdboOrders

  99    ID\_Status                               tinyint          Yes     Column ID\_Status from
                                                                          Stage.CERTdboOrders

  100   ID\_TPrequester                          smallint         Yes     Column ID\_TPrequester from
                                                                          Stage.CERTdboOrders

  101   ID\_User                                 smallint         Yes     Column ID\_User from Stage.CERTdboOrders

  102   ID\_userWhoMovedPDD                      smallint         Yes     Column ID\_userWhoMovedPDD from
                                                                          Stage.CERTdboOrders

  103   IDD                                      int              Yes     Column IDD from Stage.CERTdboOrders

  104   ImpDiscount                              float            Yes     Column ImpDiscount from
                                                                          Stage.CERTdboOrders

  105   ImporterCosts                            smallint         Yes     Column ImporterCosts from
                                                                          Stage.CERTdboOrders

  106   ImporterInvPrice                         real             Yes     Column ImporterInvPrice from
                                                                          Stage.CERTdboOrders

  107   ImporterListPrice                        real             Yes     Column ImporterListPrice from
                                                                          Stage.CERTdboOrders

  108   ImporterPrice                            int              Yes     Column ImporterPrice from
                                                                          Stage.CERTdboOrders

  109   IntrastatDate                            smalldatetime    Yes     Column IntrastatDate from
                                                                          Stage.CERTdboOrders

  110   InvoiceRqSend                            bit              Yes     Column InvoiceRqSend from
                                                                          Stage.CERTdboOrders

  111   InvToCustDate                            smalldatetime    Yes     Column InvToCustDate from
                                                                          Stage.CERTdboOrders

  112   LastAddressChange                        smalldatetime    Yes     Column LastAddressChange from
                                                                          Stage.CERTdboOrders

  113   LeasingConfirmDate                       smalldatetime    Yes     Column LeasingConfirmDate from
                                                                          Stage.CERTdboOrders

  114   OLAF                                     real             Yes     Column OLAF from Stage.CERTdboOrders

  115   OrderSendDate                            smalldatetime    Yes     Column OrderSendDate from
                                                                          Stage.CERTdboOrders

  116   OriginalPromisedDeliveryDate             smalldatetime    Yes     Column OriginalPromisedDeliveryDate from
                                                                          Stage.CERTdboOrders

  117   OurOrderNu                               nvarchar(40)     Yes     Column OurOrderNu from
                                                                          Stage.CERTdboOrders

  118   OvertakenBy                              nvarchar(200)    Yes     Column OvertakenBy from
                                                                          Stage.CERTdboOrders

  119   OvertakingDate                           smalldatetime    Yes     Column OvertakingDate from
                                                                          Stage.CERTdboOrders

  120   PicturesAvailable                        smallint         Yes     Column PicturesAvailable from
                                                                          Stage.CERTdboOrders

  121   PreviousPromisedDeliveryDate             smalldatetime    Yes     Column PreviousPromisedDeliveryDate from
                                                                          Stage.CERTdboOrders

  122   PreviousReservTill                       smalldatetime    Yes     Column PreviousReservTill from
                                                                          Stage.CERTdboOrders

  123   PreviousSalesDate                        smalldatetime    Yes     Column PreviousSalesDate from
                                                                          Stage.CERTdboOrders

  124   ProdPeriod                               smallint         Yes     Column ProdPeriod from
                                                                          Stage.CERTdboOrders

  125   Prodplant                                nvarchar(12)     Yes     Column Prodplant from
                                                                          Stage.CERTdboOrders

  126   PromisedDeliveryDate                     smalldatetime    Yes     Column PromisedDeliveryDate from
                                                                          Stage.CERTdboOrders

  127   Remark                                   nvarchar(2000)   Yes     Column Remark from Stage.CERTdboOrders

  128   RemarkInsurence                          nvarchar(200)    Yes     Column RemarkInsurence from
                                                                          Stage.CERTdboOrders

  129   ReservationRemark                        nvarchar(max)    Yes     Column ReservationRemark from
                                                                          Stage.CERTdboOrders

  130   ReservationSince                         smalldatetime    Yes     Column ReservationSince from
                                                                          Stage.CERTdboOrders

  131   ReservationTill                          smalldatetime    Yes     Column ReservationTill from
                                                                          Stage.CERTdboOrders

  132   RVG\_amount                              int              Yes     Column RVG\_amount from
                                                                          Stage.CERTdboOrders

  133   RVG\_approved                            int              Yes     Column RVG\_approved from
                                                                          Stage.CERTdboOrders

  134   RVG\_BuyBackDate                         datetime         Yes     Column RVG\_BuyBackDate from
                                                                          Stage.CERTdboOrders

  135   RVG\_contracted                          bit              Yes     Column RVG\_contracted from
                                                                          Stage.CERTdboOrders

  136   RVG\_Currency                            tinyint          Yes     Column RVG\_Currency from
                                                                          Stage.CERTdboOrders

  137   RVG\_maxOdometer                         int              Yes     Column RVG\_maxOdometer from
                                                                          Stage.CERTdboOrders

  138   SaleableRENT                             bit              Yes     Column SaleableRENT from
                                                                          Stage.CERTdboOrders

  139   SalesContractNr                          nvarchar(40)     Yes     Column SalesContractNr from
                                                                          Stage.CERTdboOrders

  140   SalesDate                                smalldatetime    Yes     Column SalesDate from
                                                                          Stage.CERTdboOrders

  141   ScaniaOrderNu                            nvarchar(80)     Yes     Column ScaniaOrderNu from
                                                                          Stage.CERTdboOrders

  142   Selector                                 bit              Yes     Column Selector from Stage.CERTdboOrders

  143   ServiceContrAmount                       real             Yes     Column ServiceContrAmount from
                                                                          Stage.CERTdboOrders

  144   ServiceContrPaidFrMrg                    char(3)          Yes     Column ServiceContrPaidFrMrg from
                                                                          Stage.CERTdboOrders

  145   SpecifDefiniteDate                       smalldatetime    Yes     Column SpecifDefiniteDate from
                                                                          Stage.CERTdboOrders

  146   SPZ                                      varchar(15)      Yes     Column SPZ from Stage.CERTdboOrders

  147   StartOfWarrantyDate                      smalldatetime    Yes     Column StartOfWarrantyDate from
                                                                          Stage.CERTdboOrders

  148   StatusChangeDate                         smalldatetime    Yes     Column StatusChangeDate from
                                                                          Stage.CERTdboOrders

  149   STOCKRemark                              text             Yes     Column STOCKRemark from
                                                                          Stage.CERTdboOrders

  150   SupportDoFabriky                         bit              Yes     Column SupportDoFabriky from
                                                                          Stage.CERTdboOrders

  151   ToBodybuilderDelDate                     smalldatetime    Yes     Column ToBodybuilderDelDate from
                                                                          Stage.CERTdboOrders

  152   TotalCredit                              smallint         Yes     Column TotalCredit from
                                                                          Stage.CERTdboOrders

  153   TPreqDate                                smalldatetime    Yes     Column TPreqDate from
                                                                          Stage.CERTdboOrders

  154   TPreqRemark                              nvarchar(max)    Yes     Column TPreqRemark from
                                                                          Stage.CERTdboOrders

  155   TPtakingOver                             nvarchar(200)    Yes     Column TPtakingOver from
                                                                          Stage.CERTdboOrders

  156   TruckLocationChangeDate                  smalldatetime    Yes     Column TruckLocationChangeDate from
                                                                          Stage.CERTdboOrders

  157   TruckLocationChangeHistory               nvarchar(max)    Yes     Column TruckLocationChangeHistory from
                                                                          Stage.CERTdboOrders

  158   Used                                     bit              Yes     Column Used from Stage.CERTdboOrders

  159   VATreference                             varchar(15)      Yes     Column VATreference from
                                                                          Stage.CERTdboOrders

  160   VehicleLocation                          varchar(50)      Yes     Column VehicleLocation from
                                                                          Stage.CERTdboOrders

  161   VersionCesowOrderID                      varchar(10)      Yes     Column VersionCesowOrderID from
                                                                          Stage.CERTdboOrders

  162   VIN                                      varchar(17)      Yes     Column VIN from Stage.CERTdboOrders

  163   ZachovatCenu                             bit              Yes     Column ZachovatCenu from
                                                                          Stage.CERTdboOrders

  164   ZTPnumber                                nvarchar(80)     Yes     Column ZTPnumber from
                                                                          Stage.CERTdboOrders

  165   DataSourceId                             int              Yes     Id of the data source the row comes from

  166   ThreadLogInsertId                        int              Yes     Id of ThreadLog which inserted the row

  167   ThreadLogUpdateId                        int              Yes     Id of ThreadLog which updated the row

  168   ThreadLogDeleteId                        int              Yes     Id of ThreadLog which deleted the row

  169   ChangeOperation                          char(1)          Yes     Char representing type of row change - I
                                                                          = Insert, U = Update, D = Delete
  ----------------------------------------------------------------------------------------------------------------

\[Back to table list\]\[listoftables\]
