Table Vault.CERTdboDealers {#tblVaultCERTdboDealers}
--------------------------

Description:

Vault table CERTdboDealers.

List of dependent objects:

-   \[Vault.uspLoadCERTdboDealers\]\[spVaultuspLoadCERTdboDealers\]

-   \[Dw.vCERTdboDealersActual\]\[viewDwvCERTdboDealersActual\]

  ----------------------------------------------------------------------------------
  Id   Column Name                Data Type       Allow   Description
                                                  Nulls   
  ---- -------------------------- --------------- ------- --------------------------
  1    DealerActive               bit             Yes     Column DealerActive from
                                                          Stage.CERTdboDealers

  2    DealerCity                 nvarchar(200)   Yes     Column DealerCity from
                                                          Stage.CERTdboDealers

  3    DealerCode                 nvarchar(16)    Yes     Column DealerCode from
                                                          Stage.CERTdboDealers

  4    DealerFactCode             int             Yes     Column DealerFactCode from
                                                          Stage.CERTdboDealers

  5    DealerName                 nvarchar(128)   Yes     Column DealerName from
                                                          Stage.CERTdboDealers

  6    ID\_Country                tinyint         Yes     Column ID\_Country from
                                                          Stage.CERTdboDealers

  7    ID\_DealerNr               tinyint         Yes     Column ID\_DealerNr from
                                                          Stage.CERTdboDealers

  8    ID\_DLRtyp                 tinyint         Yes     Column ID\_DLRtyp from
                                                          Stage.CERTdboDealers

  9    MailTO                     nvarchar(200)   Yes     Column MailTO from
                                                          Stage.CERTdboDealers

  10   DataSourceId               int             Yes     Id of the data source the
                                                          row comes from

  11   ThreadLogInsertId          int             Yes     Id of ThreadLog which
                                                          inserted the row

  12   ThreadLogUpdateId          int             Yes     Id of ThreadLog which
                                                          updated the row

  13   ThreadLogDeleteId          int             Yes     Id of ThreadLog which
                                                          deleted the row

  14   ChangeOperation            char(1)         Yes     Char representing type of
                                                          row change - I = Insert, U
                                                          = Update, D = Delete
  ----------------------------------------------------------------------------------

\[Back to table list\]\[listoftables\]
