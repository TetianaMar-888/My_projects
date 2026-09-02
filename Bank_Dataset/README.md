# Bank_Dataset_Machine_Learning_Project
Overview

This project focuses on a real-world binary classification problem: predicting whether a client will subscribe to a term deposit based on data from direct marketing campaigns of a Portuguese bank.

Dataset size: 41,188 records
Features: 20 → expanded to 48 after encoding
Class imbalance: 89% / 11%
The project demonstrates an end-to-end ML pipeline: from EDA and preprocessing to model selection, tuning, and business-driven evaluation.

Objective

Build and evaluate machine learning models to maximize business impact, with a focus on:

Identifying потенциальних клієнтів (high Recall)
Maintaining good ranking quality (ROC-AUC)
Ensuring interpretability for business stakeholders
Data Processing & Feature Engineering
Handled class imbalance using SMOTE
Treated unknown values as a separate category (preserving signal)
Engineered feature:
pdays → was_contacted (binary)
Removed duration from training to avoid data leakage
Applied One-Hot Encoding → 48 features
Stratified split:
Train: 52.5%
Validation: 17.5%
Test: 30%
Standardization applied for distance-based and linear models

## Models & Experimentation
Implemented and compared multiple models:

| # | Model | Features |
|---|---|---|
| 1 | Logistic Regression | baseline, C=1.0 |
| 2 | kNN | n_neighbors=7 |
| 3 | Decision Tree | default, max_depth=3, max_depth=5 |
| 4 | XGBoost | default, RandomizedSearch, Bayesian Optimization |

---

## Results Table
| Model | ROC-AUC Val | ROC-AUC Test | F1 Test | Recall Test | Comment |
|---|---|---|---|---|---|
| Logistic Regression | 0.71 | 0.73 | 0.39 | 0.42 | Baseline model |
| kNN | 0.71 | 0.73 | 0.39 | 0.47 | Slow, weak |
| DT (default) | 0.63 | 0.63 | 0.32 | 0.36 | Overfitting   |
| DT (max_depth=5) | 0.75 | 0.75 | 0.47 | 0.57 | Good Recall |
| **DT (max_depth=3)** | **0.75** | **0.76** | **0.46** | **0.61** | **Best Recall ** |
| XGBoost (default) | 0.77 | 0.78 | 0.43 | 0.38 | Good baseline |
| XGBoost (RandomizedSearch) | 0.76 | 0.77 | 0.43 | 0.37 | Worse than default |
| **XGBoost (Bayesian)** | **0.78** | **0.79** | **0.46** | **0.43** | **Best ROC-AUC ** |

Conclusions

Achieved:
XGBoost (Bayesian) — best ROC-AUC (0.79) and Precision
DT (max_depth=3) — best Recall (0.61), identifies 855/1392 potential clients
Minimal overfitting in DT3 (Train vs Test difference = 0.03)
Clients with calls >500 sec have a conversion rate of 40% vs 11% average
SHAP analysis confirmed that the key features — nr.employed, cons.conf.idx, education — are economically logical.

For bank marketing, DT (max_depth=3) is recommended:

Identifies 855 clients (61%) with minimal overfitting
Transparent logic — easy to explain to management and regulators

What Can Be Improved
DirectionHowClassification thresholdLower from 0.5 → increases RecallNew featuresAge segmentation, education+job combination, seasonalityTwo-model strategyDT3 filters out "no" → XGBoost refines the rest

## Files
- `Bank_Dataset_Machine_Learning_Project_english.ipynb` — full analysis and modeling code
