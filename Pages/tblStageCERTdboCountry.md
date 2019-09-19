Table Stage.CERTdboCountry {#tblStageCERTdboCountry}
--------------------------

Description:

Stage table CERTdboCountry.

List of dependent objects:

-   \[Stage.uspLoadCERTdboCountry\]\[spStageuspLoadCERTdboCountry\]

-   \[Vault.uspLoadCERTdboCountry\]\[spVaultuspLoadCERTdboCountry\]

  Id   Column Name    Data Type      Allow Nulls   Description
  ---- -------------- -------------- ------------- ------------------------------------------
  1    Country        nvarchar(40)   Yes           Column Country from CERT.dbo.Country
  2    CountryCode    nvarchar(12)   Yes           Column CountryCode from CERT.dbo.Country
  3    Flag           image          Yes           Column Flag from CERT.dbo.Country
  4    ID\_Country    tinyint        Yes           Column ID\_Country from CERT.dbo.Country
  5    DataSourceId   int            Yes           Id of the data source the row comes from
  6    ThreadLogId    int            Yes           Id of ThreadLog which inserted the row

\[Back to table list\]\[listoftables\]
