# 1.0 Sensor Fault Detection Using Official Scania Dataset
An end-to-end predictive maintainance Data Science project to predict APS sensor fault detection, based on Scania dataset from Kaggle. 

![Scania Truck](./Scania.jpg)
<p align="center">
  <img src="Scania.jpg" alt="Scania Truck" width="400"/>
</p>


## 2.0 Problem Statement
The Air Pressure System (APS) is a critical component of a heavy-duty vehicle that uses compressed air to force a piston to provide pressure to the brake pads, slowing the vehicle down. The benefits of using an APS instead of a hydraulic system are the easy availability and long-term sustainability of natural air. The data set is provided by Scania with open source licence.

This is a Binary Classification problem, in which the affirmative class indicates that the failure was caused by a certain component of the APS, while the negative class indicates that the failure was caused by something else.

As the problem is to reduce the cost due to unnecessary repairs, it is important to reduce false positives and false negatives. More importantly, to reduce false negatives, since cost incurred due to false negative is 50 times higher than the false positives.

## 3.0 Tech Stack Used
<img height="50" src="https://user-images.githubusercontent.com/25181517/192108891-d86b6220-e232-423a-bf5f-90903e6887c3.png">          <img height="50" src="https://user-images.githubusercontent.com/25181517/183914128-3fc88b4a-4ac1-40e6-9443-9a30182379b7.png">       <img height="50" src="https://www.macobserver.com/wp-content/uploads/2019/05/workfeatured-GitHub-2.png">       <img height="50" src="https://user-images.githubusercontent.com/25181517/183423507-c056a6f9-1ba8-4312-a350-19bcbc5a8697.png">       <img height="50" src="https://user-images.githubusercontent.com/25181517/117207330-263ba280-adf4-11eb-9b97-0ac5b40bc3be.png">       <img height="50" src="https://user-images.githubusercontent.com/25181517/182884177-d48a8579-2cd0-447a-b9a6-ffc7cb02560e.png">

## Infrastructure Required
<img height="50" src="https://user-images.githubusercontent.com/25181517/183896132-54262f2e-6d98-41e3-8888-e40ab5a17326.png">       <img height="50" src="https://user-images.githubusercontent.com/25181517/183868728-b2e11072-00a5-47e2-8a4e-4ebbb2b8c554.png">   

## 4.0 Data Description
**The dataset** The dataset consists of data collected from heavy Scania trucks in everyday usage. The system in focus is the Air Pressure system (APS) which generates pressurised air that are utilized in various functions in a truck, such as braking and gear changes. The datasets' positive class consists of component failures for a specific component of the APS system. The negative class consists of trucks with failures for components not related to the APS. The data consists of a subset of all available data, selected by experts. The goal is to predict `class` 0 or 1. There are 171 independent variables available in the dataset.

The dataset is highly imbalanced with 59000 instance of neg class and only 1000 instance of pos class.

Target variable:
* `class`: 0 if not caused by APS otherwise 1 .

Dataset Source Link :
[Sensor_fault_detection](https://www.kaggle.com/datasets/uciml/aps-failure-at-scania-trucks-data-set)

## 5.0 Business Assumptions
Followings assumptions have been made to define the solution strategy for diamind price prediction.

1. Dataset Reliability: Assume that the dataset provided is reliable and accurately represents the real-world scenario of APS failures in Scania trucks.

2. Data Independence: Assume that each instance (row) in the dataset is independent of others. There should be no hidden dependencies or correlations between instances that could bias the results.

3. Feature Completeness: Assume that the dataset includes all the necessary features required for the detection of APS faults. You can assume that no crucial feature is missing, which would significantly impact the performance of the model.

4. Class Imbalance: Assume that the dataset may suffer from class imbalance, meaning there may be significantly more instances of non-faulty APS readings compared to faulty readings. You might need to address this imbalance to avoid bias towards the majority class during model training.

## 6.0 Product Structure

```
Sensor_Fault_Dectection_Scania
├── README.md                                     # Read me file for the project
├── config                                        # System Configurations directory
│   └── schema.yaml
├── logs                                          # logs directory
├── main.py                                       # application file
├── notebooks                                     # Data Analysis and experiments
│   └── Scania_APS_failure_prediction.ipynb
├── requirements.txt                              # system dependencies
├── saved_models                                  # final model
│   └── 1680182317
│       └── model.pkl
├── setup.py                                      # setup file
└── src                                           # package
    ├── cloud_storage
    │   └── __init__.py
    ├── components                                # system components
    │   ├── data_ingestion.py
    │   ├── data_transformation.py
    │   ├── data_validation.py
    │   ├── model_evaluation.py
    │   ├── model_pusher.py
    │   └── model_trainer.py
    ├── configuration                             # data configurations
    │   └── mongo_db_connection.py
    ├── constant                                  # constant directory
    │   ├── application.py
    │   ├── database.py
    │   ├── env_variable.py
    │   ├── s3_bucket.py
    │   └── training_pipeline
    ├── data_access                               # data access directory
    │   └── sensor_data.py
    ├── entity                                    # components entity and artifacts constants
    │   ├── artifact_entity.py
    │   └── config_entity.py
    ├── exception.py                              # exception generator
    ├── logger.py                                 # logging generator
    ├── ml                                        # machine learning components directory
    │   ├── metric
    │   │   └── classification_metric.py
    │   └── model
    │       └── estimator.py
    ├── pipeline                                  # system pipeline
    │   └── training_pipeline.py
    └── utils                                     # util and helper function directory
       └── main_utils.py
```

## 7.0 Solution Strategy
My solution to solve this problem will be the development of a data science project. This project will have a machine learning model which can predict if the fault is caused by APS sensor or not based on provided features.

**Step 01. Data Description:** The missing values will be threated or removed. Finally, a initial data description will carried out to know the data. Therefore some calculations of descriptive statistics will be made, such as skewness, mean, median and standard desviation.

**Step 02. Exploratory Data Analysis:** The exploratory data analysis section consists of univariate analysis analysis to assist in understanding of the database mainly to check the data distribution of the sensor readings.

**Step 03. Feature Engineering:** In this section, data transformation has been applied to the whole data set using robust scaler. As the data is impbalanced, SMOT technique has been used to treat the dataset.

**Step 04. Data Preparation:** In this section, the data will be prepared for machine learning modeling. Not that there is no feature selection required as we have used all the sensor recording to fully utilise the readings from the sensor.

**Step 06. Machine Learning Modeling:** Here, the aim to train the machine learning algorithms and how they can predict the data. For validation the model is trained, validated and applied to cross validation to know the learning capacity of the model.

**Step 07. Conclusions:** This is a conclusion stage which the generation capacity model is tested using unseen data. In addition, some business questions are answered to show the applicability of the model in the business context.

**Step 8. Model Deploy:** This is the final step of the data science project. So, in this step the flask api is created. The model and the functions are saved to be implemented in the api. Finally, the model has been deployed using AWS EC2.

## 8.0 Top Data Insights

<img src="https://github.com/Bhardwaj-Saurabh/Sensor_Fault_Detection_Scania/blob/master/images/y_label.png" width="400">

As highlighted above, images shows the imbalance of depedent variable.

<img src="https://github.com/Bhardwaj-Saurabh/Sensor_Fault_Detection_Scania/blob/master/images/missing_value.png" width="800">

The image above shows the missing values present in the dataset.

<img src="https://github.com/Bhardwaj-Saurabh/Sensor_Fault_Detection_Scania/blob/master/images/distribution.png" width="800">

The image above shows data distribution of first few sensor reading. Intrestingly, for almost all sensors, the data is normally distributed and also lies within the same range.

## 9.0 Machine Learning Applied
Here's the results of the machine learning models with their different imputation methods.
```
+--------------------+-------------------------+------------+
|       Model        |    Imputation_method    | Total_cost |
+--------------------+-------------------------+------------+
|   XGBClassifier    | Simple Imputer-Constant |    2950    |
|   XGBClassifier    |           Mice          |    3510    |
|   XGBClassifier    |       Knn-Imputer       |    4460    |
|   XGBClassifier    |   Simple Imputer-Mean   |    4950    |
| CatBoostClassifier |          Median         |    5760    |
|   Random Forest    |           PCA           |   34150    |
+--------------------+-------------------------+------------+
```

## 10.0 Final Result

<img src="https://github.com/Bhardwaj-Saurabh/Sensor_Fault_Detection_Scania/blob/master/images/conf_matrix.png" width="600">

The final model is XGBoost Classifier with simple imputer with final accuracy of 99.6% and cost of 2950.

## 11.0 Run Application 

Make sure that you are have access to.

- MongoDB in your local system or MongoDB Atlas account,
- AWS account to access below service
  - AWS S3, 
  - AWS ECR, 
  - AWS EC2 instances.

**Step-1:** Create a new envionment

    conda create -p venv python==3.8

**Step-2:** Clone the repository

    git clone https://github.com/Bhardwaj-Saurabh/Sensor_Fault_Detection_Scania.git

**Step-3:** Install the necessary libraries

    pip install -r requirements.txt

**Step-4:** cd in to cloned folder

    cd Sensor_Fault_Detection_Scania

**Step-5:** Export the environment variable

export AWS_ACCESS_KEY_ID=<AWS_ACCESS_KEY_ID>

export AWS_SECRET_ACCESS_KEY=<AWS_SECRET_ACCESS_KEY>

export AWS_DEFAULT_REGION=<AWS_DEFAULT_REGION>

export MONGODB_URL="mongodb+srv://<username>:<password>@cluster0.yraezeq.mongodb.net/"

## 12.0 Conclusions

The conclusion of the Sensor Fault Detection project showcases my expertise in data science and machine learning. Through this project, I successfully developed a predictive model that accurately clasify if the fault in the system is caused by sensor or other components using Scania APS sensor dataset.

By leveraging advanced data analysis techniques, I was able to extract meaningful insights from the dataset and build a robust clasification model. The model demonstrated high accuracy in clasification task, enabling businesses in the automotive industry to make informed decisions and save cost.

This project highlights my proficiency in data preprocessing, feature engineering, and model development using popular machine learning algorithms. I showcased strong skills in Python programming, data manipulation with libraries like pandas and NumPy, and implementing machine learning models with scikit-learn.

Furthermore, this project demonstrates my ability to work on real-world data science problems and deliver valuable solutions. It showcases my analytical thinking, problem-solving skills, and attention to detail. The successful outcome of the project strengthens my credentials and positions me as a capable data scientist ready to tackle complex business challenges.

## 13.0  Challenges and other objectives

. Need to Handle many Null values in almost all columns
. No low-latency requirement.
. Interpretability is not important.
. Misclassification leads the unecessary repair costs.
