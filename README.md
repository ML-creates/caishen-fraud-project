# Caishen Fraud Detection

## Project Overview

This project was developed for Caishen, a NYC-based international bank, to build a machine learning solution for identifying potentially fraudulent transactions.

The goal was to create a minimum viable product (MVP) using historical transaction data and an ensemble classification model.

## Project Objectives

- Explore and understand the transaction data
- Clean and preprocess the data
- Identify patterns associated with fraudulent transactions
- Build and evaluate a machine learning classifier
- Use an ensemble model to classify transactions as fraudulent or non-fraudulent
- Evaluate model performance using appropriate classification metrics

## Project Pipeline

1. Initial Exploratory Data Analysis (EDA)
2. Data Cleaning and Preprocessing
3. Model Creation
4. Hyperparameter Tuning
5. Model Evaluation
6. Final Report

## Models

The project includes:

- Logistic Regression as a baseline classification model
- Random Forest as the final ensemble classifier

The Random Forest model was selected because it can combine multiple decision trees to improve classification performance.

## Model Results

The final Random Forest model achieved:

- **Accuracy:** 1.00
- **Fraud Precision:** 1.00
- **Fraud Recall:** 1.00
- **Fraud F1-Score:** 1.00
- **ROC-AUC:** 0.9994

The model correctly identified 1,639 of 1,643 fraudulent transactions in the test set.

## Project Structure

```text
caishen-fraud-project/
│
├── Notebooks/
│   └── fraud_detection.ipynb
│
├── Reports/
│   └── fraud_detection_report.md
│
└── .gitignore
