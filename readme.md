# CareSync ADF Data Pipeline

A comprehensive Azure Data Factory solution for healthcare data integration, transformation, and analysis. This project demonstrates enterprise-grade data engineering with cloud-native architecture.

## 🎯 Project Overview

CareSync is an automated data pipeline built on Azure Data Factory (ADF) that manages healthcare-related data workflows. It handles data ingestion from multiple sources, implements sophisticated transformations, and delivers clean, validated data to data warehouses and analytics platforms.

**Key Objectives:**
- Automate healthcare data ingestion and validation
- Implement scalable ETL/ELT transformations
- Ensure data quality and compliance
- Enable real-time analytics capabilities
- Reduce manual data processing overhead

## 🏗️ Architecture

```
[Data Sources]
(Healthcare Systems, APIs, Files)
    ↓
[Azure Data Factory]
├→ Linked Services (Connection Management)
├→ Datasets (Data Schema Definition)
├→ Pipelines (ETL Orchestration)
└→ Activities (Transformation Logic)
    ↓
[Azure Data Lake Storage]
├→ Raw Layer (Source data)
├→ Processed Layer (Transformed data)
└→ Output Layer (Analytics-ready data)
    ↓
[Azure SQL Database / Synapse]
    ↓
[Power BI / Analytics Tools]
```

## 🛠️ Tech Stack

- **Cloud Platform:** Azure
- **Core Services:**
  - Azure Data Factory (ADF)
  - Azure Data Lake Storage Gen2
  - Azure SQL Database
  - Azure Synapse Analytics (optional)
- **Languages:** SQL, PySpark, PowerShell
- **CI/CD:** GitHub Actions, Azure DevOps
- **Monitoring:** Azure Monitor, Application Insights

## 📁 Project Structure

```
caresync-adf-repo/
├── dataset/                # Data source & sink definitions
│   ├── source_datasets/
│   ├── sink_datasets/
│   └── lookup_datasets/
├── linkedService/          # Connection configurations
│   ├── sql_linked_service.json
│   ├── storage_linked_service.json
│   ├── api_linked_service.json
│   └── healthcare_system_services.json
├── pipeline/               # ETL workflow definitions
│   ├── main_pipeline.json
│   ├── validation_pipeline.json
│   ├── transformation_pipeline.json
│   └── load_pipeline.json
├── dataflow/               # PySpark transformation logic
│   ├── data_cleaning.py
│   ├── deduplication.py
│   └── enrichment.py
├── notebooks/              # Databricks notebooks
│   ├── data_exploration.ipynb
│   └── quality_checks.ipynb
├── publish_config.json     # Deployment configuration
├── README.md
└── .gitignore
```

## 🚀 Setup & Installation

### Prerequisites
- Azure subscription with appropriate permissions
- Azure Data Factory workspace
- Azure Storage account (Gen2)
- Azure SQL Database or Synapse workspace
- Azure DevOps or GitHub repository
- Power BI (optional, for reporting)

### Deployment Steps

1. **Clone the repository:**
   ```bash
   git clone https://github.com/vinayshetty777/caresync-adf-repo.git
   cd caresync-adf-repo
   ```

2. **Configure Azure Resources:**
   ```bash
   # Set variables
   export RESOURCE_GROUP=caresync-rg
   export ADF_NAME=caresync-adf
   export STORAGE_ACCOUNT=caresyncstore
   
   # Create resources (or use existing)
   az group create --name $RESOURCE_GROUP --location eastus
   ```

3. **Deploy Data Factory:**
   - Import the pipeline definitions into your ADF workspace
   - Configure linked services with your credentials
   - Set dataset connections to your Azure resources

4. **Configure Linked Services:**
   - Update `linkedService/` JSON files with your connection strings
   - Set authentication credentials (connection strings, managed identity, etc.)
   - Validate connections in ADF UI

5. **Deploy Pipelines:**
   ```bash
   # Use ADF Publish feature in Azure Portal
   # Or use ARM templates for Infrastructure as Code
   ```

## 📊 Data Flow

### Pipeline Stages

**1. Ingestion Pipeline**
- Source data collection from healthcare systems
- API polling or file uploads
- Initial schema validation
- Storage in Raw (Bronze) layer

**2. Validation Pipeline**
- Data quality checks
- Completeness validation
- Duplicate detection
- Error logging and alerting

**3. Transformation Pipeline**
- Data cleansing and standardization
- Business logic implementation
- Enrichment with reference data
- Aggregations and calculations

**4. Load Pipeline**
- Write to Silver (processed) layer
- Load to Gold (analytics-ready) layer
- Update dimensional tables
- Trigger downstream processes

## 🔄 ETL Workflow

```
Raw Data (Bronze Layer)
    ↓
[Validation Checks]
- Data type verification
- Null value handling
- Format standardization
    ↓
[Transformations]
- Cleansing
- Deduplication
- Business logic
    ↓
[Data Enrichment]
- Reference data joins
- Calculated fields
- Aggregations
    ↓
Analytics-Ready Data (Gold Layer)
    ↓
[Power BI / SQL Analysis]
```

## 🎯 Key Features

### Data Quality
- Automated validation rules
- Quality score calculations
- Error detection and logging
- Data lineage tracking

### Performance
- Parallel processing capabilities
- Incremental load patterns
- Scheduled vs. event-triggered runs
- Resource optimization

### Scalability
- Cloud-native architecture
- Auto-scaling capabilities
- Handles large data volumes
- Multi-source integration

### Security
- Managed identity authentication
- Encrypted connections
- HIPAA compliance ready
- Audit logging

## 🔧 Configuration

### Setting Up Linked Services

```json
{
  "name": "AzureSQLDatabaseLinkedService",
  "properties": {
    "type": "AzureSqlDatabase",
    "typeProperties": {
      "connectionString": "Server=tcp:server.database.windows.net;Database=db;..."
    }
  }
}
```

### Creating Datasets

```json
{
  "name": "SourceDataset",
  "properties": {
    "linkedServiceName": "SourceLinkedService",
    "type": "AzureSqlTable",
    "typeProperties": {
      "table": "source_table"
    }
  }
}
```

## 📈 Monitoring & Alerts

- **ADF Monitor:** Track pipeline runs and activity status
- **Azure Monitor:** Collect metrics and logs
- **Alerts:** Set up notifications for failures
- **Application Insights:** Detailed diagnostics

```bash
# View pipeline runs
az datafactory pipeline-run query-by-factory \
  --resource-group caresync-rg \
  --factory-name caresync-adf
```

## 🧪 Testing

### Validation Tests
```sql
-- Check data completeness
SELECT COUNT(*) FROM processed_table
WHERE required_column IS NULL;

-- Verify data quality
SELECT COUNT(*) FROM processed_table
WHERE quality_score < 0.8;
```

## 🐛 Troubleshooting

### Pipeline Execution Issues

**Error: "Linked Service Connection Failed"**
- Verify connection strings are correct
- Check network security groups (NSGs)
- Ensure managed identity has permissions

**Error: "Column Not Found"**
- Validate source schema hasn't changed
- Update dataset definitions
- Check transformation logic

**Performance Issues**
- Analyze Data Factory logs
- Optimize data volumes in transformations
- Consider parallel execution

## 🔐 Best Practices

✅ **Do:**
- Use managed identities for authentication
- Implement error handling in all pipelines
- Version control all definitions
- Monitor cost and optimize resources
- Document data lineage

❌ **Don't:**
- Store credentials in code
- Ignore transformation errors
- Run full refreshes when incremental is possible
- Overlook data quality checks

## 🤝 Contributing

To contribute improvements:
1. Create a feature branch
2. Update pipeline definitions
3. Add documentation
4. Submit pull request with testing details

## 📚 Documentation

- [Azure Data Factory Documentation](https://docs.microsoft.com/en-us/azure/data-factory/)
- [Data Lake Storage Best Practices](https://docs.microsoft.com/en-us/azure/storage/blobs/data-lake-storage-best-practices)
- [Azure SQL Database Documentation](https://docs.microsoft.com/en-us/azure/azure-sql/database/)

## 🔗 Related Projects

- [Databricks_bootcamp_2026](https://github.com/vinayshetty777/Databricks_bootcamp_2026)
- [SQL-DataWareHouse-Project](https://github.com/vinayshetty777/SQL-DataWareHouse-Project)

---

**Project Status:** Active Development  
**Last Updated:** 2026-09-27  
**Azure SDK Version:** Latest (2024)
