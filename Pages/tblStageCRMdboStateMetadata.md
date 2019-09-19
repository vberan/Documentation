Table Stage.CRMdboStateMetadata {#tblStageCRMdboStateMetadata}
-------------------------------

Description:

Stage table CRMdboStateMetadata.

List of dependent objects:

-   \[Stage.uspLoadCRMdboStateMetadata\]\[spStageuspLoadCRMdboStateMetadata\]

-   \[Vault.uspLoadCRMdboStateMetadata\]\[spVaultuspLoadCRMdboStateMetadata\]

  ----------------------------------------------------------------------------------------------
  Id   Column Name                  Data Type        Allow   Description
                                                     Nulls   
  ---- ---------------------------- ---------------- ------- -----------------------------------
  1    EntityName                   nvarchar(256)    Yes     Column EntityName from
                                                             ScaniaCRMExport.dbo.StateMetadata

  2    IsUserLocalizedLabel         bit              Yes     Column IsUserLocalizedLabel from
                                                             ScaniaCRMExport.dbo.StateMetadata

  3    LocalizedLabel               nvarchar(1400)   Yes     Column LocalizedLabel from
                                                             ScaniaCRMExport.dbo.StateMetadata

  4    LocalizedLabelLanguageCode   int              Yes     Column LocalizedLabelLanguageCode
                                                             from
                                                             ScaniaCRMExport.dbo.StateMetadata

  5    State                        int              Yes     Column State from
                                                             ScaniaCRMExport.dbo.StateMetadata

  6    DataSourceId                 int              Yes     Id of the data source the row comes
                                                             from

  7    ThreadLogId                  int              Yes     Id of ThreadLog which inserted the
                                                             row
  ----------------------------------------------------------------------------------------------

\[Back to table list\]\[listoftables\]
