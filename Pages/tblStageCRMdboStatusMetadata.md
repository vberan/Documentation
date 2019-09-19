Table Stage.CRMdboStatusMetadata {#tblStageCRMdboStatusMetadata}
--------------------------------

Description:

Stage table CRMdboStatusMetadata.

List of dependent objects:

-   \[Stage.uspLoadCRMdboStatusMetadata\]\[spStageuspLoadCRMdboStatusMetadata\]

-   \[Vault.uspLoadCRMdboStatusMetadata\]\[spVaultuspLoadCRMdboStatusMetadata\]

  -----------------------------------------------------------------------------------------------
  Id   Column Name                  Data Type        Allow   Description
                                                     Nulls   
  ---- ---------------------------- ---------------- ------- ------------------------------------
  1    EntityName                   nvarchar(256)    Yes     Column EntityName from
                                                             ScaniaCRMExport.dbo.StatusMetadata

  2    IsUserLocalizedLabel         bit              Yes     Column IsUserLocalizedLabel from
                                                             ScaniaCRMExport.dbo.StatusMetadata

  3    LocalizedLabel               nvarchar(1400)   Yes     Column LocalizedLabel from
                                                             ScaniaCRMExport.dbo.StatusMetadata

  4    LocalizedLabelLanguageCode   int              Yes     Column LocalizedLabelLanguageCode
                                                             from
                                                             ScaniaCRMExport.dbo.StatusMetadata

  5    State                        int              Yes     Column State from
                                                             ScaniaCRMExport.dbo.StatusMetadata

  6    Status                       int              Yes     Column Status from
                                                             ScaniaCRMExport.dbo.StatusMetadata

  7    DataSourceId                 int              Yes     Id of the data source the row comes
                                                             from

  8    ThreadLogId                  int              Yes     Id of ThreadLog which inserted the
                                                             row
  -----------------------------------------------------------------------------------------------

\[Back to table list\]\[listoftables\]
