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
ffbd - lenden_mlops_pipeline/git_ ff_bd/preprocessing_and_logging_500_features.ipynb
ffmw - lenden_mlops_pipeline/git_ff_mw/ff_mw/preprocessing_loggng_to_feature_store.ipynb


---

## 2 Training using All Features

Train model using all 500 features and log metrics in MLflow.
ffbd - lenden_mlops_pipeline/git_ ff_bd/training_all_features.ipynb
ffmw - lenden_mlops_pipeline/git_ff_mw/ff_mw/updataed_training.ipynb


---

## 3 Feature Selection

Select top 50 most important features.
ffbd - lenden_mlops_pipeline/git_ ff_bd/feature_selection.ipynb
ffmw - lenden_mlops_pipeline/git_ff_mw/ff_mw/feature_selection.ipynb
---

## 4 Training on Top 50 Features

Train model using selected features and store them in Feature Store.
ffbd - lenden_mlops_pipeline/git_ ff_bd/top_50_training.ipynb
ffmw - lenden_mlops_pipeline/git_ff_mw/ff_mw/50 version training and model registary.ipynb
---

## 5 Model Logging

Log model artifacts and register model in MLflow Model Registry.
ffbd - lenden_mlops_pipeline/git_ ff_bd/model_logging.ipynb

---

## 6 Model Comparison

Compare performance of:

- Model trained with 500 features
- Model trained with 50 features
ffbd - lenden_mlops_pipeline/git_ ff_bd/top50vs500.ipynb
ffmw - lenden_mlops_pipeline/git_ff_mw/ff_mw/50vs500model comparison.ipynb
---
## 7 model evaluation 
compare new model to production mdoel
---
ffbd - lenden_mlops_pipeline/git_ ff_bd/model_evaluations.ipynb
ffmw - lenden_mlops_pipeline/git_ff_mw/ff_mw/mw_evaluation.ipynb
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

notebook used-
ffbd - lenden_mlops_pipeline/git_Drift/Data Drift - ff_bd_updated.ipynb
ffmw - lenden_mlops_pipeline/git_Drift/Data Drift - ff_mw_updated.ipynb

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
ffmbd- lenden_mlops_pipeline/git_Drift/model_drift_updated_bd.ipynb
ffmw - lenden_mlops_pipeline/git_Drift/model_drift_updated_mw.ipynb

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
