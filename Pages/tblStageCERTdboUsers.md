Table Stage.CERTdboUsers {#tblStageCERTdboUsers}
------------------------

Description:

Stage table CERTdboUsers.

List of dependent objects:

-   \[Stage.uspLoadCERTdboUsers\]\[spStageuspLoadCERTdboUsers\]

-   \[Vault.uspLoadCERTdboUsers\]\[spVaultuspLoadCERTdboUsers\]

  ----------------------------------------------------------------------------------
  Id   Column Name                Data Type       Allow   Description
                                                  Nulls   
  ---- -------------------------- --------------- ------- --------------------------
  1    \_ID\_UserCAST             smallint        Yes     Column \_ID\_UserCAST from
                                                          CERT.dbo.Users

  2    Approver                   bit             Yes     Column Approver from
                                                          CERT.dbo.Users

  3    BonusSystemAlowed          bit             Yes     Column BonusSystemAlowed
                                                          from CERT.dbo.Users

  4    BranchCode                 varchar(3)      Yes     Column BranchCode from
                                                          CERT.dbo.Users

  5    BUS\_Sales                 bit             Yes     Column BUS\_Sales from
                                                          CERT.dbo.Users

  6    DealerModul\_Prices        bit             Yes     Column DealerModul\_Prices
                                                          from CERT.dbo.Users

  7    DistribRights              bit             Yes     Column DistribRights from
                                                          CERT.dbo.Users

  8    Email                      varchar(50)     Yes     Column Email from
                                                          CERT.dbo.Users

  9    ID\_DealerNr               tinyint         Yes     Column ID\_DealerNr from
                                                          CERT.dbo.Users

  10   ID\_User                   smallint        Yes     Column ID\_User from
                                                          CERT.dbo.Users

  11   NT\_Sales                  bit             Yes     Column NT\_Sales from
                                                          CERT.dbo.Users

  12   Oslovení                   nvarchar(200)   Yes     Column Oslovení from
                                                          CERT.dbo.Users

  13   SalesmanCode               varchar(4)      Yes     Column SalesmanCode from
                                                          CERT.dbo.Users

  14   UT\_Sales                  bit             Yes     Column UT\_Sales from
                                                          CERT.dbo.Users

  15   UV\_ModificationAlowed     bit             Yes     Column
                                                          UV\_ModificationAlowed
                                                          from CERT.dbo.Users

  16   Uzivatel                   varchar(20)     Yes     Column Uzivatel from
                                                          CERT.dbo.Users

  17   Uzivatel\_Jmeno            nvarchar(80)    Yes     Column Uzivatel\_Jmeno
                                                          from CERT.dbo.Users

  18   Uzivatel\_Prijmeni         nvarchar(80)    Yes     Column Uzivatel\_Prijmeni
                                                          from CERT.dbo.Users

  19   DataSourceId               int             Yes     Id of the data source the
                                                          row comes from

  20   ThreadLogId                int             Yes     Id of ThreadLog which
                                                          inserted the row
  ----------------------------------------------------------------------------------

\[Back to table list\]\[listoftables\]
