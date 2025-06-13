# 1.0 Sensor Fault Detection Using Official Scania Dataset
An end-to-end predictive maintainance Data Science project to predict APS sensor fault detection, based on Scania dataset from Kaggle. 

<img src="https://github.com/Bhardwaj-Saurabh/Sensor_Fault_Detection_Scania/blob/master/images/Scania.jpg">

## 2.0 Problem Statement
The Air Pressure System (APS) is a critical component of a heavy-duty vehicle that uses compressed air to force a piston to provide pressure to the brake pads, slowing the vehicle down. The benefits of using an APS instead of a hydraulic system are the easy availability and long-term sustainability of natural air. The data set is provided by Scania with open source licence.

This is a Binary Classification problem, in which the affirmative class indicates that the failure was caused by a certain component of the APS, while the negative class indicates that the failure was caused by something else.

As the problem is to reduce the cost due to unnecessary repairs, it is important to reduce false positives and false negatives. More importantly, to reduce false negatives, since cost incurred due to false negative is 50 times higher than the false positives as shown in [EDA notebook.](https://github.com/Bhardwaj-Saurabh/Sensor_Fault_Detection_Scania/blob/master/notebooks/Scania_APS_failure_prediction.ipynb) 

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



## Solution Strategy
My solution to solve this problem will be the development of a data science project. This project will have a machine learning model which can predict if the fault is caused by APS sensor or not based on provided features.

**Step 01. Data Description:** The missing values will be threated or removed. Finally, a initial data description will carried out to know the data. Therefore some calculations of descriptive statistics will be made, such as skewness, mean, median and standard desviation.

**Step 02. Exploratory Data Analysis:** The exploratory data analysis section consists of univariate analysis analysis to assist in understanding of the database mainly to check the data distribution of the sensor readings.

**Step 03. Feature Engineering:** In this section, data transformation has been applied to the whole data set using robust scaler. As the data is impbalanced, SMOT technique has been used to treat the dataset.

**Step 04. Data Preparation:** In this section, the data will be prepared for machine learning modeling. Not that there is no feature selection required as we have used all the sensor recording to fully utilise the readings from the sensor.

**Step 06. Machine Learning Modeling:** Here, the aim to train the machine learning algorithms and how they can predict the data. For validation the model is trained, validated and applied to cross validation to know the learning capacity of the model.

**Step 07. Conclusions:** This is a conclusion stage which the generation capacity model is tested using unseen data. In addition, some business questions are answered to show the applicability of the model in the business context.

**Step 8. Model Deploy:** This is the final step of the data science project. So, in this step the flask api is created. The model and the functions are saved to be implemented in the api. Finally, the model has been deployed using AWS EC2.

