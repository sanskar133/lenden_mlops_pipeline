# LendingFlow MLOps Pipeline

This repository contains the end-to-end MLOps pipeline for LendingFlow models using Databricks, Delta Lake, Feature Store and MLflow.

## Pipeline Overview

The pipeline performs the following steps:

1. Data preprocessing and feature engineering
2. Training model on 500 features
3. Feature selection
4. Training model on top 50 features
5. Model logging and registration
6. Model comparison
7. model evaluation

## drift -
1. data drift
2. model drift

---

# Repository Structure

---

# Pipeline Steps

## 1 Preprocessing

Generate ~500 features from raw data and store them in a Delta table in Unity Catalog.

Notebook


---

## 2 Training using All Features

Train model using all 500 features and log metrics in MLflow.

---

## 3 Feature Selection

Select top 50 most important features.

---

## 4 Training on Top 50 Features

Train model using selected features and store them in Feature Store.

---

## 5 Model Logging

Log model artifacts and register model in MLflow Model Registry.

---

## 6 Model Comparison

Compare performance of:

- Model trained with 500 features
- Model trained with 50 features

---
## 7 model evaluation 
compare new model to production mdoel
---

# Data Drift Detection

Drift detection compares **training data with past 20 days inference data**.

Checks performed:

### Null Value Drift

Difference in null percentage between training and inference data should not exceed 10%.

### Schema Drift

Compare:

- Column names
- Data types
- Missing columns

### Data Quality Checks

Example rules:

- 0 < age < 100
- percentage between 0 and 100

### Distribution Drift

Categorical Features:
- Chi-Square Test

Continuous Features:
- Mean difference
- Standard deviation difference

---

# Model Drift Detection

Model drift is detected by comparing prediction probability distributions between:

- Production model
- Newly trained model

Steps:

1. Extract prediction probabilities
2. Divide probabilities into bins
3. Apply Chi-Square test
4. Detect significant distribution change

---

# Technologies Used

- Databricks
- Delta Lake
- Unity Catalog
- Databricks Feature Store
- MLflow
- PySpark
- Python
- Scikit-learn