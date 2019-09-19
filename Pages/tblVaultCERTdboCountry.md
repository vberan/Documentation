Table Vault.CERTdboCountry {#tblVaultCERTdboCountry}
--------------------------

Description:

Vault table CERTdboCountry.

List of dependent objects:

-   \[Vault.uspLoadCERTdboCountry\]\[spVaultuspLoadCERTdboCountry\]

-   \[Dw.vCERTdboCountryActual\]\[viewDwvCERTdboCountryActual\]

  ---------------------------------------------------------------------------------
  Id   Column Name                Data Type      Allow   Description
                                                 Nulls   
  ---- -------------------------- -------------- ------- --------------------------
  1    Country                    nvarchar(40)   Yes     Column Country from
                                                         Stage.CERTdboCountry

  2    CountryCode                nvarchar(12)   Yes     Column CountryCode from
                                                         Stage.CERTdboCountry

  3    Flag                       image          Yes     Column Flag from
                                                         Stage.CERTdboCountry

  4    ID\_Country                tinyint        Yes     Column ID\_Country from
                                                         Stage.CERTdboCountry

  5    DataSourceId               int            Yes     Id of the data source the
                                                         row comes from

  6    ThreadLogInsertId          int            Yes     Id of ThreadLog which
                                                         inserted the row

  7    ThreadLogUpdateId          int            Yes     Id of ThreadLog which
                                                         updated the row

  8    ThreadLogDeleteId          int            Yes     Id of ThreadLog which
                                                         deleted the row

  9    ChangeOperation            char(1)        Yes     Char representing type of
                                                         row change - I = Insert, U
                                                         = Update, D = Delete
  ---------------------------------------------------------------------------------

\[Back to table list\]\[listoftables\]
