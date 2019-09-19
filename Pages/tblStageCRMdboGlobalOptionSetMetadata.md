Table Stage.CRMdboGlobalOptionSetMetadata {#tblStageCRMdboGlobalOptionSetMetadata}
-----------------------------------------

Description:

Stage table CRMdboGlobalOptionSetMetadata.

List of dependent objects:

-   \[Stage.uspLoadCRMdboGlobalOptionSetMetadata\]\[spStageuspLoadCRMdboGlobalOptionSetMetadata\]

-   \[Vault.uspLoadCRMdboGlobalOptionSetMetadata\]\[spVaultuspLoadCRMdboGlobalOptionSetMetadata\]

  --------------------------------------------------------------------------------------------------------
  Id   Column Name                  Data Type        Allow   Description
                                                     Nulls   
  ---- ---------------------------- ---------------- ------- ---------------------------------------------
  1    IsUserLocalizedLabel         bit              Yes     Column IsUserLocalizedLabel from
                                                             ScaniaCRMExport.dbo.GlobalOptionSetMetadata

  2    LocalizedLabel               nvarchar(1400)   Yes     Column LocalizedLabel from
                                                             ScaniaCRMExport.dbo.GlobalOptionSetMetadata

  3    LocalizedLabelLanguageCode   int              Yes     Column LocalizedLabelLanguageCode from
                                                             ScaniaCRMExport.dbo.GlobalOptionSetMetadata

  4    Option                       int              Yes     Column Option from
                                                             ScaniaCRMExport.dbo.GlobalOptionSetMetadata

  5    OptionSetName                nvarchar(256)    Yes     Column OptionSetName from
                                                             ScaniaCRMExport.dbo.GlobalOptionSetMetadata

  6    DataSourceId                 int              Yes     Id of the data source the row comes from

  7    ThreadLogId                  int              Yes     Id of ThreadLog which inserted the row
  --------------------------------------------------------------------------------------------------------

\[Back to table list\]\[listoftables\]
