# 🎧 Spotify Modern Data Stack Project  
**Snowflake • DBT • Apache Airflow • Apache Kafka • Python • Docker • Power BI**

---

## 📌 Project Overview

This project demonstrates an end-to-end **real-time data engineering pipeline** for Spotify-style music analytics using a Modern Data Stack architecture.

The system simulates live Spotify streaming data — including song plays, listeners, regions, and device types — and builds a fully automated pipeline from ingestion to visualization.

Once started, the pipeline runs automatically:

Data Simulation → Kafka Streaming → MinIO Storage → Snowflake (Bronze) → DBT Transformations (Silver & Gold) → Power BI Dashboard

This project mirrors a production-grade Spotify analytics system built using modern cloud data tools.

---

## 🏗️ Architecture

### 🔄 Pipeline Flow

1. **Data Simulator (Python + Faker)**  
   Generates fake Spotify streaming events:
   - user_id  
   - track_name  
   - artist  
   - region  
   - device_type  
   - timestamp  
   - duration  

2. **Kafka Producer**  
   Streams real-time events into Kafka topics.

3. **Kafka Consumer**  
   Consumes streaming events and stores raw JSON data into MinIO (S3-compatible object storage).

4. **Apache Airflow**  
   - DAG 1 → Loads raw data from MinIO into Snowflake Bronze layer  
   - DAG 2 → Triggers DBT transformation runs  

5. **Snowflake Data Warehouse**
   - Bronze Layer → Raw ingested data  
   - Silver Layer → Cleaned and standardized data  
   - Gold Layer → Aggregated, analytics-ready models  

6. **DBT**
   - Builds staging, fact, and dimension models  
   - Implements data tests  
   - Runs transformations directly inside Snowflake  

7. **Power BI**
   - Connects to Snowflake Gold tables  
   - Builds interactive dashboards  

---

## ⚡ Tech Stack

| Layer | Tools Used |
|-------|------------|
| Data Simulation | Python, Faker |
| Streaming | Apache Kafka |
| Storage | MinIO (S3-compatible) |
| Data Warehouse | Snowflake |
| Transformation | DBT |
| Orchestration | Apache Airflow |
| Visualization | Power BI |
| Deployment | Docker, docker-compose |

---

## 🏛️ Data Architecture – Medallion Model

Implemented inside Snowflake:

### 🥉 Bronze
Raw JSON data loaded from MinIO.

### 🥈 Silver
- Cleaned column names  
- Standardized timestamps  
- Removed duplicates  
- Data validation  

### 🥇 Gold
Analytics-ready models:
- Top Artists by Plays  
- Most-Streamed Regions  
- Listening Trends Over Time  
- Device Usage Distribution  

---

## 📂 Repository Structure

---

## ⚙️ Implementation Steps

### 1️⃣ Data Simulation
- Generated synthetic Spotify streaming events using Python + Faker  
- Continuous stream of realistic song-play data  

### 2️⃣ Kafka Streaming
- Producer pushes events to Kafka topics  
- Consumer stores events in MinIO as raw JSON  

### 3️⃣ Airflow Orchestration
- Automates ingestion to Snowflake Bronze  
- Triggers DBT runs for Silver and Gold transformations  

### 4️⃣ DBT Transformations
**Staging Models**
- Clean column names  
- Handle null values  
- Standardize timestamps  

**Marts**
- Facts → plays, listeners  
- Dimensions → tracks, artists, devices, regions  

Run tests and documentation:

---

## 📊 Power BI Dashboard

Connected directly to Snowflake Gold layer.

Dashboard includes:

- Top Artists / Songs by Plays  
- Regional Heatmap  
- Streaming Trends Over Time  
- Device-Type Distribution  

---

## ✅ Key Features

✔ Fully automated real-time pipeline  
✔ Kafka-based streaming architecture  
✔ Snowflake Medallion architecture (Bronze → Silver → Gold)  
✔ Modular SQL modeling using DBT  
✔ Automated orchestration via Airflow  
✔ Containerized deployment with Docker  
✔ CI/CD integration with DBT test automation  

---

## 🚀 How to Run

1. Clone the repository  
2. Configure environment variables in `.env`  
3. Run:

4. Trigger Airflow DAGs  
5. Connect Power BI to Snowflake Gold layer  

---

## 🧠 Concepts Demonstrated

- Real-time data ingestion  
- Event-driven architecture  
- Medallion data modeling  
- Cloud data warehousing  
- Workflow orchestration  
- Business intelligence visualization  
- End-to-end Modern Data Stack implementation  

---

## 👨‍💻 Author

Rahul  
M.Sc. Data Analytics Student  
Berlin, Germany  
