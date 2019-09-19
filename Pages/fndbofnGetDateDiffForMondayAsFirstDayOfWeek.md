Function dbo.fnGetDateDiffForMondayAsFirstDayOfWeek {#fndbofnGetDateDiffForMondayAsFirstDayOfWeek}
---------------------------------------------------

Description: Scalar function to get datediff between dateFrom and dateTo
variables with Monday as first day of week.

List of dependent objects: dbo.Weekly Average Accounts Visited NV,
dbo.Weekly Average Accounts Visited Service, dbo.Weekly Average Visits
NV, dbo.Weekly Average Visits Service

### \[dbo.fnGetDateDiffForMondayAsFirstDayOfWeek\] - SQL\_SCALAR\_FUNCTION

Scalar function to get datediff between dateFrom and dateTo variables
with Monday as first day of week. Definition of Function:

``` {.sql}
CREATE FUNCTION dbo.fnGetDateDiffForMondayAsFirstDayOfWeek
(
    @dateFrom date
    , @dateTo date
)
RETURNS int

AS
    BEGIN
    DECLARE @FirstDayOfWeek int = 1

    DECLARE @DateDiff int
    
    SELECT @DateDiff = 
    DATEDIFF(
        week
        , DATEADD(dd,(@@DATEFIRST -1 - @FirstDayOfWeek )%7 + 1,@dateFrom)
        , DATEADD(dd,(@@DATEFIRST -1 - @FirstDayOfWeek )%7 + 1,@dateTo)
    )
    
    RETURN @DateDiff;
END;
```

\[Back to function list\]\[listoffunctions\]
