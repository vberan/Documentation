Table Admin.DwParameter {#tblAdminDwParameter}
-----------------------

Description:

Admin table defining admin parameter's values

List of dependent objects:

-   \[Etl.uspCreateFirstVaultLoad\]\[spEtluspCreateFirstVaultLoad\]

-   \[Etl.uspCreateQueue\]\[spEtluspCreateQueue\]

-   \[Etl.uspStartBatch\]\[spEtluspStartBatch\]

  Id   Column Name      Data Type       Allow Nulls   Description
  ---- ---------------- --------------- ------------- ------------------------
  1    ParameterName    nvarchar(100)   Yes           Name of the parameter
  2    ParameterValue   nvarchar(200)   Yes           Value of teh parameter

\[Back to table list\]\[listoftables\]
