# Contoso DWH

> Copy/Paste from the Microsoft Excel Workbook attached with original database.
- [Contoso DWH](#contoso-dwh)
  - [Dimension Tables](#dimension-tables)
    - [DimAccount](#dimaccount)
    - [DimChannel](#dimchannel)
    - [DimCurrency](#dimcurrency)
    - [DimCustomer](#dimcustomer)
    - [DimDate](#dimdate)
    - [DimEmployee](#dimemployee)
    - [DimEntity](#dimentity)
    - [DimMachine](#dimmachine)
    - [DimOutage](#dimoutage)
    - [DimProduct](#dimproduct)
    - [DimProductCategory](#dimproductcategory)
    - [DimProductSubcategory](#dimproductsubcategory)
    - [DimPromotion](#dimpromotion)
    - [DimSalesTerritory](#dimsalesterritory)
    - [DimScenario](#dimscenario)
    - [DimStore](#dimstore)
    - [DimGeography](#dimgeography)
  - [Fact Tables](#fact-tables)
    - [FactExchangeRate](#factexchangerate)
    - [FactInventory](#factinventory)
    - [FactITMachine](#factitmachine)
    - [FactITSLA](#factitsla)
    - [FactSales](#factsales)
    - [FactSalesQuota](#factsalesquota)
    - [FactStrategyPlan](#factstrategyplan)
    - [FactOnlineSales](#factonlinesales)


## Dimension Tables

### DimAccount
| COLUMNS             | TYPE     | description                                       | info |
| ------------------- | -------- | ------------------------------------------------- | ---- |
| AccountKey          | int      | The primary key of account table                  | PK   |
| ParentAccountKey    | int      | The parent key of account table                   |      |
| AccountLabel        | nvarchar | The account label                                 |      |
| AccountName         | nvarchar | The name of account.                              |      |
| AccountDescription  | nvarchar | The account description                           |      |
| AccountType         | nvarchar | The type of the account such as Asset or income   |      |
| Operator            | nvarchar | The operator of the account record                |      |
| CustomMembers       | nvarchar | The account custom  member for MDX calculation    |      |
| ValueType           | nvarchar | The value type of the account record              |      |
| CustomMemberOptions | nvarchar | The options of custom members for MDX calculation |      |
| ETLLoadID           | int      | ETL load process ID                               |      |
| LoadDate            | datetime | Loaded date, used for ETL                         |      |
| UpdateDate          | datetime | Updated date, used for ETL                        |      |


### DimChannel
| COLUMNS            | TYPE     | description                                             | NOTES |
| ------------------ | -------- | ------------------------------------------------------- | ----- |
| ChannelKey         | int      | The primary key of channel table                        | PK    |
| ChannelLabel       | nvarchar | The channel label                                       |       |
| ChannelName        | nvarchar | The name of the channel.(Store/Online/Catalog/Reseller) |       |
| ChannelDescription | nvarchar | The description of the channel                          |       |
| ETLLoadID          | int      | ETL load process ID                                     |       |
| LoadDate           | datetime | Loaded date, used for ETL                               |       |
| UpdateDate         | datetime | Updated date, used for ETL                              |       |

### DimCurrency
| COLUMNS             | TYPE     | description                            | info |
| ------------------- | -------- | -------------------------------------- | ---- |
| CurrencyKey         | int      | The primary key of currency table      | PK   |
| CurrencyLabel       | nvarchar | The abbreviation of the currency       |      |
| CurrencyName        | nvarchar | The name of the currency (USD/GBP/CNY) |      |
| CurrencyDescription | nvarchar | The description of the currency        |      |
| ETLLoadID           | int      | ETL load process ID                    |      |
| LoadDate            | datetime | Loaded date, used for ETL              |      |
| UpdateDate          | datetime | Updated date, used for ETL             |      |

### DimCustomer
| COLUMNS              | TYPE       | description                                     | info |
| -------------------- | ---------- | ----------------------------------------------- | ---- |
| CustomerKey          | int        | The primary key of customer table               | PK   |
| GeographyKey         | int        | Foreign key pointed to PK in DimGeography table | FK   |
| CustomerLabel        | nvarchar 0 | The abbreviated  description of the customer    |      |
| Title                | nvarchar   | The title of the customer                       |      |
| FirstName            | nvarchar   | The first name of the customer                  |      |
| MiddleName           | nvarchar   | The middle name of the customer                 |      |
| LastName             | nvarchar   | The last name of the customer                   |      |
| NameStyle            | bit        | The style of the customer name                  |      |
| BirthDate            | date       | The birthday of the customer                    |      |
| MaritalStatus        | nvarchar   | The marital  status of the customer             |      |
| Suffix               | nvarchar   | The suffix of the customer                      |      |
| Gender               | nvarchar   | The gender of the customer                      |      |
| EmailAddress         | nvarchar   | The email address of the customer               |      |
| YearlyIncome         | money      | The yearly income of the customer               |      |
| TotalChildren        | tinyint    | The number of children                          |      |
| NumberChildrenAtHome | tinyint    | The at-home children number                     |      |
| Education            | nvarchar   | The education of the customer                   |      |
| Occupation           | nvarchar 0 | The occupation of the customer                  |      |
| HouseOwnerFlag       | nchar      | The flag of whether the customer owns a house   |      |
| NumberCarsOwned      | tinyint    | The number of cars owned by customer            |      |
| AddressLine1         | nvarchar 0 | The address 1 of the customer                   |      |
| AddressLine2         | nvarchar 0 | The address 2 of the customer                   |      |
| Phone                | nvarchar   | The phone number of the customer                |      |
| DateFirstPurchase    | date       | The first purchase date of the customer         |      |
| CustomerType         | nvarchar   | The type of customer(Person/Company)            |      |
| ETLLoadID            | int        | ETL load process ID                             |      |
| LoadDate             | datetime   | Loaded date, used for ETL                       |      |
| UpdateDate           | datetime   | Updated date, used for ETL                      |      |

### DimDate
| COLUMNS                | TYPE     | description                                | info |
| ---------------------- | -------- | ------------------------------------------ | ---- |
| Datekey                | Datetime | The primary key of Date table              | PK   |
| FullDateLabel          | nvarchar | Date label                                 |      |
| DateDescription        | nvarchar | Date description                           |      |
| CalendarYear           | int      | Calendar year                              |      |
| CalendarYearLabel      | nvarchar | Label of calendar year                     |      |
| CalendarHalfYear       | int      | Half year                                  |      |
| CalendarHalfYearLabel  | nvarchar | Label of the half year                     |      |
| CalendarQuarter        | int      | Quarter of a calendar year                 |      |
| CalendarQuarterLabel   | nvarchar | Label of the quarter                       |      |
| CalendarMonth          | int      | Month of a calendar year                   |      |
| CalendarMonthLabel     | nvarchar | Label of the month                         |      |
| CalendarWeek           | int      | Week of a calendar year                    |      |
| CalendarWeekLabel      | nvarchar | Label of the week                          |      |
| CalendarDayOfWeek      | int      | Date of a calendar year                    |      |
| CalendarDayOfWeekLabel | nvarchar | Label of the date                          |      |
| FiscalYear             | int      | Fiscal year                                |      |
| FiscalYearLabel        | nvarchar | Label of the fiscal year                   |      |
| FiscalHalfYear         | int      | Half year of a fiscal year                 |      |
| FiscalHalfYearLabel    | nvarchar | Label of the half fiscal year              |      |
| FiscalQuarter          | int      | Quarter of a fiscal year                   |      |
| FiscalQuarterLabel     | nvarchar | Label of the fiscal quarter                |      |
| FiscalMonth            | int      | Month of a fiscal year                     |      |
| FiscalMonthLabel       | nvarchar | Label of the fiscal month                  |      |
| IsWorkDay              | nvarchar | Whether it is a work day                   |      |
| IsHoliday              | int      | Whether it is a holiday                    |      |
| HolidayName            | nvarchar | The name of the holiday if it is a holiday |      |
| EuropeSeason           | nvarchar | The marketing  season in Europe.           |      |
| NorthAmericaSeason     | nvarchar | The marketing  season in North America.    |      |
| AsiaSeason             | nvarchar | The marketing  season in Asia.             |      |

### DimEmployee
| COLUMNS               | TYPE     | description                               | info |
| --------------------- | -------- | ----------------------------------------- | ---- |
| EmployeeKey           | int      | The primary key of employee table         | PK   |
| ParentEmployeeKey     | int      | The key of direct report manager          | FK   |
| FirstName             | nvarchar | First name                                |      |
| LastName              | nvarchar | Last name                                 |      |
| MiddleName            | nvarchar | Middle name                               |      |
| Title                 | nvarchar | The title of the employee                 |      |
| HireDate              | date     | The hire date                             |      |
| BirthDate             | date     | The birth date of the employee            |      |
| EmailAddress          | nvarchar | The email address of the employee         |      |
| Phone                 | nvarchar | The phone number of the employee          |      |
| MaritalStatus         | nchar    | The marital status of the employee        |      |
| EmergencyContactName  | nvarchar | Emergency contact name                    |      |
| EmergencyContactPhone | nvarchar | Emergency contact phone                   |      |
| SalariedFlag          | bit      | The flag of salary                        |      |
| Gender                | nchar    | The gender of the employee                |      |
| PayFrequency          | tinyint  | The pay frequency of the employee         |      |
| BaseRate              | money    | The base rate of the salary               |      |
| VacationHours         | smallint | The vacation hours of the employee        |      |
| CurrentFlag           | bit      | Whether is a current employee             |      |
| SalesPersonFlag       | bit      | Whether is a sales person                 |      |
| DepartmentName        | nvarchar | The department of the employee belongs to |      |
| StartDate             | date     | Hiring start date                         |      |
| EndDate               | date     | Hiring end date                           |      |
| Status                | nvarchar | The status of the employee                |      |
| ETLLoadID             | int      | ETL load process ID                       |      |
| LoadDate              | datetime | Loaded date, used for ETL                 |      |
| UpdateDate            | datetime | Updated date, used for ETL                |      |

### DimEntity
| COLUMNS           | TYPE     | description                                               | info |
| ----------------- | -------- | --------------------------------------------------------- | ---- |
| EntityKey         | int      | The primary key of Entity table                           | PK   |
| EntityLabel       | nvarchar | The label of the entity                                   |      |
| ParentEntityKey   | int      | The key of parent entity                                  |      |
| ParentEntityLabel | nvarchar | The label of parent entity                                |      |
| EntityName        | nvarchar | The entity name                                           |      |
| EntityDescription | nvarchar | The entity description                                    |      |
| EntityType        | nvarchar | The entity type (Group/Country/Region/Store)              |      |
| StartDate         | datetime | the start date of Entity (used for slow change dimension) |      |
| EndDate           | datetime | the end date of Entity (used for slow change dimension)   |      |
| Status            | nvarchar | the status of the Entity (Current/Retired)                |      |
| ETLLoadID         | int      | ETL load process ID                                       |      |
| LoadDate          | datetime | Loaded date, used for ETL                                 |      |
| UpdateDate        | datetime | Updated date, used for ETL                                |      |

### DimMachine
| COLUMNS            | TYPE     | description                                                                                | info |
| ------------------ | -------- | ------------------------------------------------------------------------------------------ | ---- |
| MachineKey         | int      | The primary key of machine table                                                           | PK   |
| MachineLabel       | nvarchar | The label of machine  (POS0128201/POS0100101/…)                                            |      |
| StoreKey           | int      | The store by which the machine is owned                                                    | FK   |
| MachineType        | nvarchar | The machine type (the generation of POS or Server: POS01/POS02/SER01/SER03/SWH01/HUB01/….) |      |
| MachineName        | nvarchar | The machine name                                                                           |      |
| MachineDescription | nvarchar | The machine description                                                                    |      |
| VendorName         | nvarchar | Procurement vendor                                                                         |      |
| MachineOS          | nvarchar | Operating system                                                                           |      |
| MachineSource      | nvarchar | Machine location (Store/Data Center)                                                       |      |
| MachineHardware    | nvarchar | Hardware configuration                                                                     |      |
| MachineSoftware    | nvarchar | Software configuration                                                                     |      |
| Status             | nvarchar | The status of the machine (Active/Decommission)                                            |      |
| ServiceStartDate   | datetime | Service start date                                                                         |      |
| DecommissionDate   | datetime | Service decommission date                                                                  |      |
| LastModifiedDate   | datetime | The last updated date.                                                                     |      |
| ETLLoadID          | int      | ETL load process ID                                                                        |      |
| LoadDate           | datetime | Loaded date, used for ETL                                                                  |      |
| UpdateDate         | datetime | Updated date, used for ETL                                                                 |      |

### DimOutage
| COLUMNS                  | TYPE     | description                                                                 | info |
| ------------------------ | -------- | --------------------------------------------------------------------------- | ---- |
| OutageKey                | int      | The primary key of outage table                                             | PK   |
| OutageLabel              | nvarchar | The label of outage                                                         |      |
| OutageName               | nvarchar | The outage name                                                             |      |
| OutageDescription        | nvarchar | The outage description                                                      |      |
| OutageType               | nvarchar | The outage type (Hardware/Software/Network/Maintenance..)                   |      |
| OutageTypeDescription    | nvarchar | The outage type description                                                 |      |
| OutageSubType            | nvarchar | The sub type of the outage (Hardware Memory/Array Controller/Fiber Channel) |      |
| OutageSubTypeDescription | nvarchar | The outage sub type description                                             |      |
| ETLLoadID                | int      | ETL load process ID                                                         |      |
| LoadDate                 | datetime | Loaded date, used for ETL                                                   |      |
| UpdateDate               | datetime | Updated date, used for ETL                                                  |      |

### DimProduct
| COLUMNS               | TYPE     | description                                             | info |
| --------------------- | -------- | ------------------------------------------------------- | ---- |
| ProductKey            | int      | The primary key of Product table                        | PK   |
| ProductLabel          | nvarchar | The label of product                                    |      |
| ProductName           | nvarchar | The name of product                                     |      |
| ProductDescription    | nvarchar | The description of product                              |      |
| ProductSubcategoryKey | int      | The key of product sub category                         | FK   |
| Manufacturer          | nvarchar | The manufacturer of the product                         |      |
| BrandName             | nvarchar | The brand name of the product                           |      |
| ClassID               | nvarchar | The Consumption class ID of the product                 |      |
| ClassName             | nvarchar | The Consumption class name (Economy/Middle/Luxury/Null) |      |
| StyleID               | nvarchar | The style ID of the product                             |      |
| StyleName             | nvarchar | The style name of the product (Professional/Home/...)   |      |
| ColorID               | nvarchar | The color ID of the product                             |      |
| ColorName             | nvarchar | The product color name (Red/Blue/Black/...)             |      |
| Size                  | nvarchar | The size of the product                                 |      |
| SizeRange             | nvarchar | The allowable maximum size of the product               |      |
| SizeUnitMeasureID     | nvarchar | The size unit ID                                        |      |
| Weight                | float    | The weight of the product                               |      |
| WeightUnitMeasureID   | nvarchar | The weight unit ID                                      |      |
| UnitOfMeasureID       | nvarchar | The unit measure ID                                     |      |
| UnitOfMeasureName     | nvarchar | The name of unit measure                                |      |
| StockTypeID           | nvarchar | The ID of stock type                                    |      |
| StockTypeName         | nvarchar | The name of stock type (High/Mid/Low)                   |      |
| UnitCost              | money    | The unit product cost                                   |      |
| UnitPrice             | money    | The suggested unit price                                |      |
| AvailableForSaleDate  | datetime | Start selling date                                      |      |
| StopSaleDate          | datetime | Stop selling date                                       |      |
| Status                | nvarchar | Selling status                                          |      |
| ImageURL              | nvarchar | Image URL address                                       |      |
| ProductURL            | nvarchar | URL address                                             |      |
| ETLLoadID             | int      | ETL load process ID                                     |      |
| LoadDate              | datetime | Loaded date, used for ETL                               |      |
| UpdateDate            | datetime | Updated date, used for ETL                              |      |

### DimProductCategory
| COLUMNS                    | TYPE     | description                                                | info |
| -------------------------- | -------- | ---------------------------------------------------------- | ---- |
| ProductCategoryKey         | int      | The primary key of ProductCategory table                   | PK   |
| ProductCategoryLabel       | nvarchar | The label of the category                                  |      |
| ProductCategoryName        | nvarchar | The category name (AUDIO/TV&VEDIO/COMPUTERS/CELLPHONES...) |      |
| ProductCategoryDescription | nvarchar | The details of the category                                |      |
| ETLLoadID                  | int      | ETL load process ID                                        |      |
| LoadDate                   | datetime | Loaded date, used for ETL                                  |      |
| UpdateDate                 | datetime | Updated date, used for ETL                                 |      |

### DimProductSubcategory
| COLUMNS                      | TYPE     | description                                                                 | info |
| ---------------------------- | -------- | --------------------------------------------------------------------------- | ---- |
| ProductSubcategoryKey        | int      | Primary Key                                                                 | PK   |
| ProductSubcategoryLabel      | nvarchar | The label of the subcategory                                                |      |
| ProductSubcategoryName       | nvarchar | The subcategory's name(Televisions/VCD&DVD/Home Theater System/Accessories) |      |
| ProductSubcategoryDesciption | nvarchar | The details of the subcategory                                              |      |
| ProductCategoryKey           | int      | Which category the subcategory belongs to                                   | FK   |
| ETLLoadID                    | int      | ETL load process ID                                                         |      |
| LoadDate                     | datetime | Loaded date, used for ETL                                                   |      |
| UpdateDate                   | datetime | Updated date, used for ETL                                                  |      |

### DimPromotion
| COLUMNS              | TYPE     | description                                                                     | info |
| -------------------- | -------- | ------------------------------------------------------------------------------- | ---- |
| PromotionKey         | int      | The primary key of Promotion table                                              | PK   |
| PromotionLabel       | nvarchar | The label of the promotion plan                                                 |      |
| PromotionName        | nvarchar | Promotion's name                                                                |      |
| Promotiondescription | nvarchar | The details of the promotion                                                    |      |
| DiscountPercent      | float    | Discount rate                                                                   |      |
| PromotionType        | nvarchar | The type of the promotion plan (No Discount/Excess Inventory/Seasonal Discount) |      |
| PromotionCategory    | nvarchar | The category of the promotion (Store/Customer)                                  |      |
| MinQuantity          | int      | The minimum quantity                                                            |      |
| MaxQuantity          | int      | The maximum quantity                                                            |      |
| StartDate            | datetime | The start date of the promotion plan                                            |      |
| EndDate              | datetime | The end date of the promotion plan                                              |      |
| ETLLoadID            | int      | ETL load process ID                                                             |      |
| LoadDate             | datetime | Loaded date, used for ETL                                                       |      |
| UpdateDate           | datetime | Updated date, used for ETL                                                      |      |

### DimSalesTerritory
| COLUMNS               | TYPE     | description                                                                 | info |
| --------------------- | -------- | --------------------------------------------------------------------------- | ---- |
| SalesTerritoryKey     | int      | The primary key of sales territory table                                    | PK   |
| GeographyKey          | int      | The foreign key linked to DimGeography table                                | FK   |
| SalesTerritoryLabel   | nvarchar | The label of the sales territory                                            |      |
| SalesTerritoryName    | nvarchar | The sales territory name.(Contoso Redmond Store/Contoso New York Store/...) |      |
| SalesTerritoryRegion  | nvarchar | The region of the sales territory (Colorado/Wisconsin/Texas/Florida)        |      |
| SalesTerritoryCountry | nvarchar | The country of the sales territory (United States/UK/Switzerland)           |      |
| SalesTerritoryGroup   | nvarchar | The group of the sales territory (North American/Asian/European )           |      |
| SalesTerritoryLevel   | nvarchar | The sales territory level                                                   |      |
| SalesTerritoryManager | int      | The manager name of the sales territory                                     |      |
| StartDate             | datetime | Start date (used for slow change dimension)                                 |      |
| EndDate               | datetime | Retired date (used for slow change dimension)                               |      |
| Status                | nvarchar | the status of the sales territory (Current/Retired)                         |      |
| ETLLoadID             | int      | ETL load process ID                                                         |      |
| LoadDate              | datetime | Loaded date, used for ETL                                                   |      |
| UpdateDate            | datetime | Updated date, used for ETL                                                  |      |

### DimScenario
| COLUMNS             | TYPE     | description                             | info |
| ------------------- | -------- | --------------------------------------- | ---- |
| ScenarioKey         | int      | The primary key of Scenario table.      | PK   |
| ScenarioLabel       | nvarchar | The label of the scenario               |      |
| ScenarioName        | nvarchar | Scenario's name(Actual/Budget/Forecast) |      |
| ScenarioDescription | nvarchar | The details of the scenario             |      |
| ETLLoadID           | int      | ETL load process ID                     |      |
| LoadDate            | datetime | Loaded date, used for ETL               |      |
| UpdateDate          | datetime | Updated date, used for ETL              |      |

### DimStore
| COLUMNS          | TYPE      | description                                                       | info |
| ---------------- | --------- | ----------------------------------------------------------------- | ---- |
| StoreKey         | int       | The primary key of Store table                                    | PK   |
| GeographyKey     | int       | The foreign key pointed to DimGeography table                     | FK   |
| StoreManager     | int       | The manager of the store                                          |      |
| StoreType        | nvarchar  | The type of the store (Online/Catalog/Store)                      |      |
| StoreName        | nvarchar  | The store's name                                                  |      |
| StoreDescription | nvarchar  | The details of the store                                          |      |
| Status           | nvarchar  | The status of the store  (Open/Close)                             |      |
| OpenDate         | datetime  | The open date of the store                                        |      |
| CloseDate        | datetime  | The close date of the store                                       |      |
| EntityKey        | int       | The key pointed to DimEntity, DimStore is the subset of DimEntity |      |
| ZipCode          | nvarchar  | The zip code                                                      |      |
| ZipCodeExtension | nvarchar  | The zip code's extension                                          |      |
| StorePhone       | nvarchar  | The phone number of the store                                     |      |
| StoreFax         | nvarchar  | The fax number of the store                                       |      |
| AddressLine1     | nvarchar  | The store address                                                 |      |
| AddressLine2     | nvarchar  | The store address                                                 |      |
| CloseReason      | nvarchar  | Why the store close                                               |      |
| EmployeeCount    | int       | The number of the store staff                                     |      |
| SellingAreaSize  | float     | The size of the store                                             |      |
| LastRemodelDate  | datetime  | The last remodel day of the store                                 |      |
| GeoLocation      | geography | The store's geography location                                    |      |
| Geometry         | geometry  | The store's geometry location                                     |      |
| ETLLoadID        | int       | ETL load process ID                                               |      |
| LoadDate         | datetime  | Loaded date, used for ETL                                         |      |
| UpdateDate       | datetime  | Updated date, used for ETL                                        |      |

### DimGeography
| COLUMNS           | TYPE     | description                                                        | info |
| ----------------- | -------- | ------------------------------------------------------------------ | ---- |
| GeographyKey      | int      | The primary key of Geography table                                 | PK   |
| GeographyType     | nvarchar | The type of geography (Continent/RegionCountry/StateProvince/City) |      |
| ContinentName     | nvarchar | The  Continent Name (Asia/Europe/North America)                    |      |
| CityName          | nvarchar | The City Name (New York/Redmond/Las Vegas)                         |      |
| StateProvinceName | nvarchar | The State or Province Name (Colorado/Wisconsin/Texas/Florida)      |      |
| RegionCountryName | nvarchar | The Country or Region Name (United States/Canada/Switzerland)      |      |
| Geometry          | geometry | The geometry location data                                         |      |
| ETLLoadID         | int      | ETL load process ID                                                |      |
| LoadDate          | datetime | Loaded date, used for ETL                                          |      |
| UpdateDate        | datetime | Updated date, used for ETL                                         |      |

## Fact Tables
### FactExchangeRate
Contains exchange rates converted from other currency to basic currency of Contoso Corporate

| COLUMNS         | TYPE     | DISCRIPTION                                  | NOTES |
| --------------- | -------- | -------------------------------------------- | ----- |
| ExchangeRateKey | int      | The Primary Key                              | PK    |
| CurrencyKey     | int      | The foreign key pointed to PK in DimCurrency | FK    |
| DateKey         | datetime | Table DimDate's Primary Key                  | FK    |
| AverageRate     | float    | Average rate of the day                      |       |
| EndOfDayRate    | float    | The rate in the end of the day               |       |
| ETLLoadID       | int      | ETL load process ID                          |       |
| LoadDate        | datetime | Load date, used for ETL                      |       |
| UpdateDate      | datetime | Update date, used for ETL                    |       |


### FactInventory
Summary table, containes per store per product weekly inventory data

| COLUMNS             | TYPE     | DISCRIPTION                                          | NOTES |
| ------------------- | -------- | ---------------------------------------------------- | ----- |
| InventoryKey        | int      | Table FactInventory's Primary Key                    | PK    |
| DateKey             | datetime | Foreign key pointed to PK in DimDate                 | FK    |
| StoreKey            | int      | Foreign key pointed to PK in DimStore                | FK    |
| ProductKey          | int      | Foreign key pointed to PK in DimProduct              | FK    |
| CurrencyKey         | int      | Foreign key pointed to PK in DimCurrency             | FK    |
| OnHandQuantity      | int      | The avaliable Quantity of products                   |       |
| OnOrderQuantity     | int      | The ordered Quantity of products                     |       |
| SafetyStockQuantity | int      | The Quantity of safety stock                         |       |
| UnitCost            | money    | The average unit cost of a product                   |       |
| DaysInStock         | int      | The days of the products stayed in the stock         |       |
| MinDayInStock       | int      | The minimum days of the products stayed in the stock |       |
| MaxDayInStock       | int      | The maximum days of the products stayed in the stock |       |
| Aging               | int      | The days that goods in stock can meet sales needs    |       |
| ETLLoadID           | int      | ETL load process ID                                  |       |
| LoadDate            | datetime | Load date, used for ETL                              |       |
| UpdateDate          | datetime | Update date, used for ETL                            |       |

### FactITMachine
Contains machine procurement and maintenance costs

| COLUMNS      | TYPE     | DISCRIPTION                                     | NOTES |
| ------------ | -------- | ----------------------------------------------- | ----- |
| ITMachinekey | int      | Table FactITMachine's Primary Key               | PK    |
| MachineKey   | int      | Foreign key linked to PK in DimMachine          | FK    |
| Datekey      | datetime | Foreign key linked to PK in DimDate             | FK    |
| CostAmount   | money    | The actual cost of each machine                 |       |
| CostType     | nvarchar | The Machine Cost Type(Maintenance/Purchase/...) |       |
| ETLLoadID    | int      | ETL load process ID                             |       |
| LoadDate     | datetime | Load date, used for ETL                         |       |
| UpdateDate   | datetime | Update date, used for ETL                       |       |

### FactITSLA
Contains outage information

| COLUMNS         | TYPE     | DISCRIPTION                           | NOTES |
| --------------- | -------- | ------------------------------------- | ----- |
| ITSLAkey        | int      | Table FactITSLA's Primary Key         | PK    |
| DateKey         | datetime | Foreign key linked to PK in DimDate   | FK    |
| StoreKey        | int      | Foreign key linked to PK in DimStore  | FK    |
| MachineKey      | int      | Foreign key linked to PK inDimMachine | FK    |
| OutageKey       | int      | Foreign key linked to PK in DimOutage | FK    |
| OutageStartTime | datetime | The time when the outage happened     |       |
| OutageEndTime   | datetime | The time when the outage resolved     |       |
| DownTime        | int      | The machine down time                 |       |
| ETLLoadID       | int      | ETL load process ID                   |       |
| LoadDate        | datetime | Load date, used for ETL               |       |
| UpdateDate      | datetime | Update date, used for ETL             |       |


### FactSales
Summary table, contains per store per product daily sales data

| COLUMNS          | TYPE     | DISCRIPTION                              | NOTES |
| ---------------- | -------- | ---------------------------------------- | ----- |
| SalesKey         | int      | Table FactSales's Primary Key            | PK    |
| DateKey          | datetime | Foreign key linked to PK in DimDate      | FK    |
| ChannelKey       | int      | Foreign key linked to PK in DimChannel   | FK    |
| StoreKey         | int      | Foreign key linked to PK in DimStore     | FK    |
| ProductKey       | int      | Foreign key linked to PK in DimProduct   | FK    |
| PromotionKey     | int      | Foreign key linked to PK in DimPromotion | FK    |
| CurrencyKey      | int      | Foreign key linked to PK in Currency     | FK    |
| UnitCost         | money    | The unit cost of product                 |       |
| UnitPrice        | money    | The unit price of product                |       |
| SalesQuantity    | int      | Sale quantity                            |       |
| ReturnQuantity   | int      | Returned quantity                        |       |
| ReturnAmount     | money    | Returned amount                          |       |
| DiscountQuantity | int      | Discount quantity                        |       |
| DiscountAmount   | money    | Discount amount                          |       |
| TotalCost        | money    | Total cost                               |       |
| SalesAmount      | money    | Total sales amount                       |       |
| ETLLoadID        | int      | ETL load process ID                      |       |
| LoadDate         | datetime | Load date, used for ETL                  |       |
| UpdateDate       | datetime | Update date, used for ETL                |       |

### FactSalesQuota
Sales operational plan, not only contains Planning/Forecasting/Budgeting data,
but also contains actual sales data

| COLUMNS            | TYPE     | DISCRIPTION                             | NOTES |
| ------------------ | -------- | --------------------------------------- | ----- |
| SalesQuotaKey      | int      | Table FactSalesQuota's Primary Key      | PK    |
| StoreKey           | int      | Foreign key linked to PK in DimStore    | FK    |
| ProductKey         | int      | Foreign key linked to PK in DimProduct  | FK    |
| ChannelKey         | int      | Foreign key linked to PK in DimChannel  | FK    |
| DateKey            | datetime | Foreign key linked to PK in DimDate     | FK    |
| CurrencyKey        | int      | Foreign key linked to PK in DimCurrency | FK    |
| ScenarioKey        | int      | Foreign key linked to PK in DimScenario | FK    |
| SalesAmountQuota   | money    | The sales amount data                   |       |
| SalesQuantityQuota | money    | The sales quantity data                 |       |
| GrossMarginQuota   | money    | The Gross Margin data                   |       |
| ETLLoadID          | int      | ETL load process ID                     |       |
| LoadDate           | datetime | Loaded date, used for ETL               |       |
| UpdateDate         | datetime | Updated date, used for ETL              |       |


### FactStrategyPlan
Corporate strategic plan, contains the whole group's monthly Actual/Forecasting/Budgeting Profit & Loss data
| COLUMNS            | TYPE     | DISCRIPTION                                    | NOTES |
| ------------------ | -------- | ---------------------------------------------- | ----- |
| StrategyPlanKey    | int      | Table FactStrategyPlan's Primary Key           | PK    |
| Datekey            | datetime | Foreign key linked to PK in DimDate            | FK    |
| EntityKey          | int      | Foreign key linked to PK in DimEntity          | FK    |
| ScenarioKey        | int      | Foreign key linked to PK in DimScenario        | FK    |
| AccountKey         | int      | Foreign key linked to PK in DimAccount         | FK    |
| CurrencyKey        | int      | Foreign key linked to PK in DimCurrency        | FK    |
| ProductCategoryKey | int      | Foreign key linked to PK in DimProductCategory | FK    |
| Amount             | money    | The amount of Actual/budget/forecast           |       |
| ETLLoadID          | int      | ETL load process ID                            |       |
| LoadDate           | datetime | Loaded date, used for ETL                      |       |
| UpdateDate         | datetime | Updated date, used for ETL                     |       |


### FactOnlineSales
Sales transactional data, contains each sales transactions occurred in on-line store
| COLUMNS              | TYPE     | DISCRIPTION                              | NOTES |
| -------------------- | -------- | ---------------------------------------- | ----- |
| OnlineSalesKey       | int      | Table FactOnlineSales's Primary Key      | PK    |
| DateKey              | datetime | Foreign key linked to PK in DimDate      | FK    |
| StoreKey             | int      | Foreign key linked to PK in DimStore     | FK    |
| ProductKey           | int      | Foreign key linked to PK in DimProduct   | FK    |
| PromotionKey         | int      | Foreign key linked to PK in DimPromotion | FK    |
| CurrencyKey          | int      | Foreign key linked to PK in Currency     | FK    |
| CustomerKey          | int      | Foreign key linked to PK in Customer     |       |
| SalesOrderNumber     | nvarchar | The PO number                            |       |
| SalesOrderLineNumber | int      | Line item of a specific Sales Order      |       |
| SalesQuantity        | int      | Sale quantity                            |       |
| SalesAmount          | money    | Sales amount                             |       |
| ReturnQuantity       | int      | The quantity of return goods             |       |
| ReturnAmount         | money    | The amount of return goods               |       |
| DiscountQuantity     | int      | Discount quantity                        |       |
| DiscountAmount       | money    | Discount amount                          |       |
| TotalCost            | money    | Total cost                               |       |
| UnitCost             | money    | Unit cost                                |       |
| UnitPrice            | money    | Unit price                               |       |
| ETLLoadID            | int      | ETL load process ID                      |       |
| LoadDate             | datetime | Loaded date, used for ETL                |       |
| UpdateDate           | datetime | Updated date, used for ETL               |       |
