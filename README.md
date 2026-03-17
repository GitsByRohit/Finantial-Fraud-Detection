# Financial Fraud Detection System

## Overview

The Financial Fraud Detection System is an end-to-end machine learning application designed to detect fraudulent financial transactions in real time. The project combines machine learning models, real-time data streaming using Apache Kafka, and an interactive analytics dashboard built with Flask and Plotly.

The system processes transaction data, predicts fraud probability using trained machine learning models, classifies transactions into multiple risk levels, and visualizes the results through a professional dashboard.

This project demonstrates how modern technologies such as machine learning, streaming pipelines, and interactive data visualization can be integrated to build an intelligent fraud monitoring system.

## Problem Statement

Financial fraud has become one of the major challenges faced by banking institutions and online payment systems. As digital transactions increase, fraudsters continuously develop sophisticated techniques to bypass traditional rule-based detection systems.

Manual monitoring of millions of transactions is impossible, and static rule systems often fail to adapt to evolving fraud patterns. Therefore, financial institutions require automated systems capable of analyzing transaction patterns and detecting suspicious activity in real time.

This project aims to address this problem by developing a machine learning-based fraud detection pipeline integrated with real-time streaming technology and an analytical dashboard.

## Objectives

The main objectives of this project are:

- Build a machine learning model capable of detecting fraudulent financial transactions.

- Perform data preprocessing and feature engineering to improve model accuracy.

- Train and compare multiple machine learning models.

- Select the best model using evaluation metrics such as Recall, Precision, and ROC-AUC.

- Implement real-time transaction processing using Apache Kafka.

- Store prediction results in a database for analytics.

- Develop a Flask-based dashboard for monitoring fraud activity.

- Visualize fraud patterns using interactive Plotly charts.

- Provide a manual prediction interface for testing transactions.

- Classify transactions into four risk levels:

  - 🟢 **Low Risk**
  - 🟡 **Medium Risk**
  - 🟠 **High Risk**
  - 🔴 **Critical Fraud**

## System Architecture

The system consists of several interconnected modules that form a complete fraud detection pipeline.

```
Dataset
   │
   ▼
Data Preprocessing
   │
   ▼
Feature Engineering
   │
   ▼
Machine Learning Models
(Logistic Regression, Random Forest, XGBoost, LightGBM)
   │
   ▼
Model Selection
   │
   ▼
Best Model Saved
   │
   ▼
Kafka Producer → Kafka Topic → Kafka Consumer
                              │
                              ▼
                        Fraud Prediction
                              │
                              ▼
                         SQLite Database
                              │
                              ▼
                   Flask Web Application
                              │
                              ▼
                       Analytics Dashboard
```

# Machine Learning Pipeline

The machine learning pipeline consists of several stages:

---

## 1. Data Preprocessing

The raw dataset is cleaned and prepared for machine learning.

### Operations Performed:
- Handling missing values  
- Removing unnecessary columns  
- Converting timestamps  
- Preparing training and testing datasets  

---

## 2. Feature Engineering

Feature engineering was implemented to improve model performance.

### Key Engineered Features:
- Transaction hour  
- Transaction day  
- Transaction month  
- Customer age  
- Distance from home  
- Merchant encoding  
- Category encoding  
- ZIP encoding  

**Final Dataset:**  
- 11 features + 1 target variable  

---

## 3. Handling Class Imbalance

Fraud datasets are highly imbalanced because fraudulent transactions are much fewer than legitimate ones.

### Steps Taken:
- Class distribution analysis  
- Dataset balancing techniques applied  

**Impact:**  
- Significantly improved fraud detection performance  

---

## 4. Model Training

Multiple machine learning models were trained:

- Logistic Regression  
- Random Forest  
- XGBoost  
- LightGBM  

### Evaluation Metrics:
- Confusion Matrix  
- Precision  
- Recall  
- F1 Score  
- ROC-AUC  

---

## 5. Model Selection

Fraud detection prioritizes **recall** because missing fraudulent transactions is more harmful than false alerts.

- Models are automatically compared  
- Best model selected based on recall  

**Selected Model:**  
- **LightGBM**

---

# Risk Classification System

Transactions are categorized into four risk levels based on fraud probability:

| Probability | Risk Level        |
|------------|------------------|
| < 0.50     | Low Risk         |
| 0.50 – 0.75 | Medium Risk      |
| 0.75 – 0.90 | High Risk        |
| > 0.90     | Critical Fraud   |

**Purpose:**  
- Helps analysts prioritize investigations  

---

# Real-Time Streaming Pipeline

## Apache Kafka Components

### Kafka Producer
- Continuously sends transaction records to a Kafka topic  

### Kafka Topic
- Acts as a message queue for streaming transactions  

### Kafka Consumer
- Reads transactions from Kafka  
- Sends them to the prediction module  
- Calculates fraud probability  
- Assigns risk level  
- Stores results in the database  

---

# Database Layer

A SQLite database stores processed transactions.

### Each Record Includes:
- Transaction ID  
- Transaction Amount  
- Category  
- Prediction Result  
- Fraud Probability  
- Risk Level  
- Timestamp  

**Purpose:**  
- Enables dashboard to display historical data  

---

# Web Application

Developed using **Flask**

### Main Components:
- Authentication system  
- Dashboard  
- Manual fraud prediction interface  
- Result page  
- Charts visualization  

---

# Dashboard

Provides real-time analytics of transaction data.

### Features:
- Total transactions counter  
- Fraud distribution summary  
- Recent transaction table  
- Risk classification indicators  

---

# Data Visualization

The dashboard contains **20 interactive charts** created using Plotly.

### Examples:
- Risk level distribution  
- Fraud probability distribution  
- Transaction amount analysis  
- Category-wise fraud detection  
- Fraud trend over time  
- Probability vs amount scatter plot  
- Risk heatmaps  
- Transaction volume trends  

**Note:**  
- Charts automatically update when new data is inserted into the database  

---

# Technologies Used

| Technology     | Purpose                          |
|---------------|----------------------------------|
| Python        | Core programming language        |
| Pandas        | Data processing                  |
| NumPy         | Numerical computation            |
| Scikit-learn  | Machine learning models          |
| XGBoost       | Gradient boosting model          |
| LightGBM      | High performance boosting        |
| Apache Kafka  | Real-time streaming              |
| SQLite        | Database                         |
| Flask         | Web framework                    |
| Plotly        | Interactive charts               |
| Matplotlib    | Data visualization               |
| Seaborn       | Exploratory data analysis        |

# Project Structure 

```
financial-fraud-detection/
│
├── data/
│ ├── raw/
│ └── processed/
│
├── src/
│ ├── config.py
│ ├── data_preprocessing.py
│ ├── feature_engineering.py
│ ├── train_logistic_regression.py
│ ├── train_random_forest.py
│ ├── train_xgboost.py
│ ├── train_lightgbm.py
│ ├── model_evaluation.py
│ ├── model_selector.py
│ └── predict.py
│
├── streaming/
│ ├── kafka_config.py
│ ├── producer.py
│ └── consumer.py
│
├── models/
│ └── saved_models/
│
├── reports/
│ └── evaluation_reports/
│
├── app/
│ ├── app.py
│ ├── auth.py
│ ├── database.py
│ └── charts.py
│
├── templates/
│ ├── login.html
│ ├── signup.html
│ ├── dashboard.html
│ ├── predict.html
│ └── result.html
```

# Dataset

The dataset used in this project contains financial transaction records used to train and evaluate the fraud detection model.

Due to file size limitations, the dataset is not included directly in this repository.

You can download the dataset from the following source:

## Dataset Link
```
https://www.kaggle.com/datasets/kartik2112/fraud-detection
```

This dataset contains simulated credit card transaction data including transaction details, merchant information, geographic attributes, timestamps, and fraud labels.

Dataset Files Used

The project uses two dataset files:
```
fraudTrain.csv
fraudTest.csv
```

These files represent:

File	Description
fraudTrain.csv	Training dataset used for model training
fraudTest.csv	Testing dataset used for model evaluation
Dataset Placement

After downloading the dataset, place the files inside the following directory:
```
data/raw/

Final structure:

data/
   raw/
      fraudTrain.csv
      fraudTest.csv
```

# How to Run this Project :

Follow the steps below to run the complete fraud detection system.

## 1. Clone the Repository
```
git clone https://github.com/your-username/financial-fraud-detection.git
cd financial-fraud-detection
```


## 2. Install Dependencies

Install all required Python libraries.
```
pip install -r requirements.txt
```

## 3. Download Dataset

Download the dataset from Kaggle:
```
https://www.kaggle.com/datasets/kartik2112/fraud-detection
```

Place the dataset files in:
```
data/raw/
```

## 4. Run Data Preprocessing
```
python -m src.data_preprocessing
```

This step cleans and prepares the raw dataset for feature engineering.

## 5. Run Feature Engineering
```
python -m src.feature_engineering
```
This step generates the final dataset used for training models.

## 6. Train Machine Learning Models

Train individual models:
```

python -m src.train_logistic_regression
python -m src.train_random_forest
python -m src.train_xgboost
python -m src.train_lightgbm
7 Select Best Model
python -m src.model_selector

```

This script evaluates all trained models and selects the best model based on recall score.

## 8. Start Kafka Streaming

Start Kafka services.

Run Kafka consumer:
```
python -m streaming.consumer
```

Run Kafka producer:
```
python -m streaming.producer
```

The producer sends transaction data and the consumer processes them using the trained model.

## 9. Run Web Application

Start the Flask application.
```
python -m app.app
```

## 10. Open Dashboard

Open your browser and visit:
```
http://127.0.0.1:5000
```

You can now access:

- Login page
- Fraud analytics dashboard
- Manual prediction interface
- Real-time transaction monitoring

---

# Results

The system successfully detects fraudulent transactions and classifies them into risk levels. The integration of machine learning with real-time streaming allows the system to simulate how real financial fraud monitoring systems operate.

The dashboard provides a clear overview of fraud activity, enabling analysts to identify suspicious patterns and trends.
---

# Challenges Faced

Several challenges were encountered during the development process:

- Handling class imbalance in the dataset

- Memory issues during feature encoding

- Integrating Kafka with the machine learning pipeline

- Ensuring consistent data flow between producer and consumer

- Designing a professional analytics dashboard

These challenges were addressed through iterative debugging and optimization.
---

# Limitations

The project has some limitations:

- Uses simulated transaction data

- Runs on a local environment

- Does not include distributed deployment

- Future versions could address these limitations by integrating cloud infrastructure.
---
# Future Improvements

- Possible future enhancements include:

- Deploying the system on cloud platforms

- Using deep learning models

- Implementing automated fraud alerts

- Scaling Kafka with distributed clusters

- Integrating advanced anomaly detection techniques
---

# License

This project is developed for educational and research purposes.
