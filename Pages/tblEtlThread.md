Table Etl.Thread {#tblEtlThread}
----------------

Description:

Etl table containing list of Threads.

List of dependent objects:

-   \[Etl.StageLastRun\]\[tblEtlStageLastRun\]

-   \[Etl.uspCreateFirstLoadQueue\]\[spEtluspCreateFirstLoadQueue\]

-   \[Etl.uspCreateFirstVaultLoad\]\[spEtluspCreateFirstVaultLoad\]

-   \[Etl.uspUserLoad\]\[spEtluspUserLoad\]

-   \[Etl.VaultLastRun\]\[tblEtlVaultLastRun\]

  Id   Column Name         Data Type        Allow Nulls   Description
  ---- ------------------- ---------------- ------------- -----------------------------------------
  1    ThreadId            int              Yes           Etl Thread inentifier.
  2    LoadFrequency       int              Yes           Frequency of thread loading in minutes.
  3    LoadObjectName      nvarchar(1000)   Yes           Name of object that Thread loads.
  4    ExecObjectName      nvarchar(1000)   Yes           Name of object that is executed.
  5    DwLevelId           int              Yes           Etl Dw Level identifier.
  6    IncrementMethodId   int              Yes           Etl Increment Method identifier.
  7    DataSourceId        int              Yes           Etl Data Source identifier.

\[Back to table list\]\[listoftables\]
