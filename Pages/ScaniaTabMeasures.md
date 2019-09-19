Measures of tabular model ScaniaTab {#ScaniaTabMeasures}
===================================

Buses Sold (current year)
-------------------------

Definition:

``` {.dax}
CALCULATE(COUNT('Bus Order'[Bus Order ID]), YEAR('Bus Order'[Sales Date]) = YEAR(TODAY()))
```

-   \[Bus Order\]\[viewdboBusOrder\]

Buses Delivered (current year)
------------------------------

Definition:

``` {.dax}
CALCULATE(COUNT('Bus Order'[Bus Order ID]), YEAR('Bus Order'[Delivery Customer Date]) = YEAR(TODAY()))
```

-   \[Bus Order\]\[viewdboBusOrder\]

Fresh Opp
---------

Definition:

``` {.dax}
DISTINCTCOUNT('Fresh Opportunity'[Opportunity ID])
```

-   \[Fresh Opportunity\]\[viewdboFreshOpportunity\]

Fresh Offered Units
-------------------

Definition:

``` {.dax}
SUM('Fresh Opportunity'[Number Of Trucks])
```

-   \[Fresh Opportunity\]\[viewdboFreshOpportunity\]

Sales (current year)
--------------------

Definition:

``` {.dax}
CALCULATE(COUNT('New Truck Order'[Order ID]), YEAR('New Truck Order'[Sales Date]) = YEAR(TODAY()))
```

-   \[New Truck Order\]\[viewdboNewTruckOrder\]

Deliveries (current year)
-------------------------

Definition:

``` {.dax}
CALCULATE(COUNT('New Truck Order'[Order ID]), YEAR('New Truck Order'[Delivery Customer Date]) = YEAR(TODAY()))
```

-   \[New Truck Order\]\[viewdboNewTruckOrder\]

Order Stock (actual)
--------------------

Definition:

``` {.dax}
CALCULATE(COUNT('New Truck Order'[Order ID]), 'New Truck Order'[Sales Date] <> BLANK(), 'New Truck Order'[Delivery Customer Date] = BLANK())
```

-   \[New Truck Order\]\[viewdboNewTruckOrder\]

Rent Activations (current year)
-------------------------------

Definition:

``` {.dax}
CALCULATE(
    DISTINCTCOUNT('Rent Vehicle'[Vehicle ID])
    , YEAR('Rent Vehicle'[Rent Start Date]) = YEAR(TODAY())
    , 'Rent Vehicle'[Rent Start Date] <= TODAY()
    , 'Rent Vehicle'[Vehicle First Time] = 1
)
```

-   \[Rent Vehicle\]\[viewdboRentVehicle\]

Perspective Accounts Not Visited (5m)
-------------------------------------

Definition:

``` {.dax}

CALCULATE (
    DISTINCTCOUNT ( 'Account'[Account ID] )
    , 'Account'[State Code] = 0
, 'Account'[Is Promising New Vehicle] = 1
, OR('Account'[Days From Last Appointment] > 150, ISBLANK('Account'[Days From Last Appointment]))
)
```

-   \[Account\]\[viewdboAccount\]

Accounts Visited Last Week
--------------------------

Definition:

``` {.dax}
CALCULATE(
        DISTINCTCOUNT('Activity'[Account ID])
        , 'Activity'[Activity State] = 1
        , 'Activity'[Account State] = 0
                                , 'Activity'[Activity] = "app"
        , IF(TODAY() < 'Activity'[Activity Start Date], BLANK(), DATEDIFF('Activity'[Activity Start Date], TODAY(), DAY) <= 7)
        , IF(TODAY() < 'Activity'[Activity Start Date], BLANK(), DATEDIFF('Activity'[Activity Start Date], TODAY(), DAY) > 0)
    )
```

-   \[Activity\]\[viewdboActivity\]

Visits Last Week
----------------

Definition:

``` {.dax}
CALCULATE(
        DISTINCTCOUNT('Activity'[Appointment ID])
        , 'Activity'[Activity State] = 1
        , 'Activity'[Account State] = 0
                                , 'Activity'[Activity] = "app"
        , IF(TODAY() < 'Activity'[Activity Start Date], BLANK(), DATEDIFF('Activity'[Activity Start Date], TODAY(), DAY) <= 7)
        , IF(TODAY() < 'Activity'[Activity Start Date], BLANK(), DATEDIFF('Activity'[Activity Start Date], TODAY(), DAY) > 0)
)
```

-   \[Activity\]\[viewdboActivity\]

Visits Last Week With Comment
-----------------------------

Definition:

``` {.dax}
CALCULATE(
        DISTINCTCOUNT('Activity'[Appointment ID])
        , 'Activity'[Activity State] = 1
        , 'Activity'[Account State] = 0
                                , 'Activity'[Activity] = "app"
        , IF(TODAY() < 'Activity'[Activity Start Date], BLANK(), DATEDIFF('Activity'[Activity Start Date], TODAY(), DAY) <= 7)
        , IF(TODAY() < 'Activity'[Activity Start Date], BLANK(), DATEDIFF('Activity'[Activity Start Date], TODAY(), DAY) > 0)
        , 'Activity'[Appointment Description] <> BLANK()
    )
```

-   \[Activity\]\[viewdboActivity\]

Accounts Planned Visits Next Week
---------------------------------

Definition:

``` {.dax}
CALCULATE(
        DISTINCTCOUNT('Activity'[Account ID])
        , OR('Activity'[Activity State] = 0, 'Activity'[Activity State] = 3)
        , 'Activity'[Account State] = 0
                                , 'Activity'[Activity] = "app"
        , IF(TODAY() >= 'Activity'[Activity Start Date], BLANK(), DATEDIFF(TODAY(), 'Activity'[Activity Start Date], DAY) < 7)
        , IF(TODAY() >= 'Activity'[Activity Start Date], BLANK(), DATEDIFF(TODAY(), 'Activity'[Activity Start Date], DAY) >= 0)
    )
```

-   \[Activity\]\[viewdboActivity\]

Perspective Accounts Planned Activities
---------------------------------------

Definition:

``` {.dax}
CALCULATE(
        DISTINCTCOUNT('Activity'[Account ID])
        , 'Activity'[Account State] = 0
        , OR('Activity'[Activity State] = 0, 'Activity'[Activity State] = 3)
        , 'Activity'[Is Promising New Vehicle] = 1
                                , 'Activity'[Activity Start Date] >= TODAY()

    )
```

-   \[Activity\]\[viewdboActivity\]

Number of Perspective Accounts
------------------------------

Definition:

``` {.dax}
CALCULATE(
        DISTINCTCOUNT('Account'[Account ID])
        , 'Account'[State Code] = 0
        , 'Account'[Is Promising New Vehicle] = 1
    )
```

-   \[Account\]\[viewdboAccount\]

Perspective Accounts Not Visited (5m) Service
---------------------------------------------

Definition:

``` {.dax}
CALCULATE (
    DISTINCTCOUNT ( 'Account Service'[Account ID] )
    , 'Account Service'[State Code] = 0
, 'Account Service'[Is Promising Services] = 1
, OR('Account Service'[Days From Last Appointment] > 150, ISBLANK('Account Service'[Days From Last Appointment]))
)
```

-   \[Account Service\]\[viewdboAccountService\]

Accounts Visited Last Week Service
----------------------------------

Definition:

``` {.dax}
CALCULATE(
        DISTINCTCOUNT('Activity Service'[Account ID])
        , 'Activity Service'[Activity State] = 1
        , 'Activity Service'[Account State] = 0
                                , 'Activity Service'[Activity] = "app"
        , IF(TODAY() < 'Activity Service'[Activity Start Date], BLANK(), DATEDIFF('Activity Service'[Activity Start Date], TODAY(), DAY) <= 7)
        , IF(TODAY() < 'Activity Service'[Activity Start Date], BLANK(), DATEDIFF('Activity Service'[Activity Start Date], TODAY(), DAY) > 0)
    )
```

-   \[Activity Service\]\[viewdboActivityService\]

Visits Last Week Service
------------------------

Definition:

``` {.dax}
CALCULATE(
        DISTINCTCOUNT('Activity Service'[Appointment ID])
        , 'Activity Service'[Activity State] = 1
        , 'Activity Service'[Account State] = 0
                                , 'Activity Service'[Activity] = "app"
        , IF(TODAY() < 'Activity Service'[Activity Start Date], BLANK(), DATEDIFF('Activity Service'[Activity Start Date], TODAY(), DAY) <= 7)
        , IF(TODAY() < 'Activity Service'[Activity Start Date], BLANK(), DATEDIFF('Activity Service'[Activity Start Date], TODAY(), DAY) > 0)
)
```

-   \[Activity Service\]\[viewdboActivityService\]

Visits Last Week With Comment Service
-------------------------------------

Definition:

``` {.dax}
CALCULATE(
        DISTINCTCOUNT('Activity Service'[Appointment ID])
        , 'Activity Service'[Activity State] = 1
        , 'Activity Service'[Account State] = 0
                                , 'Activity Service'[Activity] = "app"
        , IF(TODAY() < 'Activity Service'[Activity Start Date], BLANK(), DATEDIFF('Activity Service'[Activity Start Date], TODAY(), DAY) <= 7)
        , IF(TODAY() < 'Activity Service'[Activity Start Date], BLANK(), DATEDIFF('Activity Service'[Activity Start Date], TODAY(), DAY) > 0)
        , 'Activity Service'[Appointment Description] <> BLANK()
    )
```

-   \[Activity Service\]\[viewdboActivityService\]

Accounts Planned Visits Next Week Service
-----------------------------------------

Definition:

``` {.dax}
CALCULATE(
        DISTINCTCOUNT('Activity Service'[Account ID])
        , OR('Activity Service'[Activity State] = 0, 'Activity Service'[Activity State] = 3)
        , 'Activity Service'[Account State] = 0
                                , 'Activity Service'[Activity] = "app"
        , IF(TODAY() >= 'Activity Service'[Activity Start Date], BLANK(), DATEDIFF(TODAY(), 'Activity Service'[Activity Start Date], DAY) < 7)
                                , IF(TODAY() >= 'Activity Service'[Activity Start Date], BLANK(), DATEDIFF(TODAY(), 'Activity Service'[Activity Start Date], DAY) >= 0)
    )
```

-   \[Activity Service\]\[viewdboActivityService\]

Perspective Accounts Planned Activities Service
-----------------------------------------------

Definition:

``` {.dax}
CALCULATE(
        DISTINCTCOUNT('Activity Service'[Account ID])
        , 'Activity Service'[Account State] = 0
                                , OR('Activity Service'[Activity State] = 0, 'Activity Service'[Activity State] = 3)
        , 'Account Service'[Is Promising Services] = 1
                                , 'Activity Service'[Activity Start Date] >= TODAY()

    )
```

-   \[Account Service\]\[viewdboAccountService\]

-   \[Activity Service\]\[viewdboActivityService\]

Number of Perspective Accounts Service
--------------------------------------

Definition:

``` {.dax}
CALCULATE(
        DISTINCTCOUNT('Account Service'[Account ID])
        , 'Account Service'[State Code] = 0
        , 'Account Service'[Is Promising Services] = 1
    )
```

-   \[Account Service\]\[viewdboAccountService\]

Weekly Average Accounts Visited (5m) Service
--------------------------------------------

Definition:

``` {.dax}
CALCULATE(
    DISTINCTCOUNT('Account Service'[Account ID])
    , 'Account Service'[State Code] = 0
    , 'Activity Service'[Activity State] = 1
    , 'Activity Service'[Activity] = "app"
)
```

-   \[Account Service\]\[viewdboAccountService\]

-   \[Activity Service\]\[viewdboActivityService\]

Fresh Opp Services
------------------

Definition:

``` {.dax}
DISTINCTCOUNT('Fresh Opportunity Service'[Opportunity ID])
```

-   \[Fresh Opportunity Service\]\[viewdboFreshOpportunityService\]

Fresh Offered Units Service
---------------------------

Definition:

``` {.dax}
SUM('Fresh Opportunity Service'[Number Of Trucks])
```

-   \[Fresh Opportunity Service\]\[viewdboFreshOpportunityService\]
