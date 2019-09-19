Table Stage.CERTdboBusOrders {#tblStageCERTdboBusOrders}
----------------------------

Description:

Stage table CERTdboBusOrders.

List of dependent objects:

-   \[Stage.uspLoadCERTdboBusOrders\]\[spStageuspLoadCERTdboBusOrders\]

-   \[Vault.uspLoadCERTdboBusOrders\]\[spVaultuspLoadCERTdboBusOrders\]

  ----------------------------------------------------------------------------------
  Id   Column Name                Data Type       Allow   Description
                                                  Nulls   
  ---- -------------------------- --------------- ------- --------------------------
  1    ACC                        bit             Yes     Column ACC from
                                                          CERT.dbo.BusOrders

  2    ActualDealerDate           smalldatetime   Yes     Column ActualDealerDate
                                                          from CERT.dbo.BusOrders

  3    AEB                        bit             Yes     Column AEB from
                                                          CERT.dbo.BusOrders

  4    BuyBackDate                smalldatetime   Yes     Column BuyBackDate from
                                                          CERT.dbo.BusOrders

  5    CDD                        smalldatetime   Yes     Column CDD from
                                                          CERT.dbo.BusOrders

  6    CDDC                       smalldatetime   Yes     Column CDDC from
                                                          CERT.dbo.BusOrders

  7    Cost                       real            Yes     Column Cost from
                                                          CERT.dbo.BusOrders

  8    CustomerPrice              real            Yes     Column CustomerPrice from
                                                          CERT.dbo.BusOrders

  9    CustomerTemporary          varchar(20)     Yes     Column CustomerTemporary
                                                          from CERT.dbo.BusOrders

  10   DateOUT                    smalldatetime   Yes     Column DateOUT from
                                                          CERT.dbo.BusOrders

  11   DeliveryCustomerDate       smalldatetime   Yes     Column
                                                          DeliveryCustomerDate from
                                                          CERT.dbo.BusOrders

  12   DistributorID              varchar(4)      Yes     Column DistributorID from
                                                          CERT.dbo.BusOrders

  13   DistributorOrderID         varchar(9)      Yes     Column DistributorOrderID
                                                          from CERT.dbo.BusOrders

  14   EngineNumber               int             Yes     Column EngineNumber from
                                                          CERT.dbo.BusOrders

  15   EXWsupport                 real            Yes     Column EXWsupport from
                                                          CERT.dbo.BusOrders

  16   HighServiceLevel           char(6)         Yes     Column HighServiceLevel
                                                          from CERT.dbo.BusOrders

  17   ChassisNumber              int             Yes     Column ChassisNumber from
                                                          CERT.dbo.BusOrders

  18   ChassisONLYcontracted      bit             Yes     Column
                                                          ChassisONLYcontracted from
                                                          CERT.dbo.BusOrders

  19   ChassisType                varchar(15)     Yes     Column ChassisType from
                                                          CERT.dbo.BusOrders

  20   ChassisWeight              smallint        Yes     Column ChassisWeight from
                                                          CERT.dbo.BusOrders

  21   ID\_BusModel               tinyint         Yes     Column ID\_BusModel from
                                                          CERT.dbo.BusOrders

  22   ID\_CurrentBusLocation     tinyint         Yes     Column
                                                          ID\_CurrentBusLocation
                                                          from CERT.dbo.BusOrders

  23   ID\_Customer               int             Yes     Column ID\_Customer from
                                                          CERT.dbo.BusOrders

  24   ID\_Destinace              tinyint         Yes     Column ID\_Destinace from
                                                          CERT.dbo.BusOrders

  25   ID\_Emise                  smallint        Yes     Column ID\_Emise from
                                                          CERT.dbo.BusOrders

  26   ID\_InvoiceCountry         tinyint         Yes     Column ID\_InvoiceCountry
                                                          from CERT.dbo.BusOrders

  27   ID\_ReservUser             smallint        Yes     Column ID\_ReservUser from
                                                          CERT.dbo.BusOrders

  28   ID\_Status                 tinyint         Yes     Column ID\_Status from
                                                          CERT.dbo.BusOrders

  29   ID\_User                   smallint        Yes     Column ID\_User from
                                                          CERT.dbo.BusOrders

  30   IDD\_Bus                   int             Yes     Column IDD\_Bus from
                                                          CERT.dbo.BusOrders

  31   LastAddressChange          smalldatetime   Yes     Column LastAddressChange
                                                          from CERT.dbo.BusOrders

  32   LDW                        bit             Yes     Column LDW from
                                                          CERT.dbo.BusOrders

  33   Margin                     real            Yes     Column Margin from
                                                          CERT.dbo.BusOrders

  34   NET                        real            Yes     Column NET from
                                                          CERT.dbo.BusOrders

  35   ProdPeriod                 smallint        Yes     Column ProdPeriod from
                                                          CERT.dbo.BusOrders

  36   Prodplant                  varchar(3)      Yes     Column Prodplant from
                                                          CERT.dbo.BusOrders

  37   PromisedDeliveryDate       smalldatetime   Yes     Column
                                                          PromisedDeliveryDate from
                                                          CERT.dbo.BusOrders

  38   PurchaseBody               real            Yes     Column PurchaseBody from
                                                          CERT.dbo.BusOrders

  39   PurchaseDateBody           smalldatetime   Yes     Column PurchaseDateBody
                                                          from CERT.dbo.BusOrders

  40   PurchaseDateChassis        smalldatetime   Yes     Column PurchaseDateChassis
                                                          from CERT.dbo.BusOrders

  41   PurchaseChassis            real            Yes     Column PurchaseChassis
                                                          from CERT.dbo.BusOrders

  42   ReInvoiceDate              smalldatetime   Yes     Column ReInvoiceDate from
                                                          CERT.dbo.BusOrders

  43   Remark                     nvarchar(max)   Yes     Column Remark from
                                                          CERT.dbo.BusOrders

  44   ReservationEnd             smalldatetime   Yes     Column ReservationEnd from
                                                          CERT.dbo.BusOrders

  45   ReservationStart           smalldatetime   Yes     Column ReservationStart
                                                          from CERT.dbo.BusOrders

  46   RVGamount                  real            Yes     Column RVGamount from
                                                          CERT.dbo.BusOrders

  47   RVGsupport                 real            Yes     Column RVGsupport from
                                                          CERT.dbo.BusOrders

  48   SalesDate                  smalldatetime   Yes     Column SalesDate from
                                                          CERT.dbo.BusOrders

  49   ScaniaOrderNu              varchar(20)     Yes     Column ScaniaOrderNu from
                                                          CERT.dbo.BusOrders

  50   SEATS                      varchar(4)      Yes     Column SEATS from
                                                          CERT.dbo.BusOrders

  51   SpecifDefiniteDate         smalldatetime   Yes     Column SpecifDefiniteDate
                                                          from CERT.dbo.BusOrders

  52   UsedBus                    bit             Yes     Column UsedBus from
                                                          CERT.dbo.BusOrders

  53   VehicleLocation            varchar(50)     Yes     Column VehicleLocation
                                                          from CERT.dbo.BusOrders

  54   VIN                        varchar(17)     Yes     Column VIN from
                                                          CERT.dbo.BusOrders

  55   DataSourceId               int             Yes     Id of the data source the
                                                          row comes from

  56   ThreadLogId                int             Yes     Id of ThreadLog which
                                                          inserted the row
  ----------------------------------------------------------------------------------

\[Back to table list\]\[listoftables\]
