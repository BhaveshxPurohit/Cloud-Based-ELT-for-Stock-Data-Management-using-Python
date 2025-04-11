# 📈 Automated Financial Data Pipeline with Azure & Power BI

## 🧠 Overview

This project implements an automated, cloud-based ELT (Extract, Load, Transform) pipeline to process and visualize historical financial data for major companies using Microsoft Azure services. It streamlines stock market monitoring and financial analysis over a ten-year period, automating data extraction, transformation, storage, and reporting using tools like Azure Functions, Alteryx, Synapse Analytics, Logic Apps, and Power BI.

---

## 🚀 Key Features

- ⏱ **Daily Automated Stock Data Updates** using Azure Functions & yfinance
- 🧹 **Financial Data Cleaning and Structuring** with Alteryx
- 📦 **Cloud Storage** on Azure Blob (Data Lake architecture)
- 📊 **SQL-Based Transformations** using Azure Synapse Analytics
- 🔁 **Workflow Orchestration** with Azure Logic Apps
- 📉 **Interactive Dashboards** in Power BI for trend analysis

---

## 🧰 Tech Stack

- **Azure Blob Storage** – Centralized storage for all raw and processed data
- **Azure Functions** – Scheduled stock data retrieval and upload (via yfinance)
- **Alteryx** – Preprocessing of financial statements (Income & Balance Sheets)
- **Azure Logic Apps** – Daily automation triggers and success/failure alerts
- **Azure Synapse Analytics** – Data warehouse, SQL Pools, merging logic
- **Power BI** – Final reporting and financial trend visualization

---

## 🔄 Workflow Overview

### 🔹 Azure Function

- Pulls daily stock data via `yfinance`
- Saves as CSV to Azure Blob Storage
- Deletes older data files (with prefix `function_`) to keep storage clean

### 🔹 Alteryx Workflows

- Cleans and restructures **annual** and **quarterly** income statements and balance sheets
- Adds company name tags, reformats dates, and filters post-2014 data
- Uploads clean files to Azure Blob Storage

### 🔹 Azure Logic App

- Runs Mon–Fri to mimic trading days
- Triggers Azure Functions to update data
- Compares file modified timestamps
- Sends **success or failure email notifications** to stakeholders

### 🔹 Azure Synapse Pipelines

- Loads CSVs from Blob to SQL tables
- Executes stored procedures to clear & merge data (e.g., income + balance sheets)
- Dynamically manages SQL pool (auto start/stop) for cost optimization

### 🔹 Power BI Dashboard

- Connects directly to Synapse SQL tables
- Visualizes:
  - Stock trends
  - Financial health (Revenue, Net Income, Assets, Liabilities)
  - Year-over-year company comparisons

---

## 📈 Companies Analyzed

- **Apple**
- **Microsoft**
- **Amazon**
- **Meta (Facebook)**

> All data sourced from Yahoo Finance & Yahoo Finance Plus.

---

## ✅ Outcomes

- End-to-end **automated pipeline** with near real-time updates
- Reduced manual ETL work with **reusable and modular workflows**
- Strategic cloud cost savings via dynamic SQL pool management
- Reliable and **scalable financial dashboarding** for decision support

---

## 💡 Future Enhancements

- Integrate **error logging** and retries in Logic Apps
- Expand support to **more companies or sectors**
- Introduce **forecasting** via Azure ML or Python models
- Build a **user-facing portal** for dashboard access and data exploration


