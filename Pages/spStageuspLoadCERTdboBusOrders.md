Stored Procedure Stage.uspLoadCERTdboBusOrders {#spStageuspLoadCERTdboBusOrders}
----------------------------------------------

Definition of Stored procedure:

``` {.sql}
CREATE PROCEDURE [Stage].[uspLoadCERTdboBusOrders] 
    @ThreadLogId int
        , @DataSourceId int
    AS
    BEGIN TRY
        -- set up the enviroment
        SET NOCOUNT ON;
    

        TRUNCATE TABLE [Stage].[CERTdboBusOrders]; 

        -- log the initial table state
        UPDATE Etl.ThreadLog
            SET TableInitialRowCount = (SELECT COUNT(*) FROM [Stage].[CERTdboBusOrders] WITH (NOLOCK))
        WHERE ThreadLogId = @ThreadLogId;

        DECLARE @loadDateFrom datetime2;
        SELECT @loadDateFrom = '1901-01-01';

        INSERT INTO [Stage].[CERTdboBusOrders]
            ( 
                [ACC]
                , [ActualDealerDate]
                , [AEB]
                , [BuyBackDate]
                , [CDD]
                , [CDDC]
                , [Cost]
                , [CustomerPrice]
                , [CustomerTemporary]
                , [DateOUT]
                , [DeliveryCustomerDate]
                , [DistributorID]
                , [DistributorOrderID]
                , [EngineNumber]
                , [EXWsupport]
                , [HighServiceLevel]
                , [ChassisNumber]
                , [ChassisONLYcontracted]
                , [ChassisType]
                , [ChassisWeight]
                , [ID_BusModel]
                , [ID_CurrentBusLocation]
                , [ID_Customer]
                , [ID_Destinace]
                , [ID_Emise]
                , [ID_InvoiceCountry]
                , [ID_ReservUser]
                , [ID_Status]
                , [ID_User]
                , [IDD_Bus]
                , [LastAddressChange]
                , [LDW]
                , [Margin]
                , [NET]
                , [ProdPeriod]
                , [Prodplant]
                , [PromisedDeliveryDate]
                , [PurchaseBody]
                , [PurchaseDateBody]
                , [PurchaseDateChassis]
                , [PurchaseChassis]
                , [ReInvoiceDate]
                , [Remark]
                , [ReservationEnd]
                , [ReservationStart]
                , [RVGamount]
                , [RVGsupport]
                , [SalesDate]
                , [ScaniaOrderNu]
                , [SEATS]
                , [SpecifDefiniteDate]
                , [UsedBus]
                , [VehicleLocation]
                , [VIN]
                , [DataSourceId]
                , [ThreadLogId]
    )

        SELECT 
                [ACC] = s.[ACC]
                , [ActualDealerDate] = s.[ActualDealerDate]
                , [AEB] = s.[AEB]
                , [BuyBackDate] = s.[BuyBackDate]
                , [CDD] = s.[CDD]
                , [CDDC] = s.[CDDC]
                , [Cost] = s.[Cost]
                , [CustomerPrice] = s.[CustomerPrice]
                , [CustomerTemporary] = s.[CustomerTemporary]
                , [DateOUT] = s.[DateOUT]
                , [DeliveryCustomerDate] = s.[DeliveryCustomerDate]
                , [DistributorID] = s.[DistributorID]
                , [DistributorOrderID] = s.[DistributorOrderID]
                , [EngineNumber] = s.[EngineNumber]
                , [EXWsupport] = s.[EXWsupport]
                , [HighServiceLevel] = s.[HighServiceLevel]
                , [ChassisNumber] = s.[ChassisNumber]
                , [ChassisONLYcontracted] = s.[ChassisONLYcontracted]
                , [ChassisType] = s.[ChassisType]
                , [ChassisWeight] = s.[ChassisWeight]
                , [ID_BusModel] = s.[ID_BusModel]
                , [ID_CurrentBusLocation] = s.[ID_CurrentBusLocation]
                , [ID_Customer] = s.[ID_Customer]
                , [ID_Destinace] = s.[ID_Destinace]
                , [ID_Emise] = s.[ID_Emise]
                , [ID_InvoiceCountry] = s.[ID_InvoiceCountry]
                , [ID_ReservUser] = s.[ID_ReservUser]
                , [ID_Status] = s.[ID_Status]
                , [ID_User] = s.[ID_User]
                , [IDD_Bus] = s.[IDD_Bus]
                , [LastAddressChange] = s.[LastAddressChange]
                , [LDW] = s.[LDW]
                , [Margin] = s.[Margin]
                , [NET] = s.[NET]
                , [ProdPeriod] = s.[ProdPeriod]
                , [Prodplant] = s.[Prodplant]
                , [PromisedDeliveryDate] = s.[PromisedDeliveryDate]
                , [PurchaseBody] = s.[PurchaseBody]
                , [PurchaseDateBody] = s.[PurchaseDateBody]
                , [PurchaseDateChassis] = s.[PurchaseDateChassis]
                , [PurchaseChassis] = s.[PurchaseChassis]
                , [ReInvoiceDate] = s.[ReInvoiceDate]
                , [Remark] = s.[Remark]
                , [ReservationEnd] = s.[ReservationEnd]
                , [ReservationStart] = s.[ReservationStart]
                , [RVGamount] = s.[RVGamount]
                , [RVGsupport] = s.[RVGsupport]
                , [SalesDate] = s.[SalesDate]
                , [ScaniaOrderNu] = s.[ScaniaOrderNu]
                , [SEATS] = s.[SEATS]
                , [SpecifDefiniteDate] = s.[SpecifDefiniteDate]
                , [UsedBus] = s.[UsedBus]
                , [VehicleLocation] = s.[VehicleLocation]
                , [VIN] = s.[VIN]
                , [DataSourceId] = @DataSourceId
                , [ThreadLogId] = @ThreadLogId
    
        FROM [CERTST10].[CERT].[dbo].[BusOrders] AS s WITH (NOLOCK)

        --Log ThreadLog Success
        UPDATE Etl.ThreadLog
        SET ExtractRowCount = (SELECT COUNT(*) FROM [Stage].[CERTdboBusOrders] WITH (NOLOCK) WHERE ThreadLogId = @ThreadLogId)
            , InsertRowCount = (SELECT COUNT(*) FROM [Stage].[CERTdboBusOrders] WITH (NOLOCK) WHERE ThreadLogId = @ThreadLogId)
            , TableFinalRowCount = (SELECT COUNT(*) FROM [Stage].[CERTdboBusOrders] WITH (NOLOCK) )
            , EndTime = GETDATE()
            , LoadDateFrom = @loadDateFrom
            , LoadDateTo = GETDATE()
            , StatusId = 3
        WHERE ThreadLogId = @ThreadLogId;

        END TRY

        BEGIN CATCH
            EXEC [dbo].[uspErrorHandler] @ThreadLogId = @ThreadLogId;
        END CATCH
            
        RETURN;
```

\[Back to stored procedure list\]\[listofprocedures\]
