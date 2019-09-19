Table Stage.CRMdboOptionSetMetadata {#tblStageCRMdboOptionSetMetadata}
-----------------------------------

Description:

Stage table CRMdboOptionSetMetadata.

List of dependent objects:

-   \[Stage.uspLoadCRMdboOptionSetMetadata\]\[spStageuspLoadCRMdboOptionSetMetadata\]

-   \[Vault.uspLoadCRMdboOptionSetMetadata\]\[spVaultuspLoadCRMdboOptionSetMetadata\]

  --------------------------------------------------------------------------------------------------
  Id   Column Name                  Data Type        Allow   Description
                                                     Nulls   
  ---- ---------------------------- ---------------- ------- ---------------------------------------
  1    EntityName                   nvarchar(256)    Yes     Column EntityName from
                                                             ScaniaCRMExport.dbo.OptionSetMetadata

  2    IsUserLocalizedLabel         bit              Yes     Column IsUserLocalizedLabel from
                                                             ScaniaCRMExport.dbo.OptionSetMetadata

  3    LocalizedLabel               nvarchar(1400)   Yes     Column LocalizedLabel from
                                                             ScaniaCRMExport.dbo.OptionSetMetadata

  4    LocalizedLabelLanguageCode   int              Yes     Column LocalizedLabelLanguageCode from
                                                             ScaniaCRMExport.dbo.OptionSetMetadata

  5    Option                       int              Yes     Column Option from
                                                             ScaniaCRMExport.dbo.OptionSetMetadata

  6    OptionSetName                nvarchar(256)    Yes     Column OptionSetName from
                                                             ScaniaCRMExport.dbo.OptionSetMetadata

  7    DataSourceId                 int              Yes     Id of the data source the row comes
                                                             from

  8    ThreadLogId                  int              Yes     Id of ThreadLog which inserted the row
  --------------------------------------------------------------------------------------------------

\[Back to table list\]\[listoftables\]
