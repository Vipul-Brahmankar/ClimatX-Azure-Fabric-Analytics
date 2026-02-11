# ClimatX | Scalable Analytics Architecture for Environmental Insights

![Azure](https://img.shields.io/badge/azure-%230072C6.svg?style=for-the-badge&logo=microsoftazure&logoColor=white)
![Microsoft Fabric](https://img.shields.io/badge/Microsoft%20Fabric-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
![Databricks](https://img.shields.io/badge/Databricks-FF3621?style=for-the-badge&logo=databricks&logoColor=white)
![Power Bi](https://img.shields.io/badge/power_bi-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)

## 📋 Project Overview
**ClimatX** is an end-to-end cloud analytics platform engineered to process, transform, and visualize large-scale environmental data. Built within the **Microsoft Fabric** ecosystem, this project demonstrates a modern "Lakehouse" architecture, integrating data engineering (Spark/Databricks), warehousing (Delta Lake), and business intelligence (Power BI).

The pipeline ingests raw historical weather data from public APIs, processes it through a **Medallion Architecture** (Bronze $\rightarrow$ Silver $\rightarrow$ Gold), and delivers interactive insights on climate trends, extreme weather events, and temperature volatility.

---

## 🏗️ Architecture & Data Flow

[Insert Architecture Diagram Here]

1.  **Ingestion (Bronze Layer):** * Automated extraction of historical weather data (London, NY, Tokyo) via the Open-Meteo API.
    * Raw JSON data is landed directly into **OneLake** as Delta Parquet files.
2.  **Transformation (Silver Layer):**
    * **PySpark** notebooks perform data cleaning, schema enforcement, and deduplication.
    * Imputation of missing sensor values and timestamp normalization.
3.  **Analytics (Gold Layer):**
    * Complex aggregations including **7-day rolling averages**, **Month-over-Month (MoM) variance**, and anomaly detection (e.g., freezing days).
    * Optimized Delta tables ready for Direct Lake access.
4.  **Visualization:**
    * **Power BI** dashboards connected via **Direct Lake** mode for zero-latency reporting.
    * DAX measures for dynamic time-series analysis.

---

## 📂 Repository Structure


ClimatX-Azure-Fabric-Analytics/
│
├── src/
│   ├── 01_ingestion/       # Extract logic: API -> Bronze Lakehouse
│   │   └── extract_weather_api.py
│   │
│   ├── 02_transformation/  # Silver logic: Cleaning & Deduplication
│   │   └── clean_silver_weather.py
│   │
│   └── 03_analytics/       # Gold logic: Aggregations & Rolling Averages
│       └── aggregate_gold_weather.py
│
├── notebooks/              # Jupyter/Fabric Notebook exports (.ipynb)
├── docs/                   # Architecture diagrams and screenshots
├── requirements.txt        # Python dependencies (requests, pandas, pyspark)
└── README.md               # Project documentation
