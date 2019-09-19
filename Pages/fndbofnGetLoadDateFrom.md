Function dbo.fnGetLoadDateFrom {#fndbofnGetLoadDateFrom}
------------------------------

Description: Scalar function to get last loaded LoadToDate for Thread
loaded in this ThreadLog.

### \[dbo.fnGetLoadDateFrom\] - SQL\_SCALAR\_FUNCTION

Scalar function to get last loaded LoadToDate for Thread loaded in this
ThreadLog. Definition of Function:

``` {.sql}
CREATE FUNCTION dbo.fnGetLoadDateFrom
(
    @ThreadLogId int
)
RETURNS datetime2
AS
BEGIN
    DECLARE @LoadDateFrom datetime2

    SELECT
    @LoadDateFrom = COALESCE(MAX(LoadDateTo), '1901-01-01')
    FROM Etl.ThreadLog WITH (NOLOCK)
    WHERE ThreadId = (SELECT ThreadId FROM Etl.ThreadLog WITH (NOLOCK) WHERE ThreadLogId = @ThreadLogId) AND StatusId = 3
    RETURN @LoadDateFrom
END
```

\[Back to function list\]\[listoffunctions\]
