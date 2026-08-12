# End-to-End Azure Car Data Engineering Pipeline

## Overview
Automated ETL data pipeline built using Azure Data Factory, Databricks (PySpark), and Azure Key Vault to ingest raw car market data, perform data transformation, and store clean business metrics into Gold Delta Lake.

## Architecture & Data Flow
1. **Source / Bronze Layer**: ADLS Gen2 (Raw CSV Ingestion).
2. **Ingestion & In-Memory Data Flow**: ADF Data Flow cleans schema, trims spaces, handles typecasting, and exports Parquet data.
3. **Silver Layer**: ADLS Gen2 (Parquet Data Storage).
4. **Gold Layer (Databricks + PySpark)**: Reads Silver Parquet files via Secure PAT Token authentication using Azure Key Vault, applies SQL/Spark aggregations, and writes back in Delta format.

## Tech Stack
* **Orchestration**: Azure Data Factory (ADF)
* **Compute / Processing**: Azure Databricks (PySpark, Delta Lake)
* **Storage**: Azure Data Lake Storage Gen2 (ADLS Gen2)
* **Security**: Azure Key Vault (RBAC Managed Access, Secret Storage)

## Setup Instructions
1. Import ADF ARM Templates located under `adf/`.
2. Configure Azure Key Vault linked service `ls_KeyVault` with secret `Databricks-PAT-Token`.
3. Import the Python notebook `NB_Cars_Business_Logic.py` in Azure Databricks.
4. Execute the pipeline from Data Factory.
