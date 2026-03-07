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
