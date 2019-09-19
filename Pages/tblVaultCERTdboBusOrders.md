Table Vault.CERTdboBusOrders {#tblVaultCERTdboBusOrders}
----------------------------

Description:

Vault table CERTdboBusOrders.

List of dependent objects:

-   \[Vault.uspLoadCERTdboBusOrders\]\[spVaultuspLoadCERTdboBusOrders\]

-   \[Dw.vCERTdboBusOrdersActual\]\[viewDwvCERTdboBusOrdersActual\]

  ----------------------------------------------------------------------------------
  Id   Column Name                Data Type       Allow   Description
                                                  Nulls   
  ---- -------------------------- --------------- ------- --------------------------
  1    ACC                        bit             Yes     Column ACC from
                                                          Stage.CERTdboBusOrders

  2    ActualDealerDate           smalldatetime   Yes     Column ActualDealerDate
                                                          from
                                                          Stage.CERTdboBusOrders

  3    AEB                        bit             Yes     Column AEB from
                                                          Stage.CERTdboBusOrders

  4    BuyBackDate                smalldatetime   Yes     Column BuyBackDate from
                                                          Stage.CERTdboBusOrders

  5    CDD                        smalldatetime   Yes     Column CDD from
                                                          Stage.CERTdboBusOrders

  6    CDDC                       smalldatetime   Yes     Column CDDC from
                                                          Stage.CERTdboBusOrders

  7    Cost                       real            Yes     Column Cost from
                                                          Stage.CERTdboBusOrders

  8    CustomerPrice              real            Yes     Column CustomerPrice from
                                                          Stage.CERTdboBusOrders

  9    CustomerTemporary          varchar(20)     Yes     Column CustomerTemporary
                                                          from
                                                          Stage.CERTdboBusOrders

  10   DateOUT                    smalldatetime   Yes     Column DateOUT from
                                                          Stage.CERTdboBusOrders

  11   DeliveryCustomerDate       smalldatetime   Yes     Column
                                                          DeliveryCustomerDate from
                                                          Stage.CERTdboBusOrders

  12   DistributorID              varchar(4)      Yes     Column DistributorID from
                                                          Stage.CERTdboBusOrders

  13   DistributorOrderID         varchar(9)      Yes     Column DistributorOrderID
                                                          from
                                                          Stage.CERTdboBusOrders

  14   EngineNumber               int             Yes     Column EngineNumber from
                                                          Stage.CERTdboBusOrders

  15   EXWsupport                 real            Yes     Column EXWsupport from
                                                          Stage.CERTdboBusOrders

  16   HighServiceLevel           char(6)         Yes     Column HighServiceLevel
                                                          from
                                                          Stage.CERTdboBusOrders

  17   ChassisNumber              int             Yes     Column ChassisNumber from
                                                          Stage.CERTdboBusOrders

  18   ChassisONLYcontracted      bit             Yes     Column
                                                          ChassisONLYcontracted from
                                                          Stage.CERTdboBusOrders

  19   ChassisType                varchar(15)     Yes     Column ChassisType from
                                                          Stage.CERTdboBusOrders

  20   ChassisWeight              smallint        Yes     Column ChassisWeight from
                                                          Stage.CERTdboBusOrders

  21   ID\_BusModel               tinyint         Yes     Column ID\_BusModel from
                                                          Stage.CERTdboBusOrders

  22   ID\_CurrentBusLocation     tinyint         Yes     Column
                                                          ID\_CurrentBusLocation
                                                          from
                                                          Stage.CERTdboBusOrders

  23   ID\_Customer               int             Yes     Column ID\_Customer from
                                                          Stage.CERTdboBusOrders

  24   ID\_Destinace              tinyint         Yes     Column ID\_Destinace from
                                                          Stage.CERTdboBusOrders

  25   ID\_Emise                  smallint        Yes     Column ID\_Emise from
                                                          Stage.CERTdboBusOrders

  26   ID\_InvoiceCountry         tinyint         Yes     Column ID\_InvoiceCountry
                                                          from
                                                          Stage.CERTdboBusOrders

  27   ID\_ReservUser             smallint        Yes     Column ID\_ReservUser from
                                                          Stage.CERTdboBusOrders

  28   ID\_Status                 tinyint         Yes     Column ID\_Status from
                                                          Stage.CERTdboBusOrders

  29   ID\_User                   smallint        Yes     Column ID\_User from
                                                          Stage.CERTdboBusOrders

  30   IDD\_Bus                   int             Yes     Column IDD\_Bus from
                                                          Stage.CERTdboBusOrders

  31   LastAddressChange          smalldatetime   Yes     Column LastAddressChange
                                                          from
                                                          Stage.CERTdboBusOrders

  32   LDW                        bit             Yes     Column LDW from
                                                          Stage.CERTdboBusOrders

  33   Margin                     real            Yes     Column Margin from
                                                          Stage.CERTdboBusOrders

  34   NET                        real            Yes     Column NET from
                                                          Stage.CERTdboBusOrders

  35   ProdPeriod                 smallint        Yes     Column ProdPeriod from
                                                          Stage.CERTdboBusOrders

  36   Prodplant                  varchar(3)      Yes     Column Prodplant from
                                                          Stage.CERTdboBusOrders

  37   PromisedDeliveryDate       smalldatetime   Yes     Column
                                                          PromisedDeliveryDate from
                                                          Stage.CERTdboBusOrders

  38   PurchaseBody               real            Yes     Column PurchaseBody from
                                                          Stage.CERTdboBusOrders

  39   PurchaseDateBody           smalldatetime   Yes     Column PurchaseDateBody
                                                          from
                                                          Stage.CERTdboBusOrders

  40   PurchaseDateChassis        smalldatetime   Yes     Column PurchaseDateChassis
                                                          from
                                                          Stage.CERTdboBusOrders

  41   PurchaseChassis            real            Yes     Column PurchaseChassis
                                                          from
                                                          Stage.CERTdboBusOrders

  42   ReInvoiceDate              smalldatetime   Yes     Column ReInvoiceDate from
                                                          Stage.CERTdboBusOrders

  43   Remark                     nvarchar(max)   Yes     Column Remark from
                                                          Stage.CERTdboBusOrders

  44   ReservationEnd             smalldatetime   Yes     Column ReservationEnd from
                                                          Stage.CERTdboBusOrders

  45   ReservationStart           smalldatetime   Yes     Column ReservationStart
                                                          from
                                                          Stage.CERTdboBusOrders

  46   RVGamount                  real            Yes     Column RVGamount from
                                                          Stage.CERTdboBusOrders

  47   RVGsupport                 real            Yes     Column RVGsupport from
                                                          Stage.CERTdboBusOrders

  48   SalesDate                  smalldatetime   Yes     Column SalesDate from
                                                          Stage.CERTdboBusOrders

  49   ScaniaOrderNu              varchar(20)     Yes     Column ScaniaOrderNu from
                                                          Stage.CERTdboBusOrders

  50   SEATS                      varchar(4)      Yes     Column SEATS from
                                                          Stage.CERTdboBusOrders

  51   SpecifDefiniteDate         smalldatetime   Yes     Column SpecifDefiniteDate
                                                          from
                                                          Stage.CERTdboBusOrders

  52   UsedBus                    bit             Yes     Column UsedBus from
                                                          Stage.CERTdboBusOrders

  53   VehicleLocation            varchar(50)     Yes     Column VehicleLocation
                                                          from
                                                          Stage.CERTdboBusOrders

  54   VIN                        varchar(17)     Yes     Column VIN from
                                                          Stage.CERTdboBusOrders

  55   DataSourceId               int             Yes     Id of the data source the
                                                          row comes from

  56   ThreadLogInsertId          int             Yes     Id of ThreadLog which
                                                          inserted the row

  57   ThreadLogUpdateId          int             Yes     Id of ThreadLog which
                                                          updated the row

  58   ThreadLogDeleteId          int             Yes     Id of ThreadLog which
                                                          deleted the row

  59   ChangeOperation            char(1)         Yes     Char representing type of
                                                          row change - I = Insert, U
                                                          = Update, D = Delete
  ----------------------------------------------------------------------------------

\[Back to table list\]\[listoftables\]
