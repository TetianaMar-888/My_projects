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
🔍 Data Processing & Feature Engineering
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
| DT (default) | 0.63 | 0.63 | 0.32 | 0.36 | Overfitting ❌  |
| DT (max_depth=5) | 0.75 | 0.75 | 0.47 | 0.57 | Good Recall |
| **DT (max_depth=3)** | **0.75** | **0.76** | **0.46** | **0.61** | **Best Recall ** |
| XGBoost (default) | 0.77 | 0.78 | 0.43 | 0.38 | Good baseline |
| XGBoost (RandomizedSearch) | 0.76 | 0.77 | 0.43 | 0.37 | Worse than default |
| **XGBoost (Bayesian)** | **0.78** | **0.79** | **0.46** | **0.43** | **Best ROC-AUC ✅ ** |

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


# Using Prompts and Agents in LangChain

This notebook demonstrates how to build LLM-powered pipelines using LangChain and Claude (Anthropic).

## Tasks Overview

**Task 1 — Basic LLM Call**
Simple prompt to get a structured explanation of a topic (Quantum Computing) with a response length limit.

**Task 2 — Parameterized Prompt Template**
Using `PromptTemplate` to dynamically pass topics to the model. Tested on Bayesian Methods, Transformers, and Explainable AI.

**Task 3 — ReAct Agent for Scientific Publications**
A ReAct-type agent with Tavily search that automatically finds 5 recent AI research papers, returning title, authors, and description for each.

**Task 4 — Business Analytics Agent**
An agent combining web search (Tavily) and Python execution (PythonREPLTool) to generate a sales forecast for a Brazilian orange exporter, incorporating real-time weather data, inflation rates, and global demand trends.

## Tools & Libraries
- `langchain`, `langchain-anthropic`, `langchain-tavily`
- `langchain-experimental` (PythonREPLTool)
- `Claude Sonnet` (Anthropic API)
- `scipy`, `numpy`, `pandas`, `matplotlib`

# SQL Tasks — Employees Database

This notebook contains practical SQL exercises executed against a real MySQL `employees` database using `pandas` and `mysql-connector-python`.

## Part 1 — JOIN Operations (10 tasks)

Covers multi-table joins across `employees`, `salaries`, `titles`, `dept_emp`, `departments`, and `dept_manager` tables:

- Joining employees with their current salary
- Joining employees with their current job title
- Joining employees with their current department
- Counting employees per department (sorted by headcount)
- Finding the highest-paid employee in the Development department
- Finding which department the highest-paid employee in the company works in
- Finding the employee with the 3rd highest salary (`OFFSET`)
- Identifying employees who held multiple positions (`GROUP_CONCAT`)
- Tracking department transfers (`GROUP_CONCAT` with chronological ordering)
- Retrieving current manager salary for each department

## Part 2 — Window Functions (7 tasks)

Covers SQL window functions:

- `ROW_NUMBER()` — sequential numbering of employees
- `LAG()` — salary dynamics (previous salary for comparison)
- `RANK()` — salary rank within each department
- `CTE + DATE_SUB` — salary change over the last 2 years
- `LEAD()` — finding the employee with the highest salary increase
- `NTILE()` — dividing employees into salary groups
- Combined CTEs — average salary and first hire per job title

## Tools & Libraries
- `mysql-connector-python` — MySQL connection
- `pandas` — query execution and result display
- `pandasql` — SQL queries on DataFrames
