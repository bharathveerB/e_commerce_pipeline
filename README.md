# 🛒 E-Commerce Order Pipeline

A modern data engineering project that simulates a **real-world e-commerce data pipeline**  from raw data creation to analytics-ready insights.  
This project integrates **Python**, **Snowflake**, **dbt**, and **Apache Airflow** to demonstrate how data engineers design, orchestrate, and monitor end-to-end ETL workflows.

---

## 🧠 Project Overview

The E-Commerce Order Pipeline automates the journey of order data from **source to insights**:

1. **Python scripts** generate dummy CSV files for orders, customers, and shipments.  
2. **Snowflake** ingests the CSVs into a **RAW schema**.  
3. **dbt** transforms raw tables into curated models in an **ANALYTICS schema**.  
4. **Apache Airflow** orchestrates the process, scheduling dbt runs and sending email alerts if orders remain unshipped for more than 48 hours.



---

## ⚙️ Detailed Workflow Explanation

### 🐍 1. Dummy Data Creation (Python)
- Python scripts generate three CSV datasets:
  - **customers.csv** → customer profile data (IDs, names, regions)
  - **orders.csv** → transactional order data (order ID, customer ID, total, date)
  - **shipments.csv** → shipping details (order ID, shipment date, delivery status)

---

### ❄️ 2. Data Loading into Snowflake (RAW Schema)
- The CSV files are **uploaded to Snowflake’s RAW schema**.
- Tables created:
  - `raw.orders`
  - `raw.customers`
  - `raw.shipments`


---

### 🔄 3. Transformation using dbt (ANALYTICS Schema)
- **dbt (Data Build Tool)** is used to clean, transform, and model the raw data.  
- Models created in the `ANALYTICS` schema
- Transformations include:
  - Joining customers, orders, and shipments
  - Calculating order delivery times and fulfillment rates
  - Creating a view to track order status and delays


---

### 🪄 4. Workflow Orchestration using Apache Airflow
- **Apache Airflow** manages the scheduling and automation:
  - Runs the dbt transformation job **hourly**
  - Monitors data freshness
  - Sends **email alerts** if any shipment remains pending for more than **48 hours**
- Airflow DAG ensures reliability and proactive monitoring of the pipeline.



---

## 🏗️ Data Flow Summary

| Step | Component | Purpose |
|------|------------|----------|
| 1 | **Python** | Generate dummy order, customer, and shipment data |
| 2 | **Snowflake (RAW Schema)** | Store raw CSV data in staging tables |
| 3 | **dbt (Transformation)** | Clean and model data into analytics-ready tables |
| 4 | **Snowflake (ANALYTICS Schema)** | Host curated and aggregated models |
| 5 | **Apache Airflow** | Automate dbt runs and trigger alerts |

---

## 📊 Example Business Use Case

This pipeline provides:
- **Operational dashboards** — Track orders, shipments, and customers  
- **Fulfillment KPIs** — Identify late shipments (> 48 hrs delay)  
- **Customer insights** — Analyze purchase frequency and delivery success rates  

By automating this pipeline, an e-commerce analytics team can ensure **data freshness, accuracy, and reliability**.

---

## 🧰 Tech Stack

| Tool | Purpose |
|------|----------|
| **Python** | Generate dummy datasets (CSV) |
| **Snowflake** | Cloud data warehouse for storage |
| **dbt** | Data transformation and modeling |
| **Apache Airflow** | Pipeline orchestration and automation |
| **Email** | Automated email alerts for delayed shipments |


