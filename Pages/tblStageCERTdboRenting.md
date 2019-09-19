Table Stage.CERTdboRenting {#tblStageCERTdboRenting}
--------------------------

Description:

Stage table CERTdboRenting.

List of dependent objects:

-   \[Stage.uspLoadCERTdboRenting\]\[spStageuspLoadCERTdboRenting\]

-   \[Vault.uspLoadCERTdboRenting\]\[spVaultuspLoadCERTdboRenting\]

  ----------------------------------------------------------------------------------
  Id   Column Name                Data Type       Allow   Description
                                                  Nulls   
  ---- -------------------------- --------------- ------- --------------------------
  1    ContractNo                 varchar(30)     Yes     Column ContractNo from
                                                          CERT.dbo.Renting

  2    CustomerChargeCZK          int             Yes     Column CustomerChargeCZK
                                                          from CERT.dbo.Renting

  3    CustomerChargeEUR          int             Yes     Column CustomerChargeEUR
                                                          from CERT.dbo.Renting

  4    DoplatekCZK                int             Yes     Column DoplatekCZK from
                                                          CERT.dbo.Renting

  5    DoplatekEUR                int             Yes     Column DoplatekEUR from
                                                          CERT.dbo.Renting

  6    ID\_Customer               int             Yes     Column ID\_Customer from
                                                          CERT.dbo.Renting

  7    ID\_DealerConveyor         tinyint         Yes     Column ID\_DealerConveyor
                                                          from CERT.dbo.Renting

  8    ID\_DobaPronajmu           tinyint         Yes     Column ID\_DobaPronajmu
                                                          from CERT.dbo.Renting

  9    ID\_Projezd                tinyint         Yes     Column ID\_Projezd from
                                                          CERT.dbo.Renting

  10   ID\_RENTING                smallint        Yes     Column ID\_RENTING from
                                                          CERT.dbo.Renting

  11   ID\_Trailer                tinyint         Yes     Column ID\_Trailer from
                                                          CERT.dbo.Renting

  12   ID\_User                   smallint        Yes     Column ID\_User from
                                                          CERT.dbo.Renting

  13   IDD                        int             Yes     Column IDD from
                                                          CERT.dbo.Renting

  14   LastMonthFree              bit             Yes     Column LastMonthFree from
                                                          CERT.dbo.Renting

  15   OdometerEND                int             Yes     Column OdometerEND from
                                                          CERT.dbo.Renting

  16   OdometerSTART              int             Yes     Column OdometerSTART from
                                                          CERT.dbo.Renting

  17   OverKMchargeCZK            real            Yes     Column OverKMchargeCZK
                                                          from CERT.dbo.Renting

  18   OverKMchargeEUR            real            Yes     Column OverKMchargeEUR
                                                          from CERT.dbo.Renting

  19   RENTend                    smalldatetime   Yes     Column RENTend from
                                                          CERT.dbo.Renting

  20   RENTremark                 nvarchar(max)   Yes     Column RENTremark from
                                                          CERT.dbo.Renting

  21   RENTstart                  smalldatetime   Yes     Column RENTstart from
                                                          CERT.dbo.Renting

  22   DataSourceId               int             Yes     Id of the data source the
                                                          row comes from

  23   ThreadLogId                int             Yes     Id of ThreadLog which
                                                          inserted the row
  ----------------------------------------------------------------------------------

\[Back to table list\]\[listoftables\]
