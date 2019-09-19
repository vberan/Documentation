Table Vault.CERTdboRenting {#tblVaultCERTdboRenting}
--------------------------

Description:

Vault table CERTdboRenting.

List of dependent objects:

-   \[Vault.uspLoadCERTdboRenting\]\[spVaultuspLoadCERTdboRenting\]

-   \[Dw.vCERTdboRentingActual\]\[viewDwvCERTdboRentingActual\]

  ----------------------------------------------------------------------------------
  Id   Column Name                Data Type       Allow   Description
                                                  Nulls   
  ---- -------------------------- --------------- ------- --------------------------
  1    ContractNo                 varchar(30)     Yes     Column ContractNo from
                                                          Stage.CERTdboRenting

  2    CustomerChargeCZK          int             Yes     Column CustomerChargeCZK
                                                          from Stage.CERTdboRenting

  3    CustomerChargeEUR          int             Yes     Column CustomerChargeEUR
                                                          from Stage.CERTdboRenting

  4    DoplatekCZK                int             Yes     Column DoplatekCZK from
                                                          Stage.CERTdboRenting

  5    DoplatekEUR                int             Yes     Column DoplatekEUR from
                                                          Stage.CERTdboRenting

  6    ID\_Customer               int             Yes     Column ID\_Customer from
                                                          Stage.CERTdboRenting

  7    ID\_DealerConveyor         tinyint         Yes     Column ID\_DealerConveyor
                                                          from Stage.CERTdboRenting

  8    ID\_DobaPronajmu           tinyint         Yes     Column ID\_DobaPronajmu
                                                          from Stage.CERTdboRenting

  9    ID\_Projezd                tinyint         Yes     Column ID\_Projezd from
                                                          Stage.CERTdboRenting

  10   ID\_RENTING                smallint        Yes     Column ID\_RENTING from
                                                          Stage.CERTdboRenting

  11   ID\_Trailer                tinyint         Yes     Column ID\_Trailer from
                                                          Stage.CERTdboRenting

  12   ID\_User                   smallint        Yes     Column ID\_User from
                                                          Stage.CERTdboRenting

  13   IDD                        int             Yes     Column IDD from
                                                          Stage.CERTdboRenting

  14   LastMonthFree              bit             Yes     Column LastMonthFree from
                                                          Stage.CERTdboRenting

  15   OdometerEND                int             Yes     Column OdometerEND from
                                                          Stage.CERTdboRenting

  16   OdometerSTART              int             Yes     Column OdometerSTART from
                                                          Stage.CERTdboRenting

  17   OverKMchargeCZK            real            Yes     Column OverKMchargeCZK
                                                          from Stage.CERTdboRenting

  18   OverKMchargeEUR            real            Yes     Column OverKMchargeEUR
                                                          from Stage.CERTdboRenting

  19   RENTend                    smalldatetime   Yes     Column RENTend from
                                                          Stage.CERTdboRenting

  20   RENTremark                 nvarchar(max)   Yes     Column RENTremark from
                                                          Stage.CERTdboRenting

  21   RENTstart                  smalldatetime   Yes     Column RENTstart from
                                                          Stage.CERTdboRenting

  22   DataSourceId               int             Yes     Id of the data source the
                                                          row comes from

  23   ThreadLogInsertId          int             Yes     Id of ThreadLog which
                                                          inserted the row

  24   ThreadLogUpdateId          int             Yes     Id of ThreadLog which
                                                          updated the row

  25   ThreadLogDeleteId          int             Yes     Id of ThreadLog which
                                                          deleted the row

  26   ChangeOperation            char(1)         Yes     Char representing type of
                                                          row change - I = Insert, U
                                                          = Update, D = Delete
  ----------------------------------------------------------------------------------

\[Back to table list\]\[listoftables\]
