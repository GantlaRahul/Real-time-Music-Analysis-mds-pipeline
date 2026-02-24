📌 Project Overview

This project demonstrates an end-to-end real-time data engineering pipeline for Spotify-style music analytics using a Modern Data Stack architecture.

We simulate live Spotify streaming data — including song plays, listeners, regions, and device types — and build a fully automated pipeline from ingestion to visualization.

Once the pipeline is started, the entire workflow runs automatically:

Data Simulation → Kafka Streaming → MinIO Storage → Snowflake (Bronze) → DBT Transformations (Silver & Gold) → Power BI Dashboard

This project mirrors a real-world production-grade Spotify analytics system built using industry-standard cloud data tools.

🏗️ Architecture
🔄 Pipeline Flow

Data Simulator (Python + Faker)
Generates fake Spotify streaming events:

user_id

track_name

artist

region

device_type

timestamp

duration

Kafka Producer
Streams real-time events into Kafka topics.

Kafka Consumer
Consumes streaming events and stores raw JSON data into MinIO (S3-compatible storage).

Apache Airflow

DAG 1 → Loads raw data from MinIO into Snowflake Bronze layer

DAG 2 → Triggers DBT transformations

Snowflake Data Warehouse

Bronze Layer → Raw ingested data

Silver Layer → Cleaned and standardized data

Gold Layer → Aggregated, analytics-ready models

DBT

Builds staging, fact, and dimension models

Implements testing and documentation

Runs transformations inside Snowflake

Power BI

Connects directly to Snowflake Gold tables

Builds interactive dashboards

⚡ Tech Stack
Layer	Tools Used
Simulation	Python, Faker
Streaming	Apache Kafka
Storage	MinIO (S3-compatible)
Warehouse	Snowflake
Transformation	DBT
Orchestration	Apache Airflow
Visualization	Power BI
Deployment	Docker, docker-compose
🏛️ Data Architecture – Medallion Model

Implemented inside Snowflake:

🥉 Bronze

Raw JSON data loaded from MinIO.

🥈 Silver

Cleaned columns

Standardized timestamps

Removed duplicates

Data validation

🥇 Gold

Analytics-ready models:

🎵 Top Artists by Plays

🌎 Most-Streamed Regions

📈 Listening Trends Over Time

💽 Device Usage Distribution

📂 Repository Structure
spotify-mds-pipeline/
│
├── docker/
│   ├── .env
│   ├── docker-compose.yml
│   └── dags/
│       ├── minio-to-kafka.py
│
├── spotify_dbt/
│   └── models/
│       ├── gold/
│       ├── silver/
│       └── sources.yml
│
├── simulator/
│   ├── producer.py
│   └── .env
│
├── consumer/
│   ├── kafka-to-minio.py
│   └── .env
│
├── docker-compose.yml
├── requirements.txt
└── README.md
⚙️ Step-by-Step Implementation
1️⃣ Data Simulation

Generated synthetic Spotify streaming events using Python + Faker

Continuous stream of realistic song-play data

2️⃣ Kafka Streaming

Producer pushes events to Kafka topics

Consumer stores events in MinIO as raw JSON

3️⃣ Airflow Orchestration

Automates ingestion to Snowflake Bronze

Triggers DBT runs for Silver and Gold transformations

4️⃣ DBT Transformations

Staging Models

Clean column names

Handle null values

Standardize timestamps

Marts

Facts → plays, listeners

Dimensions → tracks, artists, devices, regions

Automated testing:

dbt test
dbt docs generate
📊 Power BI Dashboard

Connected directly to Snowflake Gold layer.

Interactive visualizations include:

🎵 Top Artists / Songs by Plays

🌎 Regional Heatmap

📈 Streaming Trends Over Time

💽 Device-Type Distribution

✅ Key Features

✔ Fully automated real-time pipeline
✔ Kafka-based streaming architecture
✔ Snowflake Medallion architecture (Bronze → Silver → Gold)
✔ Modular SQL modeling using DBT
✔ Automated DAG orchestration via Airflow
✔ Containerized deployment with Docker
✔ CI/CD integration with DBT test automation
✔ Production-style data engineering design

🧠 Concepts Demonstrated

Real-time data ingestion

Event-driven architecture

Medallion data modeling

Cloud data warehousing

Data transformation engineering

Workflow orchestration

Business intelligence visualization

End-to-end Modern Data Stack implementation

🚀 How to Run

Clone the repository

Configure .env variables

Run:

docker-compose up --build

Trigger Airflow DAGs

Open Power BI and connect to Snowflake Gold layer

👨‍💻 Author

Rahul
M.Sc. Data Analytics Student
Berlin, Germany
