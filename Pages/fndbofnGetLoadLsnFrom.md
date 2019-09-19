Function dbo.fnGetLoadLsnFrom {#fndbofnGetLoadLsnFrom}
-----------------------------

Description: Scalar function to get last loaded log sequence number for
Thread loaded in this ThreadLog.

### \[dbo.fnGetLoadLsnFrom\] - SQL\_SCALAR\_FUNCTION

Scalar function to get last loaded log sequence number for Thread loaded
in this ThreadLog. Definition of Function:

``` {.sql}
CREATE FUNCTION dbo.fnGetLoadLsnFrom
(
    @ThreadLogId int
)
RETURNS varbinary(10)
AS
BEGIN
    DECLARE @LoadLsnFrom varbinary(10)

    SELECT
    @LoadLsnFrom = MAX(LoadLsnTo)
    FROM Etl.ThreadLog WITH (NOLOCK)
    WHERE ThreadId = (SELECT ThreadId FROM Etl.ThreadLog WITH (NOLOCK) WHERE ThreadLogId = @ThreadLogId) AND StatusId = 3
    RETURN @LoadLsnFrom
END
```

\[Back to function list\]\[listoffunctions\]
