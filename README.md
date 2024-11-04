# Flat Table Remodeling to Star Schema using Azure Data Stack

## Project Overview

This project involves transforming a flat table into a star schema to optimize data storage, retrieval, and analysis in a data warehouse environment. Using Azure Data Factory, Azure Key Vault, Azure SQL Database, and Azure Blob Storage, the flat table (in CSV format) was ingested, processed, and transformed into a dimension star schema suitable for business intelligence (BI) analysis and reporting.

---

## Problem Statement

A flat table structure often presents challenges for BI analysis, including:
- **Complex Querying**: Difficulties in querying due to data redundancy and lack of structured relationships.
- **Slow Performance**: Increased query times due to larger dataset sizes.
- **Limited Analytics**: Raw data structures are not optimized for advanced analytical queries.

To address these issues, we structured the data into a star schema, significantly improving query performance and supporting efficient BI analysis.

---

## Solution Overview

### Workflow Summary
1. **Data Ingestion**: CSV file uploaded to Azure Blob Storage.
2. **Data Transformation**: Restructuring the flat table into a star schema with dimension tables.
3. **Data Loading**: Inserting data into Azure SQL Database for structured storage.
4. **Incremental Refresh**: Using `transaction_date` to process only new or updated records.

### Architecture Diagram

![Untitled Diagram drawio](https://github.com/user-attachments/assets/89188d88-aca1-465d-ac5a-84db0712c73d)

---

## Azure Tools and Services Used

Each Azure service was chosen to handle specific requirements for secure, scalable, and efficient data processing.

### Azure Blob Storage
- **Purpose**: Storage for the source CSV file.
- **Reason for Use**: Provides a scalable, secure, and accessible solution for handling large datasets.

### Azure Data Factory (ADF)
- **Purpose**: Primary ETL (Extract, Transform, Load) tool for orchestrating data ingestion and transformation.
- **Reason for Use**: Provides efficient, code-minimal workflows for data ingestion, transformation, and scheduling.

### Azure Key Vault
- **Purpose**: Securely stores credentials and connection strings.
- **Reason for Use**: Maintains security best practices by safely storing sensitive information, avoiding hardcoding.

### Azure SQL Database
- **Purpose**: Storage of the transformed data in a structured star schema format.
- **Reason for Use**: Optimized for relational data, enabling high-performance querying and efficient data retrieval for analytics.

---

## Implementation Steps

### 1. Data Ingestion
- **Step 1**: Upload the CSV file to Azure Blob Storage.
- **Step 2**: Use Azure Data Factory’s **Copy Activity** to transfer the CSV data from Blob Storage to an Azure SQL Database staging table.

### 2. Data Transformation
- **Data Flow in ADF**:
  - **Extraction**: Using Data Flow to split the flat table into dimension and fact tables.
  - **Logic**:
    - Define **Insert/Update** logic to manage data changes.
    - Set up **Incremental Refresh** based on `transaction_date` to process only new or updated records.

### 3. Data Loading
- **Step 1**: Load transformed data into Azure SQL Database, creating fact and dimension tables.
- **Step 2**: Validate table relationships to ensure correct schema and star schema structure.

---

![Marketting_infinox](https://github.com/user-attachments/assets/f12b59c9-2389-422e-9848-60c89541da8f)


---

## Key Project Components

- **Fact Table**: Holds transactional data and foreign keys referencing dimension tables.
- **Dimension Tables**: Store related information for attributes such as customer, product, and time dimensions, improving join efficiency.

---

## Downstream Task: BI Analyst

With the star schema in place, downstream tasks benefit from:
- **Optimized BI Reporting**: Faster data access supports complex KPI tracking and reporting.
- **Improved Query Performance**: The simplified schema structure reduces query complexity.
- **Enhanced Scalability**: Easily adaptable data structure for future data expansions.

---

## Benefits of Star Schema Transformation

- **Improved Query Performance**: Simplified structure for faster joins.
- **Optimized Storage**: Dimension tables reduce data redundancy.
- **Easy Maintenance**: Incremental loading keeps data current while minimizing resource use.

---

## Conclusion

This project demonstrates a complete ETL pipeline using Azure Data Stack for transforming a flat table into a star schema. The star schema enables efficient data processing, supports incremental loading, and prepares data for advanced BI analysis and reporting. 

Future steps include maintenance practices, potential integrations with additional BI tools, and monitoring to ensure ongoing data integrity.

---

## Acknowledgments

- Azure documentation and tutorials for guidance.
- Team members for their collaboration and support.
