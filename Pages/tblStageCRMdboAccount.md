Table Stage.CRMdboAccount {#tblStageCRMdboAccount}
-------------------------

Description:

Stage table CRMdboAccount.

List of dependent objects:

-   \[Stage.uspLoadCRMdboAccount\]\[spStageuspLoadCRMdboAccount\]

-   \[Vault.uspLoadCRMdboAccount\]\[spVaultuspLoadCRMdboAccount\]

  ----------------------------------------------------------------------------------------
  Id   Column Name                Data Type          Allow   Description
                                                     Nulls   
  ---- -------------------------- ------------------ ------- -----------------------------
  1    accountcategorycode        int                Yes     Column accountcategorycode
                                                             from
                                                             ScaniaCRMExport.dbo.account

  2    accountid                  uniqueidentifier   Yes     Column accountid from
                                                             ScaniaCRMExport.dbo.account

  3    address1\_city             nvarchar(320)      Yes     Column address1\_city from
                                                             ScaniaCRMExport.dbo.account

  4    address2\_city             nvarchar(320)      Yes     Column address2\_city from
                                                             ScaniaCRMExport.dbo.account

  5    Id                         uniqueidentifier   Yes     Column Id from
                                                             ScaniaCRMExport.dbo.account

  6    llp\_cantonid              uniqueidentifier   Yes     Column llp\_cantonid from
                                                             ScaniaCRMExport.dbo.account

  7    llp\_cantondid             uniqueidentifier   Yes     Column llp\_cantondid from
                                                             ScaniaCRMExport.dbo.account

  8    llp\_promisingas           int                Yes     Column llp\_promisingas from
                                                             ScaniaCRMExport.dbo.account

  9    llp\_promisingnv           int                Yes     Column llp\_promisingnv from
                                                             ScaniaCRMExport.dbo.account

  10   llp\_respactivesalesid     uniqueidentifier   Yes     Column llp\_respactivesalesid
                                                             from
                                                             ScaniaCRMExport.dbo.account

  11   llp\_respnewvehiclesid     uniqueidentifier   Yes     Column llp\_respnewvehiclesid
                                                             from
                                                             ScaniaCRMExport.dbo.account

  12   llp\_vatnumber             nvarchar(80)       Yes     Column llp\_vatnumber from
                                                             ScaniaCRMExport.dbo.account

  13   name                       nvarchar(640)      Yes     Column name from
                                                             ScaniaCRMExport.dbo.account

  14   ownerid                    uniqueidentifier   Yes     Column ownerid from
                                                             ScaniaCRMExport.dbo.account

  15   owningbusinessunit         uniqueidentifier   Yes     Column owningbusinessunit
                                                             from
                                                             ScaniaCRMExport.dbo.account

  16   statecode                  int                Yes     Column statecode from
                                                             ScaniaCRMExport.dbo.account

  17   wa\_registrationnumber     nvarchar(100)      Yes     Column wa\_registrationnumber
                                                             from
                                                             ScaniaCRMExport.dbo.account

  18   DataSourceId               int                Yes     Id of the data source the row
                                                             comes from

  19   ThreadLogId                int                Yes     Id of ThreadLog which
                                                             inserted the row
  ----------------------------------------------------------------------------------------

\[Back to table list\]\[listoftables\]
