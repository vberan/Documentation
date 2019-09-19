Table Etl.ThreadLog {#tblEtlThreadLog}
-------------------

Description:

Etl table containing log of thread run.

List of dependent objects:

-   \[dbo.fnGetLoadDateFrom\]\[fndbofnGetLoadDateFrom\]

-   \[dbo.fnGetLoadLsnFrom\]\[fndbofnGetLoadLsnFrom\]

-   \[Etl.StageLastRun\]\[tblEtlStageLastRun\]

-   \[Etl.uspCreateFirstLoadQueue\]\[spEtluspCreateFirstLoadQueue\]

-   \[Etl.uspCreateFirstVaultLoad\]\[spEtluspCreateFirstVaultLoad\]

-   \[Etl.uspCreateQueue\]\[spEtluspCreateQueue\]

-   \[dbo.uspErrorHandler\]\[spdbouspErrorHandler\]

-   \[Stage.uspLoadCERTdboBusOrders\]\[spStageuspLoadCERTdboBusOrders\]

-   \[Vault.uspLoadCERTdboBusOrders\]\[spVaultuspLoadCERTdboBusOrders\]

-   \[Stage.uspLoadCERTdboCountry\]\[spStageuspLoadCERTdboCountry\]

-   \[Vault.uspLoadCERTdboCountry\]\[spVaultuspLoadCERTdboCountry\]

-   \[Stage.uspLoadCERTdboDealers\]\[spStageuspLoadCERTdboDealers\]

-   \[Vault.uspLoadCERTdboDealers\]\[spVaultuspLoadCERTdboDealers\]

-   \[Stage.uspLoadCERTdboOrders\]\[spStageuspLoadCERTdboOrders\]

-   \[Vault.uspLoadCERTdboOrders\]\[spVaultuspLoadCERTdboOrders\]

-   \[Stage.uspLoadCERTdboRenting\]\[spStageuspLoadCERTdboRenting\]

-   \[Vault.uspLoadCERTdboRenting\]\[spVaultuspLoadCERTdboRenting\]

-   \[Vault.uspLoadCERTdboUsers\]\[spVaultuspLoadCERTdboUsers\]

-   \[Stage.uspLoadCERTdboUsers\]\[spStageuspLoadCERTdboUsers\]

-   \[Stage.uspLoadCRMdboAccount\]\[spStageuspLoadCRMdboAccount\]

-   \[Vault.uspLoadCRMdboAccount\]\[spVaultuspLoadCRMdboAccount\]

-   \[Vault.uspLoadCRMdboAppointment\]\[spVaultuspLoadCRMdboAppointment\]

-   \[Stage.uspLoadCRMdboAppointment\]\[spStageuspLoadCRMdboAppointment\]

-   \[Stage.uspLoadCRMdboBusinessunit\]\[spStageuspLoadCRMdboBusinessunit\]

-   \[Vault.uspLoadCRMdboBusinessunit\]\[spVaultuspLoadCRMdboBusinessunit\]

-   \[Stage.uspLoadCRMdboEmail\]\[spStageuspLoadCRMdboEmail\]

-   \[Vault.uspLoadCRMdboEmail\]\[spVaultuspLoadCRMdboEmail\]

-   \[Vault.uspLoadCRMdboGlobalOptionSetMetadata\]\[spVaultuspLoadCRMdboGlobalOptionSetMetadata\]

-   \[Stage.uspLoadCRMdboGlobalOptionSetMetadata\]\[spStageuspLoadCRMdboGlobalOptionSetMetadata\]

-   \[Stage.uspLoadCRMdboLlp\_canton\]\[spStageuspLoadCRMdboLlp\_canton\]

-   \[Vault.uspLoadCRMdboLlp\_canton\]\[spVaultuspLoadCRMdboLlp\_canton\]

-   \[Vault.uspLoadCRMdboLlp\_country\]\[spVaultuspLoadCRMdboLlp\_country\]

-   \[Stage.uspLoadCRMdboLlp\_country\]\[spStageuspLoadCRMdboLlp\_country\]

-   \[Stage.uspLoadCRMdboOpportunity\]\[spStageuspLoadCRMdboOpportunity\]

-   \[Vault.uspLoadCRMdboOpportunity\]\[spVaultuspLoadCRMdboOpportunity\]

-   \[Vault.uspLoadCRMdboOptionSetMetadata\]\[spVaultuspLoadCRMdboOptionSetMetadata\]

-   \[Stage.uspLoadCRMdboOptionSetMetadata\]\[spStageuspLoadCRMdboOptionSetMetadata\]

-   \[Stage.uspLoadCRMdboPhonecall\]\[spStageuspLoadCRMdboPhonecall\]

-   \[Vault.uspLoadCRMdboPhonecall\]\[spVaultuspLoadCRMdboPhonecall\]

-   \[Vault.uspLoadCRMdboStateMetadata\]\[spVaultuspLoadCRMdboStateMetadata\]

-   \[Stage.uspLoadCRMdboStateMetadata\]\[spStageuspLoadCRMdboStateMetadata\]

-   \[Stage.uspLoadCRMdboStatusMetadata\]\[spStageuspLoadCRMdboStatusMetadata\]

-   \[Vault.uspLoadCRMdboStatusMetadata\]\[spVaultuspLoadCRMdboStatusMetadata\]

-   \[Vault.uspLoadCRMdboSystemuser\]\[spVaultuspLoadCRMdboSystemuser\]

-   \[Stage.uspLoadCRMdboSystemuser\]\[spStageuspLoadCRMdboSystemuser\]

-   \[Etl.uspStartBatch\]\[spEtluspStartBatch\]

-   \[Etl.uspUserLoad\]\[spEtluspUserLoad\]

-   \[Etl.VaultLastRun\]\[tblEtlVaultLastRun\]

  ----------------------------------------------------------------------------------
  Id   Column Name                Data Type       Allow   Description
                                                  Nulls   
  ---- -------------------------- --------------- ------- --------------------------
  1    ThreadLogId                int             Yes     Etl Thread Log identifier.

  2    RequestId                  int             Yes     Etl Request identifier.

  3    ThreadId                   int             Yes     Etl Thread identifier.

  4    BatchId                    int             Yes     Etl Batch identifier.

  5    StatusId                   int             Yes     Etl Status of thread log
                                                          identifier.

  6    ScheduledTime              datetime2       Yes     Time on when was thread
                                                          sheduled.

  7    StartTime                  datetime2       Yes     Time when thread started
                                                          its process.

  8    EndTime                    datetime2       Yes     Time when thread ended its
                                                          process.

  9    TableInitialRowCount       bigint          Yes     Initial count of rows in
                                                          loaded table.

  10   ExtractRowCount            bigint          Yes     Count of rows extracted by
                                                          process.

  11   InsertRowCount             bigint          Yes     Count of inseted rows into
                                                          loaded table.

  12   UpdateRowCount             bigint          Yes     Count of updated rows in
                                                          loaded table.

  13   DeleteRowCount             bigint          Yes     Count of deleted rows in
                                                          loaded table.

  14   ErrorRowCount              bigint          Yes     Count of rows containing
                                                          error.

  15   TableFinalRowCount         bigint          Yes     Final number of rows in
                                                          loaded table.

  16   LoadDateIdFrom             int             Yes     Min DateId of data loaded
                                                          into table (YYYYMMDD).

  17   LoadDateIdTo               int             Yes     Max DateId of data loaded
                                                          into table (YYYYMMDD).

  18   LoadDateFrom               datetime2       Yes     Min datetime of data
                                                          loaded into table.

  19   LoadDateTo                 datetime2       Yes     Max datetime of data
                                                          loaded into table.

  20   LoadLsnFrom                varbinary       Yes     Min log sequence number of
                                                          rows loaded into table.

  21   LoadLsnTo                  varbinary       Yes     Max log sequence number of
                                                          rows loaded into table.

  22   LoadChangeVersionFrom      int             Yes     Min change version of rows
                                                          loaded into table.

  23   LoadChangeVersionTo        int             Yes     Max change version of rows
                                                          loaded into table.

  24   ErrorNumber                int             Yes     Number from
                                                          ERROR\_NUMBER() function

  25   ErrorMessage               nvarchar(max)   Yes     Number from
                                                          ERROR\_MESSAGE() function

  26   ErrorSeverity              int             Yes     Number from
                                                          ERROR\_SEVERITY() function

  27   ErrorState                 int             Yes     Number from ERROR\_STATE()
                                                          function
  ----------------------------------------------------------------------------------

\[Back to table list\]\[listoftables\]
