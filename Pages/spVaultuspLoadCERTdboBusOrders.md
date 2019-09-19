Stored Procedure Vault.uspLoadCERTdboBusOrders {#spVaultuspLoadCERTdboBusOrders}
----------------------------------------------

Definition of Stored procedure:

``` {.sql}
CREATE PROCEDURE [Vault].[uspLoadCERTdboBusOrders] 
    @ThreadLogId int
        , @DataSourceId int
    AS
    BEGIN TRY
            -- set up the enviroment
            SET NOCOUNT ON;
            
            DECLARE @rowCounts TABLE
            (
                MergeAction nvarchar(10)
            );
            DECLARE @UpdateRowCounts TABLE
            (
                ThreadLogUpdateId int
            );
            DECLARE @DeleteRowCounts TABLE
            (
                ThreadLogDeleteId int
            );
    -- log the initial table state
        UPDATE Etl.ThreadLog
            SET TableInitialRowCount = (SELECT COUNT(*) FROM [Vault].[CERTdboBusOrders] WITH (NOLOCK))
        WHERE ThreadLogId = @ThreadLogId;

            BEGIN TRANSACTION;

    
        MERGE INTO [Vault].[CERTdboBusOrders] AS v
        USING [Stage].[CERTdboBusOrders] AS s
            ON ( s.[IDD_Bus] = v.[IDD_Bus]AND s.[DataSourceId] = v.[DataSourceId]
     AND v.[ThreadLogDeleteId] = -1 AND v.[ThreadLogUpdateId] = -1 AND v.[ChangeOperation] <> N'D'
    )

        WHEN MATCHED AND
            (
            v.[ACC] <> s.[ACC]
            OR v.[ActualDealerDate] <> s.[ActualDealerDate]
            OR (v.[ActualDealerDate] IS NULL AND s.[ActualDealerDate] IS NOT NULL)
        OR (v.[ActualDealerDate] IS NOT NULL AND s.[ActualDealerDate] IS NULL)
        OR v.[AEB] <> s.[AEB]
            OR v.[BuyBackDate] <> s.[BuyBackDate]
            OR (v.[BuyBackDate] IS NULL AND s.[BuyBackDate] IS NOT NULL)
        OR (v.[BuyBackDate] IS NOT NULL AND s.[BuyBackDate] IS NULL)
        OR v.[CDD] <> s.[CDD]
            OR (v.[CDD] IS NULL AND s.[CDD] IS NOT NULL)
        OR (v.[CDD] IS NOT NULL AND s.[CDD] IS NULL)
        OR v.[CDDC] <> s.[CDDC]
            OR (v.[CDDC] IS NULL AND s.[CDDC] IS NOT NULL)
        OR (v.[CDDC] IS NOT NULL AND s.[CDDC] IS NULL)
        OR v.[Cost] <> s.[Cost]
            OR (v.[Cost] IS NULL AND s.[Cost] IS NOT NULL)
        OR (v.[Cost] IS NOT NULL AND s.[Cost] IS NULL)
        OR v.[CustomerPrice] <> s.[CustomerPrice]
            OR (v.[CustomerPrice] IS NULL AND s.[CustomerPrice] IS NOT NULL)
        OR (v.[CustomerPrice] IS NOT NULL AND s.[CustomerPrice] IS NULL)
        OR v.[CustomerTemporary] <> s.[CustomerTemporary]
            OR (v.[CustomerTemporary] IS NULL AND s.[CustomerTemporary] IS NOT NULL)
        OR (v.[CustomerTemporary] IS NOT NULL AND s.[CustomerTemporary] IS NULL)
        OR v.[DateOUT] <> s.[DateOUT]
            OR (v.[DateOUT] IS NULL AND s.[DateOUT] IS NOT NULL)
        OR (v.[DateOUT] IS NOT NULL AND s.[DateOUT] IS NULL)
        OR v.[DeliveryCustomerDate] <> s.[DeliveryCustomerDate]
            OR (v.[DeliveryCustomerDate] IS NULL AND s.[DeliveryCustomerDate] IS NOT NULL)
        OR (v.[DeliveryCustomerDate] IS NOT NULL AND s.[DeliveryCustomerDate] IS NULL)
        OR v.[DistributorID] <> s.[DistributorID]
            OR (v.[DistributorID] IS NULL AND s.[DistributorID] IS NOT NULL)
        OR (v.[DistributorID] IS NOT NULL AND s.[DistributorID] IS NULL)
        OR v.[DistributorOrderID] <> s.[DistributorOrderID]
            OR (v.[DistributorOrderID] IS NULL AND s.[DistributorOrderID] IS NOT NULL)
        OR (v.[DistributorOrderID] IS NOT NULL AND s.[DistributorOrderID] IS NULL)
        OR v.[EngineNumber] <> s.[EngineNumber]
            OR (v.[EngineNumber] IS NULL AND s.[EngineNumber] IS NOT NULL)
        OR (v.[EngineNumber] IS NOT NULL AND s.[EngineNumber] IS NULL)
        OR v.[EXWsupport] <> s.[EXWsupport]
            OR (v.[EXWsupport] IS NULL AND s.[EXWsupport] IS NOT NULL)
        OR (v.[EXWsupport] IS NOT NULL AND s.[EXWsupport] IS NULL)
        OR v.[HighServiceLevel] <> s.[HighServiceLevel]
            OR (v.[HighServiceLevel] IS NULL AND s.[HighServiceLevel] IS NOT NULL)
        OR (v.[HighServiceLevel] IS NOT NULL AND s.[HighServiceLevel] IS NULL)
        OR v.[ChassisNumber] <> s.[ChassisNumber]
            OR (v.[ChassisNumber] IS NULL AND s.[ChassisNumber] IS NOT NULL)
        OR (v.[ChassisNumber] IS NOT NULL AND s.[ChassisNumber] IS NULL)
        OR v.[ChassisONLYcontracted] <> s.[ChassisONLYcontracted]
            OR v.[ChassisType] <> s.[ChassisType]
            OR (v.[ChassisType] IS NULL AND s.[ChassisType] IS NOT NULL)
        OR (v.[ChassisType] IS NOT NULL AND s.[ChassisType] IS NULL)
        OR v.[ChassisWeight] <> s.[ChassisWeight]
            OR (v.[ChassisWeight] IS NULL AND s.[ChassisWeight] IS NOT NULL)
        OR (v.[ChassisWeight] IS NOT NULL AND s.[ChassisWeight] IS NULL)
        OR v.[ID_BusModel] <> s.[ID_BusModel]
            OR (v.[ID_BusModel] IS NULL AND s.[ID_BusModel] IS NOT NULL)
        OR (v.[ID_BusModel] IS NOT NULL AND s.[ID_BusModel] IS NULL)
        OR v.[ID_CurrentBusLocation] <> s.[ID_CurrentBusLocation]
            OR (v.[ID_CurrentBusLocation] IS NULL AND s.[ID_CurrentBusLocation] IS NOT NULL)
        OR (v.[ID_CurrentBusLocation] IS NOT NULL AND s.[ID_CurrentBusLocation] IS NULL)
        OR v.[ID_Customer] <> s.[ID_Customer]
            OR (v.[ID_Customer] IS NULL AND s.[ID_Customer] IS NOT NULL)
        OR (v.[ID_Customer] IS NOT NULL AND s.[ID_Customer] IS NULL)
        OR v.[ID_Destinace] <> s.[ID_Destinace]
            OR (v.[ID_Destinace] IS NULL AND s.[ID_Destinace] IS NOT NULL)
        OR (v.[ID_Destinace] IS NOT NULL AND s.[ID_Destinace] IS NULL)
        OR v.[ID_Emise] <> s.[ID_Emise]
            OR (v.[ID_Emise] IS NULL AND s.[ID_Emise] IS NOT NULL)
        OR (v.[ID_Emise] IS NOT NULL AND s.[ID_Emise] IS NULL)
        OR v.[ID_InvoiceCountry] <> s.[ID_InvoiceCountry]
            OR (v.[ID_InvoiceCountry] IS NULL AND s.[ID_InvoiceCountry] IS NOT NULL)
        OR (v.[ID_InvoiceCountry] IS NOT NULL AND s.[ID_InvoiceCountry] IS NULL)
        OR v.[ID_ReservUser] <> s.[ID_ReservUser]
            OR (v.[ID_ReservUser] IS NULL AND s.[ID_ReservUser] IS NOT NULL)
        OR (v.[ID_ReservUser] IS NOT NULL AND s.[ID_ReservUser] IS NULL)
        OR v.[ID_Status] <> s.[ID_Status]
            OR (v.[ID_Status] IS NULL AND s.[ID_Status] IS NOT NULL)
        OR (v.[ID_Status] IS NOT NULL AND s.[ID_Status] IS NULL)
        OR v.[ID_User] <> s.[ID_User]
            OR (v.[ID_User] IS NULL AND s.[ID_User] IS NOT NULL)
        OR (v.[ID_User] IS NOT NULL AND s.[ID_User] IS NULL)
        OR v.[LastAddressChange] <> s.[LastAddressChange]
            OR (v.[LastAddressChange] IS NULL AND s.[LastAddressChange] IS NOT NULL)
        OR (v.[LastAddressChange] IS NOT NULL AND s.[LastAddressChange] IS NULL)
        OR v.[LDW] <> s.[LDW]
            OR v.[Margin] <> s.[Margin]
            OR (v.[Margin] IS NULL AND s.[Margin] IS NOT NULL)
        OR (v.[Margin] IS NOT NULL AND s.[Margin] IS NULL)
        OR v.[NET] <> s.[NET]
            OR (v.[NET] IS NULL AND s.[NET] IS NOT NULL)
        OR (v.[NET] IS NOT NULL AND s.[NET] IS NULL)
        OR v.[ProdPeriod] <> s.[ProdPeriod]
            OR (v.[ProdPeriod] IS NULL AND s.[ProdPeriod] IS NOT NULL)
        OR (v.[ProdPeriod] IS NOT NULL AND s.[ProdPeriod] IS NULL)
        OR v.[Prodplant] <> s.[Prodplant]
            OR (v.[Prodplant] IS NULL AND s.[Prodplant] IS NOT NULL)
        OR (v.[Prodplant] IS NOT NULL AND s.[Prodplant] IS NULL)
        OR v.[PromisedDeliveryDate] <> s.[PromisedDeliveryDate]
            OR (v.[PromisedDeliveryDate] IS NULL AND s.[PromisedDeliveryDate] IS NOT NULL)
        OR (v.[PromisedDeliveryDate] IS NOT NULL AND s.[PromisedDeliveryDate] IS NULL)
        OR v.[PurchaseBody] <> s.[PurchaseBody]
            OR (v.[PurchaseBody] IS NULL AND s.[PurchaseBody] IS NOT NULL)
        OR (v.[PurchaseBody] IS NOT NULL AND s.[PurchaseBody] IS NULL)
        OR v.[PurchaseDateBody] <> s.[PurchaseDateBody]
            OR (v.[PurchaseDateBody] IS NULL AND s.[PurchaseDateBody] IS NOT NULL)
        OR (v.[PurchaseDateBody] IS NOT NULL AND s.[PurchaseDateBody] IS NULL)
        OR v.[PurchaseDateChassis] <> s.[PurchaseDateChassis]
            OR (v.[PurchaseDateChassis] IS NULL AND s.[PurchaseDateChassis] IS NOT NULL)
        OR (v.[PurchaseDateChassis] IS NOT NULL AND s.[PurchaseDateChassis] IS NULL)
        OR v.[PurchaseChassis] <> s.[PurchaseChassis]
            OR (v.[PurchaseChassis] IS NULL AND s.[PurchaseChassis] IS NOT NULL)
        OR (v.[PurchaseChassis] IS NOT NULL AND s.[PurchaseChassis] IS NULL)
        OR v.[ReInvoiceDate] <> s.[ReInvoiceDate]
            OR (v.[ReInvoiceDate] IS NULL AND s.[ReInvoiceDate] IS NOT NULL)
        OR (v.[ReInvoiceDate] IS NOT NULL AND s.[ReInvoiceDate] IS NULL)
        OR v.[Remark] <> s.[Remark]
            OR (v.[Remark] IS NULL AND s.[Remark] IS NOT NULL)
        OR (v.[Remark] IS NOT NULL AND s.[Remark] IS NULL)
        OR v.[ReservationEnd] <> s.[ReservationEnd]
            OR (v.[ReservationEnd] IS NULL AND s.[ReservationEnd] IS NOT NULL)
        OR (v.[ReservationEnd] IS NOT NULL AND s.[ReservationEnd] IS NULL)
        OR v.[ReservationStart] <> s.[ReservationStart]
            OR (v.[ReservationStart] IS NULL AND s.[ReservationStart] IS NOT NULL)
        OR (v.[ReservationStart] IS NOT NULL AND s.[ReservationStart] IS NULL)
        OR v.[RVGamount] <> s.[RVGamount]
            OR (v.[RVGamount] IS NULL AND s.[RVGamount] IS NOT NULL)
        OR (v.[RVGamount] IS NOT NULL AND s.[RVGamount] IS NULL)
        OR v.[RVGsupport] <> s.[RVGsupport]
            OR (v.[RVGsupport] IS NULL AND s.[RVGsupport] IS NOT NULL)
        OR (v.[RVGsupport] IS NOT NULL AND s.[RVGsupport] IS NULL)
        OR v.[SalesDate] <> s.[SalesDate]
            OR (v.[SalesDate] IS NULL AND s.[SalesDate] IS NOT NULL)
        OR (v.[SalesDate] IS NOT NULL AND s.[SalesDate] IS NULL)
        OR v.[ScaniaOrderNu] <> s.[ScaniaOrderNu]
            OR (v.[ScaniaOrderNu] IS NULL AND s.[ScaniaOrderNu] IS NOT NULL)
        OR (v.[ScaniaOrderNu] IS NOT NULL AND s.[ScaniaOrderNu] IS NULL)
        OR v.[SEATS] <> s.[SEATS]
            OR (v.[SEATS] IS NULL AND s.[SEATS] IS NOT NULL)
        OR (v.[SEATS] IS NOT NULL AND s.[SEATS] IS NULL)
        OR v.[SpecifDefiniteDate] <> s.[SpecifDefiniteDate]
            OR (v.[SpecifDefiniteDate] IS NULL AND s.[SpecifDefiniteDate] IS NOT NULL)
        OR (v.[SpecifDefiniteDate] IS NOT NULL AND s.[SpecifDefiniteDate] IS NULL)
        OR v.[UsedBus] <> s.[UsedBus]
            OR v.[VehicleLocation] <> s.[VehicleLocation]
            OR (v.[VehicleLocation] IS NULL AND s.[VehicleLocation] IS NOT NULL)
        OR (v.[VehicleLocation] IS NOT NULL AND s.[VehicleLocation] IS NULL)
        OR v.[VIN] <> s.[VIN]
            OR (v.[VIN] IS NULL AND s.[VIN] IS NOT NULL)
        OR (v.[VIN] IS NOT NULL AND s.[VIN] IS NULL)
        )
        THEN 
            UPDATE SET
                [ThreadLogUpdateId] = @ThreadLogId
            

                
        WHEN NOT MATCHED BY TARGET 
            THEN INSERT
            ( 
            [IDD_Bus]
            , [ACC]
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
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
            
    ) VALUES (
            s.[IDD_Bus]
            , s.[ACC]
            , s.[ActualDealerDate]
            , s.[AEB]
            , s.[BuyBackDate]
            , s.[CDD]
            , s.[CDDC]
            , s.[Cost]
            , s.[CustomerPrice]
            , s.[CustomerTemporary]
            , s.[DateOUT]
            , s.[DeliveryCustomerDate]
            , s.[DistributorID]
            , s.[DistributorOrderID]
            , s.[EngineNumber]
            , s.[EXWsupport]
            , s.[HighServiceLevel]
            , s.[ChassisNumber]
            , s.[ChassisONLYcontracted]
            , s.[ChassisType]
            , s.[ChassisWeight]
            , s.[ID_BusModel]
            , s.[ID_CurrentBusLocation]
            , s.[ID_Customer]
            , s.[ID_Destinace]
            , s.[ID_Emise]
            , s.[ID_InvoiceCountry]
            , s.[ID_ReservUser]
            , s.[ID_Status]
            , s.[ID_User]
            , s.[LastAddressChange]
            , s.[LDW]
            , s.[Margin]
            , s.[NET]
            , s.[ProdPeriod]
            , s.[Prodplant]
            , s.[PromisedDeliveryDate]
            , s.[PurchaseBody]
            , s.[PurchaseDateBody]
            , s.[PurchaseDateChassis]
            , s.[PurchaseChassis]
            , s.[ReInvoiceDate]
            , s.[Remark]
            , s.[ReservationEnd]
            , s.[ReservationStart]
            , s.[RVGamount]
            , s.[RVGsupport]
            , s.[SalesDate]
            , s.[ScaniaOrderNu]
            , s.[SEATS]
            , s.[SpecifDefiniteDate]
            , s.[UsedBus]
            , s.[VehicleLocation]
            , s.[VIN]
            , s.[DataSourceId]
            , @ThreadLogId
            , -1
            , -1
            , N'I' -- insert
        )
        WHEN NOT MATCHED BY SOURCE AND v.[ThreadLogDeleteId] = -1 AND v.[ThreadLogUpdateId] = -1 AND v.[ChangeOperation] <> N'D'
        THEN UPDATE
            SET 
                [ThreadLogDeleteId] = @ThreadLogId
    OUTPUT $ACTION INTO @rowCounts;
    
    INSERT INTO [Vault].[CERTdboBusOrders] (
            [IDD_Bus]
            , [ACC]
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
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
        
    ) 
    OUTPUT Inserted.ThreadLogUpdateId INTO @UpdateRowCounts
    SELECT

            s.[IDD_Bus]
            , s.[ACC]
            , s.[ActualDealerDate]
            , s.[AEB]
            , s.[BuyBackDate]
            , s.[CDD]
            , s.[CDDC]
            , s.[Cost]
            , s.[CustomerPrice]
            , s.[CustomerTemporary]
            , s.[DateOUT]
            , s.[DeliveryCustomerDate]
            , s.[DistributorID]
            , s.[DistributorOrderID]
            , s.[EngineNumber]
            , s.[EXWsupport]
            , s.[HighServiceLevel]
            , s.[ChassisNumber]
            , s.[ChassisONLYcontracted]
            , s.[ChassisType]
            , s.[ChassisWeight]
            , s.[ID_BusModel]
            , s.[ID_CurrentBusLocation]
            , s.[ID_Customer]
            , s.[ID_Destinace]
            , s.[ID_Emise]
            , s.[ID_InvoiceCountry]
            , s.[ID_ReservUser]
            , s.[ID_Status]
            , s.[ID_User]
            , s.[LastAddressChange]
            , s.[LDW]
            , s.[Margin]
            , s.[NET]
            , s.[ProdPeriod]
            , s.[Prodplant]
            , s.[PromisedDeliveryDate]
            , s.[PurchaseBody]
            , s.[PurchaseDateBody]
            , s.[PurchaseDateChassis]
            , s.[PurchaseChassis]
            , s.[ReInvoiceDate]
            , s.[Remark]
            , s.[ReservationEnd]
            , s.[ReservationStart]
            , s.[RVGamount]
            , s.[RVGsupport]
            , s.[SalesDate]
            , s.[ScaniaOrderNu]
            , s.[SEATS]
            , s.[SpecifDefiniteDate]
            , s.[UsedBus]
            , s.[VehicleLocation]
            , s.[VIN]
            , s.[DataSourceId]
            , @ThreadLogId
            , -1
            , -1
            , N'U' -- update
    FROM Stage.CERTdboBusOrders AS s
    INNER JOIN Vault.CERTdboBusOrders AS v
        ON  s.[IDD_Bus] = v.[IDD_Bus] AND v.ThreadLogUpdateId = @ThreadLogId
    
    INSERT INTO [Vault].[CERTdboBusOrders] (
            [IDD_Bus]
            , [ACC]
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
            , [ThreadLogInsertId]
            , [ThreadLogUpdateId]
            , [ThreadLogDeleteId]
            , [ChangeOperation]
            
    ) 
    OUTPUT Inserted.ThreadLogDeleteId INTO @DeleteRowCounts
    SELECT
            v.[IDD_Bus]
            , v.[ACC]
            , v.[ActualDealerDate]
            , v.[AEB]
            , v.[BuyBackDate]
            , v.[CDD]
            , v.[CDDC]
            , v.[Cost]
            , v.[CustomerPrice]
            , v.[CustomerTemporary]
            , v.[DateOUT]
            , v.[DeliveryCustomerDate]
            , v.[DistributorID]
            , v.[DistributorOrderID]
            , v.[EngineNumber]
            , v.[EXWsupport]
            , v.[HighServiceLevel]
            , v.[ChassisNumber]
            , v.[ChassisONLYcontracted]
            , v.[ChassisType]
            , v.[ChassisWeight]
            , v.[ID_BusModel]
            , v.[ID_CurrentBusLocation]
            , v.[ID_Customer]
            , v.[ID_Destinace]
            , v.[ID_Emise]
            , v.[ID_InvoiceCountry]
            , v.[ID_ReservUser]
            , v.[ID_Status]
            , v.[ID_User]
            , v.[LastAddressChange]
            , v.[LDW]
            , v.[Margin]
            , v.[NET]
            , v.[ProdPeriod]
            , v.[Prodplant]
            , v.[PromisedDeliveryDate]
            , v.[PurchaseBody]
            , v.[PurchaseDateBody]
            , v.[PurchaseDateChassis]
            , v.[PurchaseChassis]
            , v.[ReInvoiceDate]
            , v.[Remark]
            , v.[ReservationEnd]
            , v.[ReservationStart]
            , v.[RVGamount]
            , v.[RVGsupport]
            , v.[SalesDate]
            , v.[ScaniaOrderNu]
            , v.[SEATS]
            , v.[SpecifDefiniteDate]
            , v.[UsedBus]
            , v.[VehicleLocation]
            , v.[VIN]
            , v.[DataSourceId]
            , @ThreadLogId
            , -1
            , -1
            , N'D' -- update
    FROM Vault.CERTdboBusOrders AS v
    WHERE v.ThreadLogDeleteId = @ThreadLogId
    ;

        DECLARE @insertCount int,
                @updateCount int,
                @deleteCount int;

        SELECT @insertCount = COUNT(*) FROM @rowCounts WHERE [MergeAction] = N'INSERT';
        SELECT @updateCount = COUNT(*) FROM @UpdateRowCounts;
        SELECT @deleteCount = COUNT(*) FROM @DeleteRowCounts;


        --Log ThreadLog Success
        UPDATE Etl.ThreadLog
            SET
                UpdateRowCount = @updateCount
                , InsertRowCount = @insertCount
                , DeleteRowCount = @deleteCount
                , TableFinalRowCount = (SELECT COUNT(*) FROM [Vault].[CERTdboBusOrders] WITH (NOLOCK))
                , EndTime = GETDATE()
                , StatusId = 3      -- Finished
            WHERE ThreadLogId = @ThreadLogId;

        COMMIT TRANSACTION;
    END TRY

    BEGIN CATCH
            EXEC [dbo].[uspErrorHandler] @ThreadLogId = @ThreadLogId;
    END CATCH
```

\[Back to stored procedure list\]\[listofprocedures\]
