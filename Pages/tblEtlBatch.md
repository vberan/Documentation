Table Etl.Batch {#tblEtlBatch}
---------------

Description:

Etl table containing log of batch run.

List of dependent objects:

-   \[Etl.uspStartBatch\]\[spEtluspStartBatch\]

  Id   Column Name       Data Type   Allow Nulls   Description
  ---- ----------------- ----------- ------------- --------------------------------------------
  1    BatchId           int         Yes           Etl Batch identifier.
  2    CreatedTime       datetime2   Yes           Time when Batch was created.
  3    ClosedTime        datetime2   Yes           Time when Batch was closed by Etl process.
  4    NumberOfThreads   int         Yes           Number of threads requested in Etl Batch.
  5    SuccessCount      int         Yes           Number of successfully loaded Threads.
  6    ErrorCount        int         Yes           Number of Threads with error load.
  7    StatusId          int         Yes           Etl Status identifier.

\[Back to table list\]\[listoftables\]
