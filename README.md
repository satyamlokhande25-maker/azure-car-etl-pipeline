# Azure Car Data Engineering Pipeline

An end-to-end cloud data engineering pipeline for ingesting raw car-market data, applying transformation and business logic, and producing curated Gold-layer Delta data using Azure services.

## Architecture

```text
ADLS Gen2 — Bronze / Raw CSV
            ↓
Azure Data Factory
Schema cleanup • trimming • type casting
            ↓
ADLS Gen2 — Silver / Parquet
            ↓
Azure Databricks + PySpark
Business transformations & aggregations
            ↓
Delta Lake — Gold / Curated Metrics
```

## Technology Stack

- **Orchestration:** Azure Data Factory
- **Processing:** Azure Databricks, PySpark
- **Storage:** Azure Data Lake Storage Gen2
- **Table Format:** Delta Lake
- **Security:** Azure Key Vault / RBAC

## Key Engineering Concepts

- Medallion-style Bronze/Silver/Gold architecture
- Cloud-based ETL orchestration
- Schema and data-type standardization
- PySpark transformations and aggregations
- Secret management through Azure Key Vault
- Curated Delta Lake outputs for analytics

## Repository Structure

```text
adf/                         # Azure Data Factory templates
NB_Cars_Business_Logic.py    # Databricks/PySpark business logic
README.md                    # Project documentation
```

## Deployment / Setup

1. Import the ADF ARM templates from `adf/`.
2. Configure the Key Vault linked service.
3. Store the Databricks credential/token as a Key Vault secret.
4. Import `NB_Cars_Business_Logic.py` into Databricks.
5. Configure linked services, datasets, and parameters for your environment.
6. Execute and monitor the pipeline from Azure Data Factory.

## Security

Secrets should remain in Azure Key Vault and should never be hardcoded in notebooks, pipeline definitions, or Git history. Prefer managed identities/RBAC where supported by the deployment architecture.

## Future Enhancements

- Add automated data-quality gates
- Add incremental ingestion and watermarking
- Add CI/CD for ADF and Databricks artifacts
- Add pipeline observability and alerting
- Add schema-drift handling
- Add automated testing for PySpark transformations

## Author

**Satyam Lokhande**  
Azure Data Engineering • PySpark • ADF • Databricks • ADLS • Delta Lake
