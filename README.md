# Documentation BI Solution of project Scania

This document is documentation of Business Inteligence Solution of project Scania created by BI Experts. 
Documentation was generated on 2019-07-12.


## Data Warehouse ScaniaDw

Database description: Datawarehouse - part of Business Intelligence solution of customer Scania


## Database schemas

Table of database schemas. Includes descriptions and schema owner name. 

|Schema name|Schema owner|Description|
|-|-|--|
|db_accessadmin|db_accessadmin|No description available or system schema|
|db_backupoperator|db_backupoperator|No description available or system schema|
|db_datareader|db_datareader|No description available or system schema|
|db_datawriter|db_datawriter|No description available or system schema|
|db_ddladmin|db_ddladmin|No description available or system schema|
|db_denydatareader|db_denydatareader|No description available or system schema|
|db_denydatawriter|db_denydatawriter|No description available or system schema|
|db_owner|db_owner|No description available or system schema|
|db_securityadmin|db_securityadmin|No description available or system schema|
|dbo|dbo|No description available or system schema|
|Admin|dbo|Database schema containing objects related to configuration and maintenance of Datawarehouse (e.g. values defined in Datawarehouse).|
|Dw|dbo|Database schema containing actual views on source data.|
|Etl|dbo|Database schema containing objects for configuration, control and administrating ETL processes (data sources, threads, thread logs, ...).|
|Persist|dbo|Database schema containing objects with persisted data.|
|Stage|dbo|Schema containing objects with data from data sources. Represents largely incremental copy of source.|
|Vault|dbo|Database schema containing tables, that historize data from source.|
|guest|guest|Storage for Stage objects|
|INFORMATION_SCHEMA|INFORMATION_SCHEMA|Data file for loading Stage objects.|
|sys|sys|No description available or system schema|

## List of database tables {#listoftables}


* [Admin.DwParameter][tblAdminDwParameter]


* [Etl.Batch][tblEtlBatch]


* [Etl.DataSource][tblEtlDataSource]


* [Etl.DataSourceType][tblEtlDataSourceType]


* [Etl.DwLevel][tblEtlDwLevel]


* [Etl.IncrementMethod][tblEtlIncrementMethod]


* [Etl.Request][tblEtlRequest]


* [Etl.Status][tblEtlStatus]


* [Etl.Thread][tblEtlThread]


* [Etl.ThreadLog][tblEtlThreadLog]


* [Etl.UserThreadLog][tblEtlUserThreadLog]


* [Stage.CERTdboBusOrders][tblStageCERTdboBusOrders]


* [Stage.CERTdboCountry][tblStageCERTdboCountry]


* [Stage.CERTdboDealers][tblStageCERTdboDealers]


* [Stage.CERTdboOrders][tblStageCERTdboOrders]


* [Stage.CERTdboRenting][tblStageCERTdboRenting]


* [Stage.CERTdboUsers][tblStageCERTdboUsers]


* [Stage.CRMdboAccount][tblStageCRMdboAccount]


* [Stage.CRMdboAppointment][tblStageCRMdboAppointment]


* [Stage.CRMdboBusinessunit][tblStageCRMdboBusinessunit]


* [Stage.CRMdboEmail][tblStageCRMdboEmail]


* [Stage.CRMdboGlobalOptionSetMetadata][tblStageCRMdboGlobalOptionSetMetadata]


* [Stage.CRMdboLlp_canton][tblStageCRMdboLlp_canton]


* [Stage.CRMdboLlp_country][tblStageCRMdboLlp_country]


* [Stage.CRMdboOpportunity][tblStageCRMdboOpportunity]


* [Stage.CRMdboOptionSetMetadata][tblStageCRMdboOptionSetMetadata]


* [Stage.CRMdboPhonecall][tblStageCRMdboPhonecall]


* [Stage.CRMdboStateMetadata][tblStageCRMdboStateMetadata]


* [Stage.CRMdboStatusMetadata][tblStageCRMdboStatusMetadata]


* [Stage.CRMdboSystemuser][tblStageCRMdboSystemuser]


* [Vault.CERTdboBusOrders][tblVaultCERTdboBusOrders]


* [Vault.CERTdboCountry][tblVaultCERTdboCountry]


* [Vault.CERTdboDealers][tblVaultCERTdboDealers]


* [Vault.CERTdboOrders][tblVaultCERTdboOrders]


* [Vault.CERTdboRenting][tblVaultCERTdboRenting]


* [Vault.CERTdboUsers][tblVaultCERTdboUsers]


* [Vault.CRMdboAccount][tblVaultCRMdboAccount]


* [Vault.CRMdboAppointment][tblVaultCRMdboAppointment]


* [Vault.CRMdboBusinessunit][tblVaultCRMdboBusinessunit]


* [Vault.CRMdboEmail][tblVaultCRMdboEmail]


* [Vault.CRMdboGlobalOptionSetMetadata][tblVaultCRMdboGlobalOptionSetMetadata]


* [Vault.CRMdboLlp_canton][tblVaultCRMdboLlp_canton]


* [Vault.CRMdboLlp_country][tblVaultCRMdboLlp_country]


* [Vault.CRMdboOpportunity][tblVaultCRMdboOpportunity]


* [Vault.CRMdboOptionSetMetadata][tblVaultCRMdboOptionSetMetadata]


* [Vault.CRMdboPhonecall][tblVaultCRMdboPhonecall]


* [Vault.CRMdboStateMetadata][tblVaultCRMdboStateMetadata]


* [Vault.CRMdboStatusMetadata][tblVaultCRMdboStatusMetadata]


* [Vault.CRMdboSystemuser][tblVaultCRMdboSystemuser]


## List of database views {#listofviews}

* [dbo.Account][viewdboAccount]


* [dbo.Account Service][viewdboAccountService]


* [dbo.Activity][viewdboActivity]


* [dbo.Activity Service][viewdboActivityService]


* [dbo.Bus Order][viewdboBusOrder]


* [dbo.Business Unit][viewdboBusinessUnit]


* [dbo.Fresh Opportunity][viewdboFreshOpportunity]


* [dbo.Fresh Opportunity Service][viewdboFreshOpportunityService]


* [dbo.New Truck Order][viewdboNewTruckOrder]


* [dbo.Rent Vehicle][viewdboRentVehicle]


* [dbo.Salesman][viewdboSalesman]


* [dbo.Salesman CERT][viewdboSalesmanCERT]


* [dbo.Salesman CRM][viewdboSalesmanCRM]


* [dbo.Weekly Appointment][viewdboWeeklyAppointment]


* [dbo.Weekly Average Accounts Visited NV][viewdboWeeklyAverageAccountsVisitedNV]


* [dbo.Weekly Average Accounts Visited Service][viewdboWeeklyAverageAccountsVisitedService]


* [dbo.Weekly Average Visits NV][viewdboWeeklyAverageVisitsNV]


* [dbo.Weekly Average Visits Service][viewdboWeeklyAverageVisitsService]


* [Dw.vCERTdboBusOrdersActual][viewDwvCERTdboBusOrdersActual]


* [Dw.vCERTdboCountryActual][viewDwvCERTdboCountryActual]


* [Dw.vCERTdboDealersActual][viewDwvCERTdboDealersActual]


* [Dw.vCERTdboOrdersActual][viewDwvCERTdboOrdersActual]


* [Dw.vCERTdboRentingActual][viewDwvCERTdboRentingActual]


* [Dw.vCERTdboUsersActual][viewDwvCERTdboUsersActual]


* [Dw.vCRMdboAccountActual][viewDwvCRMdboAccountActual]


* [Dw.vCRMdboAppointmentActual][viewDwvCRMdboAppointmentActual]


* [Dw.vCRMdboBusinessunitActual][viewDwvCRMdboBusinessunitActual]


* [Dw.vCRMdboEmailActual][viewDwvCRMdboEmailActual]


* [Dw.vCRMdboGlobalOptionSetMetadataActual][viewDwvCRMdboGlobalOptionSetMetadataActual]


* [Dw.vCRMdboLlp_cantonActual][viewDwvCRMdboLlp_cantonActual]


* [Dw.vCRMdboLlp_countryActual][viewDwvCRMdboLlp_countryActual]


* [Dw.vCRMdboOpportunityActual][viewDwvCRMdboOpportunityActual]


* [Dw.vCRMdboOptionSetMetadataActual][viewDwvCRMdboOptionSetMetadataActual]


* [Dw.vCRMdboPhonecallActual][viewDwvCRMdboPhonecallActual]


* [Dw.vCRMdboStateMetadataActual][viewDwvCRMdboStateMetadataActual]


* [Dw.vCRMdboStatusMetadataActual][viewDwvCRMdboStatusMetadataActual]


* [Dw.vCRMdboSystemuserActual][viewDwvCRMdboSystemuserActual]


* [Etl.StageLastRun][viewEtlStageLastRun]


* [Etl.VaultLastRun][viewEtlVaultLastRun]



## List of database functions {#listoffunctions}


* [dbo.fnGetDateDiffForMondayAsFirstDayOfWeek][fndbofnGetDateDiffForMondayAsFirstDayOfWeek]
* [dbo.fnGetLoadDateFrom][fndbofnGetLoadDateFrom]
* [dbo.fnGetLoadLsnFrom][fndbofnGetLoadLsnFrom]

## List of stored procedures {#listofprocedures}

* [dbo.uspErrorHandler][spdbouspErrorHandler]
* [Etl.uspCreateFirstLoadQueue][spEtluspCreateFirstLoadQueue]
* [Etl.uspStartBatch][spEtluspStartBatch]
* [Etl.uspCreateQueue][spEtluspCreateQueue]
* [Etl.uspUserLoad][spEtluspUserLoad]
* [Etl.uspCreateFirstVaultLoad][spEtluspCreateFirstVaultLoad]
* [Stage.uspLoadCRMdboStatusMetadata][spStageuspLoadCRMdboStatusMetadata]
* [Stage.uspLoadCRMdboStateMetadata][spStageuspLoadCRMdboStateMetadata]
* [Stage.uspLoadCRMdboOptionSetMetadata][spStageuspLoadCRMdboOptionSetMetadata]
* [Stage.uspLoadCRMdboSystemuser][spStageuspLoadCRMdboSystemuser]
* [Stage.uspLoadCRMdboPhonecall][spStageuspLoadCRMdboPhonecall]
* [Stage.uspLoadCRMdboOpportunity][spStageuspLoadCRMdboOpportunity]
* [Stage.uspLoadCRMdboLlp_country][spStageuspLoadCRMdboLlpcountry]
* [Stage.uspLoadCRMdboLlp_canton][spStageuspLoadCRMdboLlpcanton]
* [Stage.uspLoadCRMdboGlobalOptionSetMetadata][spStageuspLoadCRMdboGlobalOptionSetMetadata]
* [Stage.uspLoadCRMdboAccount][spStageuspLoadCRMdboAccount]
* [Stage.uspLoadCERTdboUsers][spStageuspLoadCERTdboUsers]
* [Stage.uspLoadCERTdboDealers][spStageuspLoadCERTdboDealers]
* [Stage.uspLoadCRMdboEmail][spStageuspLoadCRMdboEmail]
* [Stage.uspLoadCERTdboRenting][spStageuspLoadCERTdboRenting]
* [Stage.uspLoadCRMdboBusinessunit][spStageuspLoadCRMdboBusinessunit]
* [Stage.uspLoadCRMdboAppointment][spStageuspLoadCRMdboAppointment]
* [Stage.uspLoadCERTdboBusOrders][spStageuspLoadCERTdboBusOrders]
* [Stage.uspLoadCERTdboOrders][spStageuspLoadCERTdboOrders]
* [Stage.uspLoadCERTdboCountry][spStageuspLoadCERTdboCountry]
* [Vault.uspLoadCERTdboCountry][spVaultuspLoadCERTdboCountry]
* [Vault.uspLoadCERTdboOrders][spVaultuspLoadCERTdboOrders]
* [Vault.uspLoadCERTdboBusOrders][spVaultuspLoadCERTdboBusOrders]
* [Vault.uspLoadCRMdboLlp_country][spVaultuspLoadCRMdboLlpcountry]
* [Vault.uspLoadCRMdboLlp_canton][spVaultuspLoadCRMdboLlpcanton]
* [Vault.uspLoadCRMdboGlobalOptionSetMetadata][spVaultuspLoadCRMdboGlobalOptionSetMetadata]
* [Vault.uspLoadCRMdboEmail][spVaultuspLoadCRMdboEmail]
* [Vault.uspLoadCRMdboBusinessunit][spVaultuspLoadCRMdboBusinessunit]
* [Vault.uspLoadCRMdboAppointment][spVaultuspLoadCRMdboAppointment]
* [Vault.uspLoadCRMdboAccount][spVaultuspLoadCRMdboAccount]
* [Vault.uspLoadCERTdboUsers][spVaultuspLoadCERTdboUsers]
* [Vault.uspLoadCERTdboDealers][spVaultuspLoadCERTdboDealers]
* [Vault.uspLoadCERTdboRenting][spVaultuspLoadCERTdboRenting]
* [Vault.uspLoadCRMdboSystemuser][spVaultuspLoadCRMdboSystemuser]
* [Vault.uspLoadCRMdboStatusMetadata][spVaultuspLoadCRMdboStatusMetadata]
* [Vault.uspLoadCRMdboStateMetadata][spVaultuspLoadCRMdboStateMetadata]
* [Vault.uspLoadCRMdboPhonecall][spVaultuspLoadCRMdboPhonecall]
* [Vault.uspLoadCRMdboOptionSetMetadata][spVaultuspLoadCRMdboOptionSetMetadata]
* [Vault.uspLoadCRMdboOpportunity][spVaultuspLoadCRMdboOpportunity]


# Tabular model ScaniaTab

* [Measure list][ScaniaTabMeasures]


##  Tables of tabular model ScaniaTab 
* [Table Account][ScaniaTabAccount]


* [Table Bus Order][ScaniaTabBusOrder]


* [Table Business Unit][ScaniaTabBusinessUnit]


* [Table Fresh Opportunity][ScaniaTabFreshOpportunity]


* [Table New Truck Order][ScaniaTabNewTruckOrder]


* [Table Rent Vehicle][ScaniaTabRentVehicle]


* [Table Salesman][ScaniaTabSalesman]


* [Table Activity][ScaniaTabActivity]


* [Table Account Service][ScaniaTabAccountService]


* [Table Activity Service][ScaniaTabActivityService]


* [Table Fresh Opportunity Service][ScaniaTabFreshOpportunityService]


* [Table Weekly Appointment][ScaniaTabWeeklyAppointment]


* [Table Weekly Average Accounts Visited NV][ScaniaTabWeeklyAverageAccountsVisitedNV]


* [Table Weekly Average Accounts Visited Service][ScaniaTabWeeklyAverageAccountsVisitedService]


* [Table Weekly Average Visits NV][ScaniaTabWeeklyAverageVisitsNV]


* [Table Weekly Average Visits Service][ScaniaTabWeeklyAverageVisitsService]




### Report list 
#### Accounts without Activities New Truck
> Report Description: Provides detailed listing of accounts that have no activities planned in the future - for sales type New Truck

#### Accounts without Activities Services
> Report Description: Provides detailed listing of accounts that have no activities planned in the future - for sales type Services

#### Unattended Accounts New Truck
> Report Description: Provides detailed listing of accounts that have not been visited in last five months - for sales type New Truck

#### Unattended Accounts Services
> Report Description: Provides detailed listing of accounts that have not been visited in last five months - for sales type Services

#### Weekly appointments New Truck
> Report Description: Provides detailed listing of appointments made by sales person during evaluated week - for sales type New Truck

#### Weekly appointments Services
> Report Description: Provides detailed listing of appointments made by sales person during evaluated week  - for sales type Services

#### Weekly report New Truck
> Report Description: Provides summary of sales persons‘ weekly activities - for sales type New Truck

#### Weekly report Services
> Report Description: Provides summary of sales persons‘ weekly activities - for sales type Services


[tblAdminDwParameter]: Pages\tblAdminDwParameter.md

[tblEtlDataSourceType]: Pages\tblEtlDataSourceType.md

[tblEtlDataSource]: Pages\tblEtlDataSource.md

[tblEtlThread]: Pages\tblEtlThread.md

[tblEtlThreadLog]: Pages\tblEtlThreadLog.md

[tblEtlRequest]: Pages\tblEtlRequest.md

[tblEtlIncrementMethod]: Pages\tblEtlIncrementMethod.md

[tblStageCERTdboBusOrders]: Pages\tblStageCERTdboBusOrders.md

[tblStageCERTdboOrders]: Pages\tblStageCERTdboOrders.md

[tblStageCRMdboSystemuser]: Pages\tblStageCRMdboSystemuser.md

[tblStageCRMdboPhonecall]: Pages\tblStageCRMdboPhonecall.md

[tblStageCRMdboOpportunity]: Pages\tblStageCRMdboOpportunity.md

[tblStageCRMdboLlp_country]: Pages\tblStageCRMdboLlp_country.md

[tblEtlDwLevel]: Pages\tblEtlDwLevel.md

[tblEtlBatch]: Pages\tblEtlBatch.md

[tblEtlStatus]: Pages\tblEtlStatus.md

[tblEtlUserThreadLog]: Pages\tblEtlUserThreadLog.md

[tblStageCRMdboLlp_canton]: Pages\tblStageCRMdboLlp_canton.md

[tblStageCRMdboEmail]: Pages\tblStageCRMdboEmail.md

[tblStageCRMdboBusinessunit]: Pages\tblStageCRMdboBusinessunit.md

[tblStageCRMdboAppointment]: Pages\tblStageCRMdboAppointment.md

[fndbofnGetLoadDateFrom]: Pages\fndbofnGetLoadDateFrom.md

[fndbofnGetLoadLsnFrom]: Pages\fndbofnGetLoadLsnFrom.md

[tblStageCERTdboRenting]: Pages\tblStageCERTdboRenting.md

[ScaniaTabAccount]: Pages\ScaniaTabAccount.md

[ScaniaTabNewTruckOrder]: Pages\ScaniaTabNewTruckOrder.md

[ScaniaTabAccountService]: Pages\ScaniaTabAccountService.md

[tblStageCRMdboAccount]: Pages\tblStageCRMdboAccount.md

[tblStageCERTdboCountry]: Pages\tblStageCERTdboCountry.md

[tblVaultCRMdboLlp_canton]: Pages\tblVaultCRMdboLlp_canton.md

[tblVaultCRMdboEmail]: Pages\tblVaultCRMdboEmail.md

[tblVaultCRMdboBusinessunit]: Pages\tblVaultCRMdboBusinessunit.md

[tblVaultCRMdboAppointment]: Pages\tblVaultCRMdboAppointment.md

[tblVaultCERTdboBusOrders]: Pages\tblVaultCERTdboBusOrders.md

[tblVaultCERTdboOrders]: Pages\tblVaultCERTdboOrders.md

[tblVaultCRMdboSystemuser]: Pages\tblVaultCRMdboSystemuser.md

[tblVaultCRMdboPhonecall]: Pages\tblVaultCRMdboPhonecall.md

[tblVaultCRMdboOpportunity]: Pages\tblVaultCRMdboOpportunity.md

[tblVaultCRMdboLlp_country]: Pages\tblVaultCRMdboLlp_country.md

[tblStageCERTdboUsers]: Pages\tblStageCERTdboUsers.md

[tblStageCERTdboDealers]: Pages\tblStageCERTdboDealers.md

[ScaniaTabWeeklyAverageAccountsVisitedNV]: Pages\ScaniaTabWeeklyAverageAccountsVisitedNV.md

[tblStageCRMdboStatusMetadata]: Pages\tblStageCRMdboStatusMetadata.md

[tblStageCRMdboStateMetadata]: Pages\tblStageCRMdboStateMetadata.md

[ScaniaTabWeeklyAverageVisitsService]: Pages\ScaniaTabWeeklyAverageVisitsService.md

[viewDwvCRMdboStatusMetadataActual]: Pages\viewDwvCRMdboStatusMetadataActual.md

[tblStageCRMdboOptionSetMetadata]: Pages\tblStageCRMdboOptionSetMetadata.md

[tblStageCRMdboGlobalOptionSetMetadata]: Pages\tblStageCRMdboGlobalOptionSetMetadata.md

[tblVaultCRMdboGlobalOptionSetMetadata]: Pages\tblVaultCRMdboGlobalOptionSetMetadata.md

[tblVaultCERTdboDealers]: Pages\tblVaultCERTdboDealers.md

[tblVaultCRMdboAccount]: Pages\tblVaultCRMdboAccount.md

[tblVaultCERTdboUsers]: Pages\tblVaultCERTdboUsers.md

[tblVaultCERTdboRenting]: Pages\tblVaultCERTdboRenting.md

[tblVaultCRMdboStatusMetadata]: Pages\tblVaultCRMdboStatusMetadata.md

[tblVaultCRMdboStateMetadata]: Pages\tblVaultCRMdboStateMetadata.md

[tblVaultCRMdboOptionSetMetadata]: Pages\tblVaultCRMdboOptionSetMetadata.md

[tblVaultCERTdboCountry]: Pages\tblVaultCERTdboCountry.md

[fndbofnGetDateDiffForMondayAsFirstDayOfWeek]: Pages\fndbofnGetDateDiffForMondayAsFirstDayOfWeek.md

[spEtluspCreateFirstLoadQueue]: Pages\spEtluspCreateFirstLoadQueue.md

[spdbouspErrorHandler]: Pages\spdbouspErrorHandler.md

[spEtluspStartBatch]: Pages\spEtluspStartBatch.md

[spEtluspCreateQueue]: Pages\spEtluspCreateQueue.md

[spEtluspUserLoad]: Pages\spEtluspUserLoad.md

[spStageuspLoadCRMdboSystemuser]: Pages\spStageuspLoadCRMdboSystemuser.md

[spStageuspLoadCRMdboPhonecall]: Pages\spStageuspLoadCRMdboPhonecall.md

[spStageuspLoadCRMdboOpportunity]: Pages\spStageuspLoadCRMdboOpportunity.md

[spStageuspLoadCRMdboLlpcountry]: Pages\spStageuspLoadCRMdboLlpcountry.md

[spStageuspLoadCRMdboLlpcanton]: Pages\spStageuspLoadCRMdboLlpcanton.md

[spStageuspLoadCRMdboEmail]: Pages\spStageuspLoadCRMdboEmail.md

[spStageuspLoadCRMdboBusinessunit]: Pages\spStageuspLoadCRMdboBusinessunit.md

[spStageuspLoadCRMdboAppointment]: Pages\spStageuspLoadCRMdboAppointment.md

[spStageuspLoadCERTdboBusOrders]: Pages\spStageuspLoadCERTdboBusOrders.md

[spStageuspLoadCERTdboOrders]: Pages\spStageuspLoadCERTdboOrders.md

[spVaultuspLoadCERTdboCountry]: Pages\spVaultuspLoadCERTdboCountry.md

[spVaultuspLoadCERTdboOrders]: Pages\spVaultuspLoadCERTdboOrders.md

[spVaultuspLoadCERTdboBusOrders]: Pages\spVaultuspLoadCERTdboBusOrders.md

[spVaultuspLoadCRMdboLlpcountry]: Pages\spVaultuspLoadCRMdboLlpcountry.md

[spVaultuspLoadCRMdboLlpcanton]: Pages\spVaultuspLoadCRMdboLlpcanton.md

[spVaultuspLoadCRMdboGlobalOptionSetMetadata]: Pages\spVaultuspLoadCRMdboGlobalOptionSetMetadata.md

[spVaultuspLoadCRMdboEmail]: Pages\spVaultuspLoadCRMdboEmail.md

[spVaultuspLoadCRMdboBusinessunit]: Pages\spVaultuspLoadCRMdboBusinessunit.md

[spVaultuspLoadCRMdboAppointment]: Pages\spVaultuspLoadCRMdboAppointment.md

[spVaultuspLoadCRMdboAccount]: Pages\spVaultuspLoadCRMdboAccount.md

[spVaultuspLoadCERTdboUsers]: Pages\spVaultuspLoadCERTdboUsers.md

[spVaultuspLoadCERTdboDealers]: Pages\spVaultuspLoadCERTdboDealers.md

[spVaultuspLoadCERTdboRenting]: Pages\spVaultuspLoadCERTdboRenting.md

[spVaultuspLoadCRMdboSystemuser]: Pages\spVaultuspLoadCRMdboSystemuser.md

[spVaultuspLoadCRMdboStatusMetadata]: Pages\spVaultuspLoadCRMdboStatusMetadata.md

[spVaultuspLoadCRMdboStateMetadata]: Pages\spVaultuspLoadCRMdboStateMetadata.md

[spVaultuspLoadCRMdboPhonecall]: Pages\spVaultuspLoadCRMdboPhonecall.md

[spVaultuspLoadCRMdboOptionSetMetadata]: Pages\spVaultuspLoadCRMdboOptionSetMetadata.md

[spVaultuspLoadCRMdboOpportunity]: Pages\spVaultuspLoadCRMdboOpportunity.md

[ScaniaTabMeasures]: Pages\ScaniaTabMeasures.md

[spEtluspCreateFirstVaultLoad]: Pages\spEtluspCreateFirstVaultLoad.md

[spStageuspLoadCRMdboStatusMetadata]: Pages\spStageuspLoadCRMdboStatusMetadata.md

[viewDwvCRMdboStateMetadataActual]: Pages\viewDwvCRMdboStateMetadataActual.md

[viewDwvCRMdboOptionSetMetadataActual]: Pages\viewDwvCRMdboOptionSetMetadataActual.md

[spStageuspLoadCRMdboStateMetadata]: Pages\spStageuspLoadCRMdboStateMetadata.md

[ScaniaTabBusOrder]: Pages\ScaniaTabBusOrder.md

[ScaniaTabBusinessUnit]: Pages\ScaniaTabBusinessUnit.md

[ScaniaTabFreshOpportunity]: Pages\ScaniaTabFreshOpportunity.md

[spStageuspLoadCRMdboOptionSetMetadata]: Pages\spStageuspLoadCRMdboOptionSetMetadata.md

[ScaniaTabRentVehicle]: Pages\ScaniaTabRentVehicle.md

[ScaniaTabSalesman]: Pages\ScaniaTabSalesman.md

[ScaniaTabActivity]: Pages\ScaniaTabActivity.md

[spStageuspLoadCRMdboGlobalOptionSetMetadata]: Pages\spStageuspLoadCRMdboGlobalOptionSetMetadata.md

[ScaniaTabActivityService]: Pages\ScaniaTabActivityService.md

[ScaniaTabFreshOpportunityService]: Pages\ScaniaTabFreshOpportunityService.md

[ScaniaTabWeeklyAppointment]: Pages\ScaniaTabWeeklyAppointment.md

[spStageuspLoadCRMdboAccount]: Pages\spStageuspLoadCRMdboAccount.md

[spStageuspLoadCERTdboUsers]: Pages\spStageuspLoadCERTdboUsers.md

[ScaniaTabWeeklyAverageAccountsVisitedService]: Pages\ScaniaTabWeeklyAverageAccountsVisitedService.md

[ScaniaTabWeeklyAverageVisitsNV]: Pages\ScaniaTabWeeklyAverageVisitsNV.md

[spStageuspLoadCERTdboDealers]: Pages\spStageuspLoadCERTdboDealers.md

[spStageuspLoadCERTdboRenting]: Pages\spStageuspLoadCERTdboRenting.md

[viewdboActivity]: Pages\viewdboActivity.md

[viewdboActivityService]: Pages\viewdboActivityService.md

[viewdboBusOrder]: Pages\viewdboBusOrder.md

[spStageuspLoadCERTdboCountry]: Pages\spStageuspLoadCERTdboCountry.md

[viewdboBusinessUnit]: Pages\viewdboBusinessUnit.md

[viewdboFreshOpportunity]: Pages\viewdboFreshOpportunity.md

[viewDwvCERTdboDealersActual]: Pages\viewDwvCERTdboDealersActual.md

[viewDwvCRMdboSystemuserActual]: Pages\viewDwvCRMdboSystemuserActual.md

[viewDwvCRMdboOpportunityActual]: Pages\viewDwvCRMdboOpportunityActual.md

[viewDwvCRMdboEmailActual]: Pages\viewDwvCRMdboEmailActual.md

[viewdboFreshOpportunityService]: Pages\viewdboFreshOpportunityService.md

[viewdboNewTruckOrder]: Pages\viewdboNewTruckOrder.md

[viewdboRentVehicle]: Pages\viewdboRentVehicle.md

[viewdboSalesmanCERT]: Pages\viewdboSalesmanCERT.md

[viewdboSalesmanCRM]: Pages\viewdboSalesmanCRM.md

[viewdboWeeklyAppointment]: Pages\viewdboWeeklyAppointment.md

[viewdboSalesman]: Pages\viewdboSalesman.md

[viewdboWeeklyAverageAccountsVisitedNV]: Pages\viewdboWeeklyAverageAccountsVisitedNV.md

[viewdboWeeklyAverageAccountsVisitedService]: Pages\viewdboWeeklyAverageAccountsVisitedService.md

[viewdboWeeklyAverageVisitsNV]: Pages\viewdboWeeklyAverageVisitsNV.md

[viewdboWeeklyAverageVisitsService]: Pages\viewdboWeeklyAverageVisitsService.md

[viewdboAccount]: Pages\viewdboAccount.md

[viewdboAccountService]: Pages\viewdboAccountService.md

[viewDwvCRMdboAccountActual]: Pages\viewDwvCRMdboAccountActual.md

[viewDwvCERTdboUsersActual]: Pages\viewDwvCERTdboUsersActual.md

[viewDwvCERTdboRentingActual]: Pages\viewDwvCERTdboRentingActual.md

[viewDwvCERTdboBusOrdersActual]: Pages\viewDwvCERTdboBusOrdersActual.md

[viewDwvCERTdboCountryActual]: Pages\viewDwvCERTdboCountryActual.md

[viewDwvCERTdboOrdersActual]: Pages\viewDwvCERTdboOrdersActual.md

[viewDwvCRMdboPhonecallActual]: Pages\viewDwvCRMdboPhonecallActual.md

[viewDwvCRMdboLlp_countryActual]: Pages\viewDwvCRMdboLlp_countryActual.md

[viewDwvCRMdboLlp_cantonActual]: Pages\viewDwvCRMdboLlp_cantonActual.md

[viewDwvCRMdboGlobalOptionSetMetadataActual]: Pages\viewDwvCRMdboGlobalOptionSetMetadataActual.md

[viewEtlVaultLastRun]: Pages\viewEtlVaultLastRun.md

[viewDwvCRMdboBusinessunitActual]: Pages\viewDwvCRMdboBusinessunitActual.md

[viewDwvCRMdboAppointmentActual]: Pages\viewDwvCRMdboAppointmentActual.md

[viewEtlStageLastRun]: Pages\viewEtlStageLastRun.md

