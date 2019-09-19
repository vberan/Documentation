Table Vault.CERTdboUsers {#tblVaultCERTdboUsers}
------------------------

Description:

Vault table CERTdboUsers.

List of dependent objects:

-   \[Vault.uspLoadCERTdboUsers\]\[spVaultuspLoadCERTdboUsers\]

-   \[Dw.vCERTdboUsersActual\]\[viewDwvCERTdboUsersActual\]

  ----------------------------------------------------------------------------------
  Id   Column Name                Data Type       Allow   Description
                                                  Nulls   
  ---- -------------------------- --------------- ------- --------------------------
  1    \_ID\_UserCAST             smallint        Yes     Column \_ID\_UserCAST from
                                                          Stage.CERTdboUsers

  2    Approver                   bit             Yes     Column Approver from
                                                          Stage.CERTdboUsers

  3    BonusSystemAlowed          bit             Yes     Column BonusSystemAlowed
                                                          from Stage.CERTdboUsers

  4    BranchCode                 varchar(3)      Yes     Column BranchCode from
                                                          Stage.CERTdboUsers

  5    BUS\_Sales                 bit             Yes     Column BUS\_Sales from
                                                          Stage.CERTdboUsers

  6    DealerModul\_Prices        bit             Yes     Column DealerModul\_Prices
                                                          from Stage.CERTdboUsers

  7    DistribRights              bit             Yes     Column DistribRights from
                                                          Stage.CERTdboUsers

  8    Email                      varchar(50)     Yes     Column Email from
                                                          Stage.CERTdboUsers

  9    ID\_DealerNr               tinyint         Yes     Column ID\_DealerNr from
                                                          Stage.CERTdboUsers

  10   ID\_User                   smallint        Yes     Column ID\_User from
                                                          Stage.CERTdboUsers

  11   NT\_Sales                  bit             Yes     Column NT\_Sales from
                                                          Stage.CERTdboUsers

  12   Oslovení                   nvarchar(200)   Yes     Column Oslovení from
                                                          Stage.CERTdboUsers

  13   SalesmanCode               varchar(4)      Yes     Column SalesmanCode from
                                                          Stage.CERTdboUsers

  14   UT\_Sales                  bit             Yes     Column UT\_Sales from
                                                          Stage.CERTdboUsers

  15   UV\_ModificationAlowed     bit             Yes     Column
                                                          UV\_ModificationAlowed
                                                          from Stage.CERTdboUsers

  16   Uzivatel                   varchar(20)     Yes     Column Uzivatel from
                                                          Stage.CERTdboUsers

  17   Uzivatel\_Jmeno            nvarchar(80)    Yes     Column Uzivatel\_Jmeno
                                                          from Stage.CERTdboUsers

  18   Uzivatel\_Prijmeni         nvarchar(80)    Yes     Column Uzivatel\_Prijmeni
                                                          from Stage.CERTdboUsers

  19   DataSourceId               int             Yes     Id of the data source the
                                                          row comes from

  20   ThreadLogInsertId          int             Yes     Id of ThreadLog which
                                                          inserted the row

  21   ThreadLogUpdateId          int             Yes     Id of ThreadLog which
                                                          updated the row

  22   ThreadLogDeleteId          int             Yes     Id of ThreadLog which
                                                          deleted the row

  23   ChangeOperation            char(1)         Yes     Char representing type of
                                                          row change - I = Insert, U
                                                          = Update, D = Delete
  ----------------------------------------------------------------------------------

\[Back to table list\]\[listoftables\]
