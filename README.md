# Sensor Fault Detection in APS using production grade MlOps pipelines


![Scania Truck](Scania.jpg)


## Problem Statement
The Air Pressure System (APS) is a critical component of a heavy-duty vehicle that uses compressed air to force a piston to provide pressure to the brake pads, slowing the vehicle down. The benefits of using an APS instead of a hydraulic system are the easy availability and long-term sustainability of natural air. The data set is provided by Scania with open source licence.

This is a Binary Classification problem, in which the affirmative class indicates that the failure was caused by a certain component of the APS, while the negative class indicates that the failure was caused by something else.

As the problem is to reduce the cost due to unnecessary repairs, it is important to reduce false positives and false negatives. More importantly, to reduce false negatives, since cost incurred due to false negative is 50 times higher than the false positives.

## Tech Stack Used
<img height="50" src="https://user-images.githubusercontent.com/25181517/192108891-d86b6220-e232-423a-bf5f-90903e6887c3.png">          <img height="50" src="https://user-images.githubusercontent.com/25181517/183914128-3fc88b4a-4ac1-40e6-9443-9a30182379b7.png">       <img height="50" src="https://www.macobserver.com/wp-content/uploads/2019/05/workfeatured-GitHub-2.png">       <img height="50" src="https://user-images.githubusercontent.com/25181517/183423507-c056a6f9-1ba8-4312-a350-19bcbc5a8697.png">       <img height="50" src="https://user-images.githubusercontent.com/25181517/117207330-263ba280-adf4-11eb-9b97-0ac5b40bc3be.png">       <img height="50" src="https://user-images.githubusercontent.com/25181517/182884177-d48a8579-2cd0-447a-b9a6-ffc7cb02560e.png">

## Infrastructure Required 
<img height="50" src="https://user-images.githubusercontent.com/25181517/183896132-54262f2e-6d98-41e3-8888-e40ab5a17326.png">       <img height="50" src="https://user-images.githubusercontent.com/25181517/183868728-b2e11072-00a5-47e2-8a4e-4ebbb2b8c554.png">   


```
AWS Services: IAM,EC2,S3,ECR
MlOps Infrastructure in Production: Docker, GithubActions , Airflow
MlOps Infrastructure in Sanboxed / Testing (For stakeholder facing services): FASTAPI , Mlflow , Prometheus

```

## Data Description
**The dataset** The dataset consists of data collected from heavy Scania trucks in everyday usage. The system in focus is the Air Pressure system (APS) which generates pressurised air that are utilized in various functions in a truck, such as braking and gear changes. The datasets' positive class consists of component failures for a specific component of the APS system. The negative class consists of trucks with failures for components not related to the APS. The data consists of a subset of all available data, selected by experts. The goal is to predict `class` 0 or 1. There are 171 independent variables available in the dataset.

The dataset is highly imbalanced with 59000 instance of neg class and only 1000 instance of pos class.

Target variable:
* `class`: 0 if not caused by APS otherwise 1 .

Dataset Source Link :
[Sensor_fault_detection](https://www.kaggle.com/datasets/uciml/aps-failure-at-scania-trucks-data-set)



## Data Collections
![image](https://user-images.githubusercontent.com/57321948/193536736-5ccff349-d1fb-486e-b920-02ad7974d089.png)


## Project Archietecture
![image](https://user-images.githubusercontent.com/57321948/193536768-ae704adc-32d9-4c6c-b234-79c152f756c5.png)


## Deployment Archietecture
![image](https://user-images.githubusercontent.com/57321948/193536973-4530fe7d-5509-4609-bfd2-cd702fc82423.png)

