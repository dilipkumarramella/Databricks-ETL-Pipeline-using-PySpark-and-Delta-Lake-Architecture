# Databricks ETL Pipeline - PySpark and Delta Lake
This project demonstrates the design and implementation of a modern Lakehouse architecture on Azure, built for scalable, reliable, and automated data processing.

The pipeline ingests raw data, applies multi-layered transformations (Bronze → Silver → Gold), and produces curated Delta tables for analytics and reporting. Orchestration is handled via Azure Data Factory (ADF) and Databricks Jobs, with built-in monitoring, notifications, and governance.

Unlike academic projects, this initiative reflects real-world enterprise practices — ingestion pipelines, orchestration, IAM-based security, incremental transformations, and enriched analytics-ready data. 

Why this project matters: It reflects real-world Data Engineering best practices—something I can bring directly into your engineering team.

## Tech Stack  

| Layer               | Technology Used                                                                 |
|---------------------|---------------------------------------------------------------------------------|
| **Storage**         | Azure Data Lake Storage Gen2 (ADLS)                                             |
| **Compute/ETL**     | Azure Databricks (PySpark, Delta Lake)                                          |
| **Orchestration**   | Azure Data Factory (ADF Pipelines), Databricks Jobs                             |
| **Data Formats**    | Delta, Parquet                                                                  |
| **Governance**      | Azure IAM (RBAC, token-based access), Resource Templates                        |
| **Analytics**       | Power BI (optional downstream for visualization)                                |

## Data Flow
- Bronze Layer (Raw Ingest)
  - Used Kaggle API for automated dataset extraction. 
  - Stored raw data as ingested from source
  - Schema applied but no business logic

- Silver Layer (Curated Clean Data)
  - PySpark transformations:
    - Null handling
    - Data type casting
    - Removal of unwanted characters (regex cleaning)
    - Consistent schema enforcement

- Gold Layer (Business-Ready Data)
  - Added business-derived features:
    - Movie Era → (Old, Middle, Recent)
    - Rating Category → (Highly Rated, Good, Moderate, Low)
    - Popularity → (Most Popular, Moderate, Low)
  - Stored as Delta tables and Parquet for downstream analytics

## Orchestration

- Azure Data Factory (ADF):
  - Executes Databricks notebooks sequentially with success conditions
  - Scheduled weekly pipeline runs

- Databricks Jobs:
  - Runs daily automated jobs
  - Configured with failure email notifications

## Security & Governance

- **Secrets Management:** Stored credentials in Azure Key Vault; accessed securely in Databricks via Secret Scopes.  
- **Authentication:** Used OAuth 2.0 with Service Principal; IAM roles assigned with least-privilege access (Storage Blob Data Contributor).  
- **Secure Data Access:** Mounted ADLS Gen2 in Databricks without exposing keys.  
- **Governance:** All resources deployed via ARM Templates; notebooks & pipelines exported for auditability.  

## Outputs
- Cleaned & enriched data in Delta format (Silver, Gold)
- Delta Tables registered in Databricks
- Gold layer Parquet exported for BI/analytics

## Key Highlights

- Self-initiated industry-style project, not coursework
- PySpark-based scalable transformations on Databricks
- Real-world Lakehouse design (Bronze → Silver → Gold)
- Automated with ADF pipelines + Databricks Jobs
- Secure & production-ready with IAM roles
- Value-added business features for analytics readiness
