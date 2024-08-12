# Azure End to End Data Engineering Pipeline

## 🎯 **Project Overview**

- This project creates a complete Azure Data Engineering solution that handles data ingestion, ETL, and analytics in one pipeline using Microsoft Azure services and Power BI. 
- The main goal is to move an on-premises database, like Microsoft SQL Server Management System (SSMS), to the cloud. This is done by building an ETL pipeline using Azure Data Factory, Azure Databricks, and Azure Synapse Analytics.
- The solution also connects to Microsoft Power BI for easy data visualization and reporting through a dashboard.

## 📚 **Dataset**
### AdventureWorks Dataset
[Download here](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksLT2022.bak)

## ⚙ **Services Used**
- **Data Source**: SQL Server
- **Orchestration**: Azure Data Factory
- **Ingestion**: Azure Data Lake Gen2
- **Storage**: Azure Synapse Analytics
- **Security & Governance**: Azure Active Directory and Azure Key Vault
- **Data Visualization**: PowerBI

## 📐 **Project Architecture**
![image](https://github.com/RithicaM/Azure_Pipeline_Data_Engineering_Project/blob/main/Implemention%20images/SSMS.png)

## 📔 On Prem SQL Server
![image](https://github.com/RithicaM/Azure_Pipeline_Data_Engineering_Project/blob/main/Implemention%20images/SSMS.png)

## 📩 Data Ingestion
-Established a connection between the on-premises SQL Server and Azure using Microsoft Integration Runtime.
![image](https://github.com/RithicaM/Azure_Pipeline_Data_Engineering_Project/blob/main/Implemention%20images/SHIR.png)
-Set up a Resource Group with necessary services like Key Vault, Storage Account, Data Factory, Databricks, and Synapse Analytics.
![image](https://github.com/RithicaM/Azure_Pipeline_Data_Engineering_Project/blob/main/Implemention%20images/Resrc%20grp.png)
-Transferred tables from the on-premises SQL Server to Azure Data Lake Storage Gen2.
![image](https://github.com/RithicaM/Azure_Pipeline_Data_Engineering_Project/blob/main/Implemention%20images/Datalake.png)
![image](https://github.com/RithicaM/Azure_Pipeline_Data_Engineering_Project/blob/main/Implemention%20images/Data%20factory%20pipeline.png)

## 🛠 Data Transformation
- Mounted Azure Blob Storage in Databricks to access the raw data from the Data Lake.
- Used a Spark Cluster in Azure Databricks to transform the data following the Medallion Architecture, moving it from the Bronze stage to Silver and then to Gold.
- Saved the final, refined data in Delta format, optimized for further analysis.
![image](https://github.com/RithicaM/Azure_Pipeline_Data_Engineering_Project/blob/main/Implemention%20images/Mounting1.png)
![image](https://github.com/RithicaM/Azure_Pipeline_Data_Engineering_Project/blob/main/Implemention%20images/Mounting2.png)
![image](https://github.com/RithicaM/Azure_Pipeline_Data_Engineering_Project/blob/main/Implemention%20images/Mounting2.png)
![image](https://github.com/RithicaM/Azure_Pipeline_Data_Engineering_Project/blob/main/Implemention%20images/Bronze-silver%201.png)
![image](https://github.com/RithicaM/Azure_Pipeline_Data_Engineering_Project/blob/main/Implemention%20images/Bronze-silver%202.png)
![image](https://github.com/RithicaM/Azure_Pipeline_Data_Engineering_Project/blob/main/Implemention%20images/Silver-gold1.png)
![image](https://github.com/RithicaM/Azure_Pipeline_Data_Engineering_Project/blob/main/Implemention%20images/Silver-gold2.png)
![image](https://github.com/RithicaM/Azure_Pipeline_Data_Engineering_Project/blob/main/Implemention%20images/Silver-gold3.png)

## 📥 Data Loading
- Utilized Azure Synapse Analytics to efficiently load the refined "gold" level data.
- Created a SQL database connected to the data lake and ran an Azure Synapse Pipeline.
- The pipeline retrieves table names from the gold folder and executes a stored procedure for each table, which creates and updates views in the Azure SQL Database.
![image](https://github.com/RithicaM/Azure_Pipeline_Data_Engineering_Project/blob/main/Implemention%20images/synapse%20pipeline.png)
![image](https://github.com/RithicaM/Azure_Pipeline_Data_Engineering_Project/blob/main/Implemention%20images/stored%20procedure.png)
![image](https://github.com/RithicaM/Azure_Pipeline_Data_Engineering_Project/blob/main/Implemention%20images/serverless%20db.png)

## 📊 Data Reporting
- Loaded data from views into Microsoft Power BI using DirectQuery, allowing automatic updates from cloud pipelines.
- Connected Power BI to Azure Synapse and used database views to create interactive and insightful data visualizations.
![image](https://github.com/RithicaM/Azure_Pipeline_Data_Engineering_Project/blob/main/Implemention%20images/dashboard%20.png)





