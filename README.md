# ClimatX | Scalable Analytics Architecture for Environmental Insights

![Azure](https://img.shields.io/badge/azure-%230072C6.svg?style=for-the-badge&logo=microsoftazure&logoColor=white)
![Microsoft Fabric](https://img.shields.io/badge/Microsoft%20Fabric-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
![Databricks](https://img.shields.io/badge/Databricks-FF3621?style=for-the-badge&logo=databricks&logoColor=white)
![Power Bi](https://img.shields.io/badge/power_bi-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)

## 📋 Project Overview
**ClimatX** is an end-to-end cloud analytics platform engineered to process, transform, and visualize large-scale environmental data. Built within the **Microsoft Fabric** ecosystem, this project demonstrates a modern "Lakehouse" architecture, integrating data engineering (Spark/Databricks), warehousing (Delta Lake), and business intelligence (Power BI).

The pipeline ingests raw historical weather data from public APIs, processes it through a **Medallion Architecture** (Bronze $\rightarrow$ Silver $\rightarrow$ Gold), and delivers interactive insights on climate trends, extreme weather events, and temperature volatility.


## 🏗️ Architecture & Data Flow
![Arch Placeholder](https://github.com/Vipul-Brahmankar/ClimatX-Azure-Fabric-Analytics/blob/801661282866af24ac9a6e40b9dc718b5a9a92f7/docs/ClimatX-architecture.png)

1.  **Ingestion (Bronze Layer):**
    * Automated extraction of historical weather data (London, NY, Tokyo) via the Open-Meteo API.
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

```text
ClimatX-Azure-Fabric-Analytics/
│
├── notebooks/              #Fabric Notebook exports (.ipynb)
│   ├── 01_ingestion/       # Extract logic: API -> Bronze Lakehouse
│   │   └── extract_weather_api.ipynb
│   │
│   ├── 02_transformation/  # Silver logic: Cleaning & Deduplication
│   │   └── clean_silver_weather.ipynb
│   │
│   └── 03_analytics/       # Gold logic: Aggregations & Rolling Averages
│       └── aggregate_gold_weather.ipynb
│
├── docs/                   # Architecture diagrams and screenshots
├── requirements.txt        # Python dependencies (requests, pandas, pyspark)
└── README.md               # Project documentation
```

---

## 🚀 Key Features
* **Scalable ELT Pipeline:** Designed workflows capable of handling multi-region weather data with automated error handling.
* **Delta Lake Optimization:** utilized `OPTIMIZE` and `Z-ORDER` indexing (implied in Silver layer partitioning) for fast query performance.
* **Advanced Analytics:** Implemented window functions in Spark to calculate sliding window metrics for trend analysis.
* **Full-Stack Data Engineering:** From API calls (Python) to Distributed Compute (Spark) to BI Modeling (DAX).

---

## 📊 Dashboard Preview
![Dashboard Placeholder](https://github.com/Vipul-Brahmankar/ClimatX-Azure-Fabric-Analytics/blob/4cd1ff06f2c8bc0554106333289875d6529e8dc0/docs/ClimatX-dashboard.png)


**Key Metrics Tracked:**
* Average Monthly Temperature vs. 5-Year Baseline
* Frequency of Extreme Weather Events (Freezing/Heatwave)
* Precipitation Trends by City

---

## 🛠️ Setup & Usage

### Prerequisites
* Microsoft Fabric Workspace (or Azure Databricks Workspace + ADLS Gen2)
* Python 3.10+

### Running the Pipeline
1.  **Clone the Repo:**
    ```bash
    git clone [https://github.com/yourusername/ClimatX-Azure-Fabric-Analytics.git](https://github.com/yourusername/ClimatX-Azure-Fabric-Analytics.git)
    ```
2.  **Import Notebooks:** Upload the files from `src/` or `notebooks/` into your Fabric Workspace.
3.  **Run Ingestion:** Execute `01_ingestion/extract_weather_api.py` to populate the Bronze layer.
4.  **Run Transformation:** Execute `02_transformation/clean_silver_weather.py` to clean data.
5.  **Run Analytics:** Execute `03_analytics/aggregate_gold_weather.py` to generate report-ready tables.

---

## 📬 Contact
**[Vipul Brahmankar]** [vipul.brahmankar@gmail.com]  
