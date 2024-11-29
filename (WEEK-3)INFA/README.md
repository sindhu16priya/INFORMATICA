# Informatica Project: ETL Process with SCD Type 1 and Fact Table Construction

This in-house infrmatica project demonstrates ETL (Extract,Transform,Load) workflow using **Informatica PowerCenter** to process flat file data,implement Slowly Changing Dimensions Type 1 (SCD1) and build a fact table for analytics.

---
## Overview

### Objective
- **Ingest** flat file data into staging and dimension tables.
- **Apply** SCD1 logic to maintain updated records in dimension tables.
- **Construct** a fact table from the transformed data.

---
## ETL Process Workflow

### 1. **Flat File Data Ingestion**
- **Source**: Flat files containing transactional data (e.g., customer, product, sales details).
- **Staging Tables**: Data loaded into staging tables for initial processing.
  - Created corresponding source-to-target mappings in Informatica.
  - Applied data cleansing and validations during this step.

---
### 2. **SCD1 Implementation**
- **Target**: Dimension tables (e.g., `dim_customer`, `dim_product`).
- **Logic**:
  - Checked if incoming records matched existing records.
  - Updated existing records if changes were detected.
  - Inserted new records for previously unseen entities.
- **Key Highlights**:
  - Ensured no historical data storage (overwrites old records).
  - Used **Update Strategy Transformation** for inserts/updates.
NOTE: I IMPLEMENTED "SCD-2" FOR PRODUCTS 
---
### 3. **Fact Table Construction**
- **Fact Table**: Combined dimension table references and transactional data into a denormalized format for analytics.
- **Transformations**:
  - Joined dimension tables with the staging data to fetch surrogate keys.
  - Aggregated transactional data as required (e.g., total sales per region).
- **Load**:
  - Used **Lookup Transformations** to fetch surrogate keys from dimension tables.
  - Inserted records into the fact table.
---
## Key Components

### Informatica Transformations Used:
- **Source Qualifier**: To read flat file data into the mapping.
- **Expression**: For data cleansing and applying business rules.
- **Lookup**: For fetching existing dimension records.
- **Update Strategy**: To implement SCD1 (Insert/Update logic).
- **Router**: To segregate new and existing records.
- **Aggregator**: For data summarization in the fact table.

## Results
- Dimension tables updated dynamically using SCD1 rules.
- Fact table populated with consistent and analytics-ready data.
- Workflow optimized for performance and scalability.


