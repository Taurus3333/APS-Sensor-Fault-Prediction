# Sensor Fault Detection in APS using production grade MlOps pipelines


![Scania Truck](Scania.jpg)


## 🧠 Problem Statement

The **Air Pressure System (APS)** is a critical subsystem in heavy-duty Scania trucks. It uses compressed air to apply pressure to brake pads, offering sustainability and reliability over traditional hydraulic systems.

This is a **binary classification** task:
- **Class 1** → Fault caused by APS component
- **Class 0** → Fault caused by non-APS component

🔍 **Business Objective**  
Minimize **false negatives** as they result in **50x higher repair costs** than false positives. Reducing unnecessary repairs while ensuring actual APS faults are detected is critical.


## Tech Stack Used
<img height="50" src="https://user-images.githubusercontent.com/25181517/192108891-d86b6220-e232-423a-bf5f-90903e6887c3.png">          <img height="50" src="https://user-images.githubusercontent.com/25181517/183914128-3fc88b4a-4ac1-40e6-9443-9a30182379b7.png">       <img height="50" src="https://www.macobserver.com/wp-content/uploads/2019/05/workfeatured-GitHub-2.png">       <img height="50" src="https://user-images.githubusercontent.com/25181517/183423507-c056a6f9-1ba8-4312-a350-19bcbc5a8697.png">       <img height="50" src="https://user-images.githubusercontent.com/25181517/117207330-263ba280-adf4-11eb-9b97-0ac5b40bc3be.png">       <img height="50" src="https://user-images.githubusercontent.com/25181517/182884177-d48a8579-2cd0-447a-b9a6-ffc7cb02560e.png">


## 🛠️ Tech Stack Description

| 🐍 Python - Core ML development 
| 🐳 Docker - Containerization 
| 🧬 MLflow - Model tracking & comparison 
| ⚙️ GitHub Actions - CI/CD pipeline 
| 🧮 Airflow - Workflow orchestration (prod) 
| 🚦 Prometheus - Monitoring & metrics 
| ⚡ FastAPI - Real-time inference API 

## ☁️ Infrastructure Overview
<img height="50" src="https://user-images.githubusercontent.com/25181517/183896132-54262f2e-6d98-41e3-8888-e40ab5a17326.png">       <img height="50" src="https://user-images.githubusercontent.com/25181517/183868728-b2e11072-00a5-47e2-8a4e-4ebbb2b8c554.png">   

| Environment       | Stack                                                  |
|-------------------|--------------------------------------------------------|
| **Production**    | AWS EC2, S3, ECR, IAM, Docker, Airflow, GitHub Actions |
| **Sandbox / Dev** | Docker Compose, FastAPI, MLflow, Prometheus            |


✅ AWS Services Used: EC2, S3, ECR, IAM
✅ Prod MLOps Tools: Docker, GitHub Actions, Airflow
✅ Dev Environment: FastAPI, MLflow, Prometheus



## 📂 Dataset Overview

    Source: Kaggle - APS Failure at Scania Trucks

    Features: 171 sensor features (continuous & categorical)

    Target: class (0 = not APS fault, 1 = APS fault)

    Imbalance:

    Class 0: ~59,000 samples

    Class 1: ~1,000 samples

    ⚠️ This is a highly imbalanced dataset, which requires careful sampling and evaluation.

## Dataset Source Link :

    [Sensor_fault_detection](https://www.kaggle.com/datasets/uciml/aps-failure-at-scania-trucks-data-set)



## Data Collections
![image](https://user-images.githubusercontent.com/57321948/193536736-5ccff349-d1fb-486e-b920-02ad7974d089.png)


## Project Archietecture
![image](https://user-images.githubusercontent.com/57321948/193536768-ae704adc-32d9-4c6c-b234-79c152f756c5.png)


## Deployment Archietecture
![image](https://user-images.githubusercontent.com/57321948/193536973-4530fe7d-5509-4609-bfd2-cd702fc82423.png)



🔁 MLOps Pipeline Components

    Data Ingestion  →  Data Validation  →  Data Transformation -> Model Training  →  Model Evaluation  →  Model Pusher


✅ Components Description

    Data Ingestion: Load raw data from MongoDB or local source

    Data Validation: Check schema, missing/null values, duplicates

    Data Transformation: Scaling, encoding, outlier removal

    Model Trainer: Train multiple models & log to MLflow

    Model Evaluation: Compare metrics and select best model

    Model Pusher: Register and save production model


🔄 CI/CD Workflow

    ✅ Trigger: Push to main or PR

    🐳 Docker build & push to AWS ECR

    🚀 SSH into EC2 and deploy updated container

    🔁 Airflow reloads DAGs from latest Docker image


🛡️ Security Practices

    🔐 Secrets managed via .env.yaml and environment variables

    ✅ Role-based IAM in AWS

    🚫 No hardcoded credentials or private keys in codebase

    ✅ GitHub Actions with least privilege deployment




🛠 Future Enhancements

    Add SHAP/LIME for model interpretability

    Implement data & concept drift detection

    Enable Grafana dashboards for observability

    Automate retraining pipeline on drift signal


✅ Project Status

    Production-ready pipeline with Airflow on EC2

    Dev sandbox with FastAPI + MLflow

    Real-time monitoring via Prometheus

    CI/CD with GitHub Actions

    Drift Detection (Planned)

    Explainability Dashboard (Planned)