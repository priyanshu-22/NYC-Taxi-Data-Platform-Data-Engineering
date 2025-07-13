# NYC-Taxi-Data-Platform-Data-Engineering

# 🚖 NYC Taxi Data Platform – Data Engineering Assessment

This project is my submission for a Data Engineer technical assessment. I built a batch data processing pipeline using PySpark and Databricks to analyze New York City TLC taxi trip data (Yellow and Green). The project includes dimensional modeling, data quality checks, performance optimization, and analytical queries.

---

## 📦 Project Overview

- 🔹 Processed 3 months of Yellow & Green NYC taxi trip data  
- 🔹 Built a **Star Schema** model to support analytics
- 🔹 Implemented **batch processing** using PySpark on Databricks
- 🔹 Created **aggregation tables** and **analysis queries** (revenue, zones, long trips)
- 🔹 Designed an architecture that supports partitioning, optimization, and late-arriving data

---

## 🧱 Project Components

### 🗂️ Data Architecture
- Batch ingestion of historical trip data
- Stored curated data in Azure Data Lake
- Data warehouse modeled using **Star Schema**
- Serving layer optimized for BI/analytics
- Simulated real-time ingestion (optional/future scope)

📷 [View Architecture Diagram](docs/architecture_diagram.png)

---

### 🧮 Data Modeling
- ✅ **Fact Table**: `fact_trips`
- ✅ **Dimensions**: `dim_zones`, `dim_rate_codes`, `dim_payment_types`
- ✅ **SCD Handling**:
  - Zones & Payment Types as **SCD Type 2**
  - Rate Codes as **SCD Type 1**
- ✅ **Aggregations**:
  - `agg_revenue_by_time`
  - `agg_trip_patterns`
  - `agg_long_trips`

📄 [View Dimensional Model Documentation](docs/dimensional_model.md)

---

### ⚙️ Batch ETL Logic

Implemented in [combined_taxi.ipynb](notebooks/combined_taxi.ipynb):
- Trip duration & speed calculation
- Outlier detection (fare, duration)
- Zone name joins
- Hourly/daily/monthly aggregations
- Data validation & staging logic
- Partitioning by pickup datetime and location

---

### 📈 Analysis Queries (2024)

1. **Top 10 pickup zones by revenue**  
   [`queries/top_10_pickups.sql`](queries/top_10_pickups.sql)

2. **Trip pattern by weekday vs weekend**  
   [`queries/weekday_weekend_patterns.sql`](queries/weekday_weekend_patterns.sql)

3. **Top 10 long trips (>10 miles)**  
   [`queries/top_10_long_trips.sql`](queries/top_10_long_trips.sql)

---

## 📊 Optimization Techniques

- Broadcast joins for small lookup tables
- Filter & predicate pushdown
- Partitioning by month, zone
- Pre-aggregated summary tables for BI
- Indexing foreign keys in Delta Tables

---

## 📂 Folder Structure

nyc-taxi-data-platform/
├── notebooks/
├── docs/
├── queries/
├── README.md
├── requirements.txt


---

## ✅ Tools & Technologies

- **PySpark**, **Spark SQL**
- **Databricks** (Spark on Azure)
- **Azure Data Lake**
- **Delta Lake** (optional)
- **Star Schema & SCD modeling**

---

## 🚀 How to Run

1. Upload the notebook to a Databricks workspace
2. Attach a cluster with Spark 3.x and Python
3. Add 3 months of NYC Yellow & Green CSVs
4. Run cells to generate cleaned fact/dimension/aggregate tables
5. Use `submission.csv` or views for queries

---

## 📎 Additional Files

- 📝 `docs/dimensional_model.md`: Data model design
- 📌 `notebooks/combined_taxi.ipynb`: Full pipeline logic
- 📈 SQL queries for 2024 analysis

---

## 📄 License

This project is under the MIT License — feel free to use for learning or interview prep.
