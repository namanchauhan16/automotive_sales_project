# Automotive Sales Data Engineering Pipeline

## Project Overview

This project is an end-to-end Automotive Sales Data Engineering Pipeline built using Microsoft Azure cloud services and Medallion Architecture.

The project processes automotive sales data containing information related to:
- Vehicle brands and models
- Dealers and branches
- Revenue generated
- Units sold
- Sales dates

The raw data is extracted from Azure SQL Database and GitHub using Azure Data Factory and stored in Azure Data Lake Storage Gen2 in Parquet format.

The pipeline follows Bronze, Silver, and Gold layered architecture where data is incrementally processed, transformed, and modeled for analytics and reporting. Final business-ready data is connected to Power BI for dashboarding and visualization.

This project demonstrates concepts like:
- Data Ingestion
- Incremental Loading
- Data Transformation
- Medallion Architecture
- Fact and Dimension Modeling
- Cloud Data Storage
- Data Orchestration using Azure Services

---

# Architecture Diagram

_Add your architecture image here_

```md
![Architecture Diagram](architecture/project_architecture.png)
```

---

# Tech Stack Used

- Azure Data Factory
- Azure Databricks
- Azure SQL Database
- Azure Data Lake Storage Gen2
- PySpark
- SQL
- Delta Lake
- Parquet Files

---

# Project Flow / Pipeline Flow

### 1. Data Source

The source data is available in:
- Azure SQL Database
- GitHub datasets/files

The data contains automotive sales information including revenue, units sold, dealer details, and vehicle brands.

---

### 2. Data Ingestion using Azure Data Factory

Azure Data Factory is used to orchestrate the complete pipeline.

Pipeline flow:
- First, the pipeline fetches:
  - Last Load Date
  - Current Load Date

- Based on these values, incremental loading is performed.

- Raw source data is then extracted and stored into Azure Data Lake Storage Gen2 in Parquet format.

---

### 3. Bronze Layer (Raw Layer)

The Bronze layer stores raw ingested automotive sales data.

- Data format: Parquet
- Storage: ADLS Gen2
- No transformations applied
- Historical raw data is maintained

Purpose:
- Raw data storage
- Incremental data support
- Backup and auditing

---

### 4. Silver Layer (Transformation Layer)

The Silver layer is created inside Azure Databricks.

In this layer:
- Bronze layer data is fetched
- Data cleaning is performed
- Null values are handled
- Schema corrections are applied
- Business transformations are implemented

The transformed data is then stored back into ADLS.

---

### 5. Gold Layer (Business Layer)

The Gold layer contains analytics-ready business data.

In this layer:
- Data from Silver layer is processed
- Fact tables and Dimension tables are created
- Data modeling is implemented
- Curated business datasets are generated

Example tables:
- Fact_Sales
- Dim_Dealer
- Dim_Branch
- Dim_Product
- Dim_Date

---

### 6. Reporting and Analytics

The final Gold layer data contains business-ready curated datasets that can be used for reporting, analytics, and dashboard creation.

This data can be connected with reporting tools such as:
- Power BI
- Tableau
- Excel
- Other BI and analytics platforms

The Gold layer is optimized for business analysis and decision-making.

---

# Medallion Architecture

This project follows Medallion Architecture:

| Layer | Purpose |
|---|---|
| Bronze | Stores raw automotive sales data |
| Silver | Stores cleaned and transformed data |
| Gold | Stores analytics-ready business data |

---

# Features Implemented

- End-to-End Azure Data Engineering Pipeline
- Automotive Sales Data Processing
- Azure Data Factory Orchestration
- Incremental Data Loading
- Medallion Architecture
- Data Transformation using PySpark
- Fact and Dimension Modeling
- Delta Lake Implementation
- Parquet File Storage
- ADLS Gen2 Integration
- Power BI Reporting Integration
- Cloud-based Data Processing using Azure
