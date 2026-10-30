# 🚀 Real-Time Traffic Analytics Using Azure
### DEPI Data Engineering Track | End-to-End Data Pipeline

![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python)
![Apache Kafka](https://img.shields.io/badge/Apache_Kafka-Streaming-black?logo=apache-kafka)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Database-blue?logo=postgresql)
![dbt](https://img.shields.io/badge/dbt_Core-Transformation-orange?logo=dbt)
![Docker](https://img.shields.io/badge/Docker-Containerization-blue?logo=docker)
![Power BI](https://img.shields.io/badge/Power_BI-Visualization-yellow?logo=power-bi)

---

## 📌 Executive Summary
**Real-Time Traffic Analytics** is a robust, containerized data engineering pipeline designed to ingest, stream, transform, and visualize live traffic data from the **Digitraffic Finland API**. By integrating event-driven architecture with rigorous data quality frameworks, this project provides a unified, near-real-time analytical view of traffic conditions, road maintenance, and weather impacts.

---

## 🏗️ System Architecture
The pipeline follows a decoupled, event-driven Medallion Architecture (Raw ➔ Staging ➔ Gold):


graph TD
    A[🌐 Digitraffic API\nJSON / XML] -->|1. Python Producers| B((📨 Apache Kafka))
    B -->|2. Python Consumers| C[(🗄️ PostgreSQL\nRaw Layer)]
    C -->|3. dbt Core Transformations| D[(⚙️ PostgreSQL\nStaging Layer)]
    D -->|4. dbt Core Modeling| E[(🏆 PostgreSQL\nGold Layer)]
    E -->|5. Direct Query / Import| F[📊 Power BI\nDashboard]

    %% Styling for professional look
    classDef api fill:#e1f5fe,stroke:#01579b,stroke-width:2px;
    classDef kafka fill:#fff3e0,stroke:#e65100,stroke-width:2px;
    classDef db fill:#e8f5e9,stroke:#1b5e20,stroke-width:2px;
    classDef bi fill:#fff8e1,stroke:#f57f17,stroke-width:2px;

    class A api;
    class B kafka;
    class C,D,E db;
    class F bi;

---

## 🛠️ Technology Stack

| Category | Technologies Used |
| :--- | :--- |
| **Data Ingestion** | Python, Requests, XML/JSON Parsing |
| **Event Streaming** | Apache Kafka |
| **Data Storage** | PostgreSQL |
| **Transformation & QA** | dbt Core (SQL, Data Quality Tests) |
| **Visualization** | Power BI Desktop |
| **DevOps & Cloud** | Docker, Docker Compose, Azure Virtual Machine |

---

## 📂 Project Documentation (DEPI Guidelines)
All project documentation is strictly organized according to the **7 DEPI Project Phases**. 

### 📅 Phase 1: Project Planning
- [Master Project Plan & Execution Strategy](docs/01_Project_Planning/Master_Project_Plan.pdf)

### ✅ Phase 2: Lecturer Review
- [Initial Proposal & Sign-off Document](docs/02_Lecturer_Review/Initial_Proposal_Signoff.pdf)

### 📋 Phase 3: Requirements Gathering
- [Requirements Gathering & Analysis Document](docs/03_Requirements/Requirements_Gathering_Document.pdf)

### 🏗️ Phase 4: System Analysis & Design
- [System Architecture Diagram](docs/04_Analysis_Design/System_Architecture_Diagram.png)
- [Database Schema & Data Model](docs/04_Analysis_Design/Database_Schema.pdf)
- 📚 **[Literature Review: State of the Art & Research Gap](docs/04_Analysis_Design/Literature_Review.pdf)** *(Independent Academic Review)*

### 🛠️ Phase 5: Implementation
- [Project Infographic & Visual Roadmap](docs/05_Implementation/Infographic_Slide.png)

### 🧪 Phase 6: Testing & Quality Assurance
- [Risk Assessment & Mitigation Plan](docs/06_Testing_QA/Risk_Assessment_Plan.pdf)
- [KPIs & Testing Strategy](docs/06_Testing_QA/KPIs_and_Testing_Strategy.pdf)

### 🏆 Phase 7: Final Phase
- [Final Project Report](docs/07_Final_Phase/Final_Project_Report.pdf)
- [Final Presentation Deck](docs/07_Final_Phase/Final_Presentation.pptx)

---

## 📁 Repository Structure

- 📄 **`docs/`** : All DEPI Documentation (Phases 1-7)
  - `01_Project_Planning/`
  - `02_Lecturer_Review/`
  - `03_Requirements/`
  - `04_Analysis_Design/` *(Includes Literature Review)*
  - `05_Implementation/`
  - `06_Testing_QA/`
  - `07_Final_Phase/`
- 🐍 **`src/`** : Python Source Code (Producers, Consumers, Utils)
- 🔄 **`dbt_project/`** : dbt Core Models, Tests, and Configurations
- 🐳 **`docker/`** : Dockerfiles and `docker-compose.yml`
- 📊 **`powerbi/`** : Power BI `.pbix` files and dataset configs
- 🚫 **`.gitignore`** : Ignored files (`.env`, `__pycache__`, etc.)
- 📖 **`README.md`** : You are here!

---

## 🚀 How to Run Locally

1. Clone the repository:
   git clone https://github.com/nhahub/NHA-5-051.git
   cd real-time-traffic-analytics

2. Configure Environment Variables:
   Create a .env file in the docker/ directory based on the .env.example template.

3. Start the Infrastructure (Kafka, PostgreSQL, Zookeeper):
   cd docker
   docker-compose up -d

4. Run the Python Ingestion Services:
   cd ../src
   python producers/main.py
   python consumers/main.py

5. Execute dbt Transformations:
   cd ../dbt_project
   dbt deps
   dbt run
   dbt test

6. Connect Power BI:
   Open the .pbix file in the powerbi/ folder and connect to your local PostgreSQL instance.

---

## 👥 Project Team

| Name | Role | Core Responsibility |
| :--- | :--- | :--- |
| **Amr Mahmoud** | Team Lead & Data Architect | Architecture, Integration, Technical Review |
| **Mohamed Ibrahim** | Python Data Ingestion Engineer | API Extraction, Producers, Kafka Publishing |
| **Mohsen Khalaf** | Data Quality & Testing Engineer | Validation, Test Execution, Defect Reporting |
| **Mohamed Saleh** | Database & Transformation Engineer | PostgreSQL Modeling, dbt Core, Data Structures |
| **Basant Magdy** | Power BI Developer | Dashboard Design, Visualization, Report Validation |
| **Kerolos Adly** | DevOps & Deployment Engineer | Docker Configuration, Azure VM Deployment |

---

## 📄 License
This project is developed as part of the **Digital Egypt Pioneers Initiative (DEPI)**. 
© 2026 Real-Time Traffic Analytics Team. All rights reserved.