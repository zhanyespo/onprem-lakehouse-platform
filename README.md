# 🧱 Local Lakehouse Platform (Streaming · Analytics · ML)

A **production-style, open-source data platform** running fully **locally** using  
**WSL2 + Docker + VS Code**, designed to mirror modern cloud architectures while remaining
portable, reproducible, and vendor-neutral.

This repository implements an **end-to-end lakehouse** with streaming ingestion, object storage,
distributed compute, analytics warehouse, orchestration, ML lifecycle, and BI — all running on a single machine.

---

## 🧠 Architecture Overview

```

Sources
↓
[ Ingestion ]
MQTT / Kafka / NiFi
↓
[ Storage ]
MinIO (Parquet / Delta / Iceberg)
↓
[ Compute ]
Spark / Flink / dbt
↓
[ Warehouse ]
ClickHouse + Trino
↓
[ BI / ML ]
Superset / Metabase / MLflow

````

Orchestration: **Airflow**  
Infrastructure: **Docker → Kubernetes (future)**

---

## 🎯 Goals

- Reproduce **cloud-native data architecture locally**
- Support **batch + streaming workloads**
- Separate **infrastructure, compute, and data logic**
- Enable **analytics, ML, and BI** from the same data foundation
- Remain **vendor-agnostic** and fully open-source

---

## 📁 Repository Structure

```text
lakehouse-platform/
├── infra/                 # Infrastructure definitions (Docker / K8s)
├── ingestion/             # Kafka, MQTT, NiFi pipelines
├── storage/               # Bronze / Silver / Gold lake layers
├── compute/               # Spark, Flink, dbt jobs
├── warehouse/             # ClickHouse & Trino SQL
├── orchestration/         # Airflow DAGs
├── ml/                    # ML training, experiments, inference
├── bi/                    # Superset & Metabase configs
├── data/                  # Sample / test datasets
├── docker-compose.yml
├── .env.example
└── README.md
````

---

## 🧱 Stack Components

### Ingestion

* **Kafka** — streaming event ingestion
* **MQTT** — lightweight IoT / edge events
* **NiFi** — optional visual flow orchestration

### Storage

* **MinIO** — S3-compatible object storage
* **Parquet** — columnar storage
* **Delta / Iceberg** — table formats (Silver / Gold)

### Compute

* **Spark** — batch ETL & transformations
* **Flink** — real-time stream processing
* **dbt** — analytics transformations

### Warehouse

* **ClickHouse** — high-performance OLAP
* **Trino** — federated SQL across sources

### Orchestration

* **Airflow** — scheduling, dependency management

### Machine Learning

* **MLflow** — experiment tracking & model registry
* **Python** — training & inference pipelines

### BI

* **Apache Superset**
* **Metabase**

### Infrastructure

* **Docker Compose** (local)
* **Kubernetes** (planned)

---

## 🗂️ Data Lake Layout

```text
s3://lake/
├── bronze/      # raw ingested data
├── silver/      # cleaned / normalized
└── gold/        # analytics-ready datasets
```

---

## 🚀 Getting Started

### Prerequisites

* Windows 10/11
* WSL2 (Ubuntu recommended)
* Docker Desktop
* VS Code + Remote WSL extension

---

### 1️⃣ Clone Repository

```bash
git clone https://github.com/your-org/lakehouse-platform.git
cd lakehouse-platform
```

---

### 2️⃣ Configure Environment

```bash
cp .env.example .env
```

Edit `.env` as needed (ports, credentials, resource limits).

---

### 3️⃣ Start Platform

```bash
docker compose up -d
```

Verify services:

| Service    | URL                                            |
| ---------- | ---------------------------------------------- |
| MinIO      | [http://localhost:9001](http://localhost:9001) |
| Airflow    | [http://localhost:8080](http://localhost:8080) |
| Superset   | [http://localhost:8088](http://localhost:8088) |
| Metabase   | [http://localhost:3000](http://localhost:3000) |
| MLflow     | [http://localhost:5000](http://localhost:5000) |
| ClickHouse | [http://localhost:8123](http://localhost:8123) |

---

## 🛠️ Development Workflow

* **All code mounted as volumes** — no image rebuilds during development
* **SQL lives with the warehouse**
* **Business logic lives in compute**
* **Airflow DAGs only orchestrate**

Recommended VS Code extensions:

* Docker
* Python
* SQLTools
* dbt Power User

---

## 🧪 Example Pipelines

* Kafka → MinIO (Bronze)
* Spark → Silver transforms
* ClickHouse materialized views
* dbt → Gold semantic layer
* Airflow DAG orchestration
* MLflow experiment tracking
* Superset dashboards

---

## 📈 Roadmap

* [ ] Iceberg tables with Trino
* [ ] Flink real-time metrics
* [ ] Kubernetes deployment
* [ ] CI/CD for data pipelines
* [ ] Data quality checks
* [ ] Feature store patterns

---

## 🧩 Design Principles

* Infrastructure as code
* Idempotent pipelines
* Clear layer separation
* Cloud-portable design
* Analytics & ML from same source of truth

---

## 📜 License

MIT License — free to use, modify, and extend.

---

## 🙌 Why This Project Exists

This platform is built to **learn, test, and demonstrate modern data engineering architecture**
without relying on managed cloud services — while remaining production-realistic.

It is suitable for:

* learning
* experimentation
* portfolio projects
* architectural prototyping