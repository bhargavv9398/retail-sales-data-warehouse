Retail Sales ETL & Data Warehouse Project
Project Overview

This project implements an end-to-end ETL (Extract, Transform, Load) and Data Warehouse solution for a Retail Sales domain using:

Amazon Web Services S3 for cloud storage
Databricks for ETL processing and data warehousing
Delta Lake for scalable and reliable data management

The project follows the Medallion Architecture:

1.Bronze Layer
2.Silver Layer
3.Gold Layer

The solution includes:

1.Incremental Loading
2.SCD Type-2 Implementation
3.Archival Process
4.ETL Validation Framework
5.ETL Logging
6.Workflow Automation

Architecture
S3 Raw Files
      ↓
Archival Process
      ↓
Bronze Layer
      ↓
Silver Layer
      ↓
Gold Layer
      ↓
SCD Type-2
      ↓
Validation Layer
      ↓
ETL Logging
      ↓
Databricks Workflow Automation


Technologies Used:
| Technology             | Purpose                          |
| ---------------------- | -------------------------------- |
| Amazon Web Services S3 | Cloud Storage                    |
| Databricks             | ETL Processing & Data Warehouse  |
| SQL                    | Data Transformation & Validation |
| Delta Lake             | Incremental Processing & MERGE   |
| GitHub                 | Version Control                  |


Project Structure:
Retail-Sales-ETL-Project/

├── bronze.sql
├── silver.sql
├── gold.sql
├── archival.py
├── ETL Validation.sql
├── ETL Logging.sql
├── Validation Reports/
├── screenshots/
├── architecture/
└── README.md

Data Layers
1. Bronze Layer

Purpose:

Load raw CSV files from S3
Preserve original source data

Tables:

customers_raw
products_raw
stores_raw
sales_raw

Activities:

Raw ingestion
Basic schema inference
2. Silver Layer

Purpose:

Data cleansing and standardization

Transformations:

Trim spaces
Lowercase conversion
Proper case formatting
Remove duplicates
Handle null values
Data type casting
Invalid data filtering

Tables:

customers_silver
products_silver
stores_silver
sales_silver
3. Gold Layer

Purpose:

Create business-ready warehouse tables

Tables:

dim_customer
dim_product
dim_store
fact_sales

Business Use Cases:

Revenue analysis
Top customers
Product sales analysis
Regional performance reporting
SCD Type-2 Implementation

Implemented in:

gold.dim_customer

Features:

Historical data tracking
Active vs inactive records
StartDate & EndDate management

Example:

Old customer record becomes inactive
New updated customer record inserted
Incremental Load

Implemented using:

Delta Lake MERGE
Timestamp-based file processing

Features:

Process only new or changed records
Avoid full data reload
Improve ETL performance
Archival Process

Purpose:

Move old processed files into archive folders
Retain only latest files in raw layer

Archive Structure:

archive/
├── customers_src/
├── products_src/
├── stores_src/
└── sales_transactions_src/
ETL Validation Framework

Validation Types Included:

Source to Target Validation
Row count validation
Column mapping validation
Data type validation
Data Transformation Validation
Trim validation
Lowercase validation
Proper case validation
Derived amount validation
Date format validation
Data Quality Validation
Duplicate checks
Null handling validation
Invalid data rejection
Referential integrity validation
SCD Type-2 Validation
Active vs inactive record validation
Historical data validation
StartDate & EndDate validation
Incremental Load Validation
Full load validation
Incremental load validation
Changed customer record validation
ETL Logging

Logging includes:

Process name
Table name
Rows processed
Execution timestamp
Status

Purpose:

Monitoring
Audit tracking
Troubleshooting
Workflow Automation

The complete ETL pipeline is automated using Databricks Workflows.

Automated Flow:

File Arrival
   ↓
Archival
   ↓
Bronze Load
   ↓
Silver Transformation
   ↓
Gold Load
   ↓
SCD Type-2
   ↓
Validation
   ↓
Logging
Real-Time Business Scenario

A retail company generates daily customer and sales transaction files from multiple stores.

The ETL pipeline:

ingests source data into S3
processes data through Bronze, Silver, and Gold layers
maintains historical customer changes using SCD Type-2
performs incremental loading
validates data quality
automates complete ETL processing
Key Features
End-to-End ETL Pipeline
Medallion Architecture
SCD Type-2
Incremental Loading
Delta Lake MERGE
Automated Archival Process
ETL Validation Framework
ETL Logging
Workflow Automation
Cloud-Based Data Warehouse
Future Enhancements
Dashboard integration
Real-time streaming ingestion
CI/CD deployment
Advanced monitoring and alerting
Data quality dashboards