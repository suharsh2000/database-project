# AdventureWorks ETL & Data Warehousing Project

This project demonstrates a complete ETL pipeline from an OLTP system (AdventureWorks2014) to a Data Warehouse using SQL Server Integration Services (SSIS). It focuses on transforming data from Human Resources and Sales modules into a structured dimensional model using best practices in data warehousing.

## Project Structure

- **OLTP Source**: AdventureWorks2014
- **Staging Database**: AWN_STG_Demo
- **Data Warehouse**: AWN_DW_Demo
- **ETL Tool**: SSIS (SQL Server Integration Services)

## Technologies Used

- Microsoft SQL Server (T-SQL)
- SSIS (Data Flow Tasks, Control Flow, Derived Columns)
- SQL Server Management Studio (SSMS)
- Stored Procedures & Views
- ETL Design & Optimization

---

## Key Features

- ✅ Extract, Transform, Load (ETL) processes via SSIS
- ✅ Dimensional modeling (Fact & Dimension tables)
- ✅ Incremental and full data loading support
- ✅ Data quality transformations using derived columns
- ✅ Performance optimization with indexing and query tuning
- ✅ Data governance: default values, constraints, and security

---

## SSIS Package Highlights

### Package.dtsx
- **OLE DB Source** → `erp.Currency`
- **Derived Column**: Adds audit metadata (`ServerExecutionID`, `Created_Dt`)
- **OLE DB Destination**: Inserts into `DimCurrency`

### incremental.dtsx
- **Expression Task**: Conditional logic to control incremental/full loads
- **Container Tasks**:
  - Get Last Sale Date
  - Truncate & Load `SalesHeader` and `SalesDetail` tables based on logic

---

##  SQL Scripts Included

- Creation scripts for:
  - `AWN_STG_Demo` and `AWN_DW_Demo` databases
  - All relevant schemas, tables, views
- ETL Stored Procedures:
  - `Refresh_DimCurrency`
  - `Refresh_DimCustomer`
  - `Refresh_DimProduct`
  - `Refresh_DimSalesTerritory`
  - `Refresh_FactEmployeePay`

---

## Dimensional Tables (DW)

| Dimension | Source Table/View                  |
|-----------|-------------------------------------|
| DimCurrency | erp.Currency                      |
| DimCustomer | Stg_vw_Erp_Customer               |
| DimProduct  | Stg_vw_Erp_Product                |
| DimEmployee | hr.Employee + Department History  |
| DimReseller | erp.Store                         |
| DimSalesTerritory | erp.SalesTerritory         |

| Fact Table        | Description                      |
|-------------------|----------------------------------|
| FactInternetSales | Online order transactions        |
| FactResellerSales | Reseller-based sales             |
| FactEmployeePay   | Employee pay history per month   |



