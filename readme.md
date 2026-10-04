# CareSync ADF Repository

Enterprise-grade healthcare data pipeline built on Azure Data Factory. Demonstrates cloud-native data engineering with automated ETL, data quality checks, and analytics-ready outputs.

## 📋 Overview

CareSync is an automated data pipeline managing healthcare-related data workflows. It handles data ingestion from multiple sources, implements sophisticated transformations, and delivers clean, validated data to data warehouses and analytics platforms.

**Tech:** Azure Data Factory, Azure Data Lake, SQL Server, PySpark  
**Architecture:** Bronze-Silver-Gold medallion pattern  
**Status:** 📈 Production Pipeline

---

## 🏗️ Architecture

```
[Data Sources]
    ↓
[Azure Data Factory]
├→ Linked Services (Connection Management)
├→ Datasets (Schema Definition)
├→ Pipelines (ETL Orchestration)
└→ Activities (Transformation Logic)
    ↓
[Azure Data Lake Storage]
├→ Raw Layer (Bronze)
├→ Processed Layer (Silver)
└→ Analytics Layer (Gold)
    ↓
[Azure SQL Database / Analytics]
```

---

## 🛠️ Tech Stack

| Component | Technology |
|-----------|------------|
| **Cloud** | Azure |
| **ETL** | Azure Data Factory |
| **Storage** | Azure Data Lake Gen2 |
| **Database** | Azure SQL Server |
| **Processing** | PySpark, Spark SQL |
| **Languages** | SQL, Python, PowerShell |

---

## 📁 Project Structure

```
caresync-adf-repo/
├── dataset/                   # Data definitions
├── linkedService/             # Connection configs
├── pipeline/                  # ETL workflows
├── dataflow/                  # Spark transformations
├── notebooks/                 # Databricks notebooks
├── sql/                       # SQL scripts
├── publish_config.json        # Deployment config
└── README.md
```

---

## 🚀 Quick Start

### Prerequisites
- Azure subscription
- Azure Data Factory workspace
- Azure Storage account
- SQL Server/Database

### Deployment

```bash
# Clone repository
git clone https://github.com/vinayshetty777/caresync-adf-repo.git

# Create Azure resources
az group create --name caresync-rg --location eastus
az storage account create --name caresyncstore --resource-group caresync-rg

# Deploy using ARM template or ADF UI
# Import pipeline definitions to your ADF workspace
```

---

## 📊 Data Flow

```
Raw Data (Bronze)
    ↓
[Validation & Cleaning]
    ↓
Processed Data (Silver)
    ↓
[Aggregations & Modeling]
    ↓
Analytics Data (Gold)
    ↓
[Power BI / SQL Analysis]
```

---

## ✨ Key Features

- **Automated Data Ingestion** - From multiple healthcare systems
- **Data Quality Checks** - Validation and error logging
- **Scalable Architecture** - Handles large data volumes
- **PySpark Transformations** - Complex business logic
- **Security** - Managed identity authentication
- **Compliance** - HIPAA-ready infrastructure

---

## 🔧 Configuration

### Linked Services
Update connection strings for your Azure resources:
- Azure Storage
- SQL Server
- Data Lake

### Datasets
Configure data source and sink definitions with appropriate schemas

### Pipelines
Set up trigger schedules and pipeline dependencies

---

## 🧪 Testing

```bash
# Validate pipeline definitions
az datafactory pipeline validate --factory-name caresync-adf --name main_pipeline

# Monitor pipeline runs
az datafactory pipeline-run query-by-factory --resource-group caresync-rg
```

---

## 🐛 Troubleshooting

| Issue | Solution |
|-------|----------|
| Connection failed | Verify connection strings and NSG rules |
| Column not found | Update dataset definitions and schemas |
| Performance issues | Optimize data volumes and transformations |
| Data loss | Check replication and backup settings |

---

## 🔐 Best Practices

✅ **Do:**
- Use managed identities for authentication
- Implement error handling in pipelines
- Version control all definitions
- Monitor costs and optimize resources
- Document data lineage

❌ **Don't:**
- Store credentials in code
- Skip data quality checks
- Use full refreshes when incremental works
- Ignore transformation errors

---

## 🤝 Contributing

1. Create feature branch
2. Update pipeline definitions
3. Add documentation
4. Submit PR with details

---

## 📚 Resources

- [Azure Data Factory Docs](https://docs.microsoft.com/en-us/azure/data-factory/)
- [Data Lake Storage Guide](https://docs.microsoft.com/en-us/azure/storage/blobs/data-lake-storage-best-practices)
- [Azure SQL Documentation](https://docs.microsoft.com/en-us/azure/azure-sql/database/)

---

**Last Updated:** 2026-09-27  
**Status:** Production Ready
