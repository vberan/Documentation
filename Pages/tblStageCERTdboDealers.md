Table Stage.CERTdboDealers {#tblStageCERTdboDealers}
--------------------------

Description:

Stage table CERTdboDealers.

List of dependent objects:

-   \[Stage.uspLoadCERTdboDealers\]\[spStageuspLoadCERTdboDealers\]

-   \[Vault.uspLoadCERTdboDealers\]\[spVaultuspLoadCERTdboDealers\]

  Id   Column Name      Data Type       Allow Nulls   Description
  ---- ---------------- --------------- ------------- ---------------------------------------------
  1    DealerActive     bit             Yes           Column DealerActive from CERT.dbo.Dealers
  2    DealerCity       nvarchar(200)   Yes           Column DealerCity from CERT.dbo.Dealers
  3    DealerCode       nvarchar(16)    Yes           Column DealerCode from CERT.dbo.Dealers
  4    DealerFactCode   int             Yes           Column DealerFactCode from CERT.dbo.Dealers
  5    DealerName       nvarchar(128)   Yes           Column DealerName from CERT.dbo.Dealers
  6    ID\_Country      tinyint         Yes           Column ID\_Country from CERT.dbo.Dealers
  7    ID\_DealerNr     tinyint         Yes           Column ID\_DealerNr from CERT.dbo.Dealers
  8    ID\_DLRtyp       tinyint         Yes           Column ID\_DLRtyp from CERT.dbo.Dealers
  9    MailTO           nvarchar(200)   Yes           Column MailTO from CERT.dbo.Dealers
  10   DataSourceId     int             Yes           Id of the data source the row comes from
  11   ThreadLogId      int             Yes           Id of ThreadLog which inserted the row

\[Back to table list\]\[listoftables\]
