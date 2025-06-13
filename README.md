# sensor_fault_detection
This is a fault detection project using sensor reading.


for linux:
$(pwd)/airflow/dags

docker run -p 8080:8080 -v %cd%\airflow\dags:/app/airflow/dags -e 'MONGO_DB_URL=mongodb+srv://avnish:Aa327030@cluster0.or68e.mongodb.net/?retryWrites=true&w=majority' sensor:latest 



Github Secrets:
```
AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
AWS_REGION=
AWS_ECR_LOGIN_URI=
ECR_REPOSITORY_NAME=
BUCKET_NAME=
MONGO_DB_URL=
```
# Sensor-APS-Fault-Prediction
# Sensor-Fault-Detection

### Problem Statement
The Air Pressure System (APS) is a critical component of a heavy-duty vehicle that uses compressed air to force a piston to provide pressure to the brake pads, slowing the vehicle down. The benefits of using an APS instead of a hydraulic system are the easy availability and long-term sustainability of natural air.

This is a Binary Classification problem, in which the affirmative class indicates that the failure was caused by a certain component of the APS, while the negative class
indicates that the failure was caused by something else.

### Solution Proposed 
In this project, the system in focus is the Air Pressure system (APS) which generates pressurized air that are utilized in various functions in a truck, such as braking and gear changes. The datasets positive class corresponds to component failures for a specific component of the APS system. The negative class corresponds to trucks with failures for components not related to the APS system.

The problem is to reduce the cost due to unnecessary repairs. So it is required to minimize the false predictions.
## Tech Stack Used
1. Python 
2. FastAPI 
3. Machine learning algorithms
4. Docker
5. MongoDB

## Infrastructure Required.

1. AWS S3
2. AWS EC2
3. AWS ECR
4. Git Actions


## Data Collections
![image](https://user-images.githubusercontent.com/57321948/193536736-5ccff349-d1fb-486e-b920-02ad7974d089.png)


## Project Archietecture
![image](https://user-images.githubusercontent.com/57321948/193536768-ae704adc-32d9-4c6c-b234-79c152f756c5.png)


## Deployment Archietecture
![image](https://user-images.githubusercontent.com/57321948/193536973-4530fe7d-5509-4609-bfd2-cd702fc82423.png)


### Step 1: Clone this repository

### Step 2- Create a conda environment after opening the repository.(Use conda create or python -m venv command)

### Step 3 - Install the requirements (bash)

pip install -r requirements.txt


### Step 4 - Export the environment variable (bash)

export AWS_ACCESS_KEY_ID=<AWS_ACCESS_KEY_ID>

export AWS_SECRET_ACCESS_KEY=<AWS_SECRET_ACCESS_KEY>

export AWS_DEFAULT_REGION=<AWS_DEFAULT_REGION>

export MONGODB_URL="Replace your mongodb atlas uri here"



### Step 5 - Run the application server (Has both /train and /test endpoints)

python app.py


### Step 6. Train application (If FastAPI runs sucesfully you'get have endpoint like below)
http://localhost:8080/train


### Step 7. Prediction application (If FastAPI runs sucesfully you'get have endpoint like below)

http://localhost:8080/predict

# APS-Sensor-Fault-Prediction
