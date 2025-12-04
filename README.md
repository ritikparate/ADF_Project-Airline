# **ADF_Project-Airline**

## This is a small-scale project built in Azure Data Factory to handle data in the kilobyte range, focused on exploring and understanding the Medallion (Bronze–Silver–Gold) architecture concept through hands-on implementation.

# 📊 Data Pipeline Documentation

## 1. Pipeline Overview

**Description:**  
The pipeline is designed to ingest, transform, and organize data from multiple sources into a structured format for analytics and reporting. It ensures data quality and readiness by processing data through multiple layers: Bronze, Silver, and Gold.  

**High-Level Architecture:** 
<div><img width="1280" height="561" alt="image" src="https://github.com/user-attachments/assets/9d04d9c7-cc61-4ac6-b06f-464338ac280f" /></div>

**Pipeline Layers and Purpose:**  
- **Bronze Layer:** Raw data ingestion from multiple sources; minimal transformation applied.  
- **Silver Layer:** Data cleansing, standardization, and enrichment for analytical readiness.  
- **Gold Layer:** Aggregated, curated, and analytics-ready datasets for reporting and BI consumption.  

## 2. Data Sources

| Source Type        | Source Name / Description       | Data Type       |
|-------------------|-------------------------------|----------------|
| API               | External REST APIs             | Structured     |
| SQL Database      | Azure SQL Database             | Structured     |
| On-Prem Database  | Local SQL Server               | Structured     |
| CSV / Flat Files  | Internal data dumps            | Structured / Semi-structured |

**Notes:**  
- The pipeline supports both structured and semi-structured data.  
- Data is ingested incrementally wherever possible to optimize runtime and storage.  


## 3. Pipeline Execution Runtime:
The Integration Runtime was configured and deployed on my local system through Azure Data Factory. This screenshot highlights the active Self-Hosted Integration Runtime, enabling secure and reliable data transfer between on-premise sources and Azure Data Factory.
<div align = "center">
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/df80928e-726e-4904-86b0-fbe2ff82555b" />
</div>

## 4. Ingestion Pipelines
This project demonstrates a complete data ingestion solution built using Azure Data Factory. It covers API-based data ingestion, incremental loading from SQL to Data Lake using watermark validation, and automated on-premise file migration through dynamic ForEach activities. The pipelines are designed for scalability, reliability, and end-to-end automation. Below are snapshots from ADF.
<div align="center">
<img width="300" height="300" alt="image" src="https://github.com/user-attachments/assets/799a554d-f334-47f3-af52-43037ceb499c" />
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/c5e83edc-a04d-4d03-a67f-0897a70da49b" />
<img width="600" height="550" alt="image" src="https://github.com/user-attachments/assets/44732478-4b74-4f60-b57c-4a446a2d835e" />
</div>
A master orchestration pipeline was designed in Azure Data Factory to trigger and manage multiple ingestion pipelines, including on-premise, API, and incremental SQL-to-Data Lake loads. Integrated with Azure Logic Apps via web activity to enable automated failure notifications and operational monitoring.

🖼 Screenshot:
<div align='center'>
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/0408f6ab-4b9e-45c5-a64e-fd74fa3c544e" />
</div>

## 5. Silver Layer Transformation in Data Flow
Silver layer transformations were implemented using Azure Data Factory Mapping Data Flows to cleanse, standardize, and enrich raw Bronze data. This included column selection, filtering, data standardization (capitalization, formatting), business rule validations, and upsert logic to prepare high-quality, analysis-ready datasets for downstream consumption.

🖼 Screenshot:
<div align='center'>
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/3ab1d539-dd57-462e-a0f1-0ed26a4a4030" />
</div>

## 🚀 Pipeline Execution Summary

**Parent Pipeline:** `Parent_Pipeline_Name`  
**Status:** ✅ **Succeeded**

| 🔹 Step | ⏱ Start Time | ⏱ End Time | ⏳ Duration | ✅ Status |
|---------|--------------|------------|------------|-----------|
| Silver Layer Transformation | 10:19 AM | 10:22 AM | 3 min | ✅ Succeeded |

**💬 Message:**  
> Parent pipeline executed successfully, including the **Silver layer transformation**.  
> All ingestion pipelines completed, and the data is ready for further processing.

**🖼 Screenshot:**  
<div align='center'>
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/fef1c72b-412c-44fd-acd3-abfa67b6178e" />
</div>

A failure notification for any pipeline error is sent automatically to the configured email address.
Below is a screenshot of a failure notification received in my mailbox:
<div align='center'>
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/e25dda29-ed5f-4130-90e2-714cc1c00a64" />
<div align='center'>{img.} - This demonstrates the pipeline’s error-handling mechanism and ensures timely alerts for any issues during execution.</div>
</div>
