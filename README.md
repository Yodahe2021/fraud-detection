# Fraud Detection for E-Commerce and Bank Transactions

## Project Overview
This project focuses on building **robust, accurate, and explainable fraud detection models** for **e-commerce transactions** and **bank credit card transactions**. The solution addresses the critical challenge of **severely imbalanced datasets** (where fraud cases are rare) while carefully balancing **fraud prevention** with **customer experience**.

Using advanced **machine learning techniques**, **feature engineering**, and **geolocation analysis**, the project aims to detect fraudulent activities effectively and provide **actionable business insights** suitable for real-world deployment.

---

## Business Context
Fraud detection systems must manage a difficult trade-off:

- **Financial Loss (False Negatives):**  
  Missed fraudulent transactions result in direct financial loss.

- **Customer Friction (False Positives):**  
  Legitimate users incorrectly flagged as fraud may abandon the platform.

To address this, the project prioritizes **Average Precision (PR-AUC)** and **F1-Score**, ensuring the model remains **stable, reliable, and practical** for production use.

---

## Technical Environment
To ensure full reproducibility and avoid compatibility issues (notably with NumPy 2.0), the project uses a controlled local environment.

- **Python Version:** 3.11  
- **Core ML Library:** `scikit-learn==1.3.2`  
- **Environment Manager:** Conda (local `.conda` prefix)  
- **Dependencies:** Defined in `requirements.txt`

---

## Setup Instructions
```bash
# Install project dependencies
pip install -r requirements.txt
fraud-detection/
├── .conda/               # Local environment files (ignored by git)
├── data/                 # Data storage (ignored by git)
│   ├── raw/              # Original CSV files
│   └── processed/        # Model-ready data (after feature engineering)
├── notebooks/
│   ├── eda-fraud-data.ipynb
│   ├── feature-engineering.ipynb
│   └── modeling.ipynb    # Baseline models, tuning, SHAP, and evaluation
├── reports/
│   ├── figures/          # Saved plots (PR curves, SHAP, feature importance)
│   └── summary.md        # Final model selection rationale
├── models/               # Saved model artifacts (.pkl / .joblib)
├── requirements.txt      # Project dependencies
├── README.md             # Project documentation
└── .gitignore            # Files excluded from version control
Methodology & Modeling
1. Handling Class Imbalance

Fraud datasets are highly imbalanced. To address this:

Applied SMOTE (Synthetic Minority Over-sampling Technique) only on training data

Ensures the model learns meaningful fraud patterns rather than defaulting to majority-class predictions

2. Model Evaluation Strategy

A robust and reproducible evaluation pipeline was implemented in modeling.ipynb:

Baseline Models:

Logistic Regression

Random Forest Ensemble

Cross-Validation:

5-Fold Stratified Cross-Validation

Reports mean and standard deviation for performance stability

Hyperparameter Tuning:

GridSearchCV used to optimize:

n_estimators

max_depth

min_samples_split

3. Model Explainability (SHAP)

To ensure transparency and business trust:

Used SHAP (SHapley Additive exPlanations)

Interprets model predictions by quantifying feature contributions

Identifies high-risk indicators such as:

Purchase value

Time-to-purchase

Geolocation signals

This enables actionable insights rather than opaque predictions.

Datasets
1. E-Commerce Fraud Dataset (Fraud_Data.csv)

User registration and purchase timestamps

Device identifiers

IP addresses for geolocation analysis

2. IP Geolocation Dataset (IpAddress_to_Country.csv)

Maps IP address ranges to countries

Enables geographic fraud risk analysis

3. Credit Card Dataset (creditcard.csv)

PCA-transformed bank transaction data

Used to validate model robustness on anonymized, real-world financial data

How to Run the Project

Clone the repository

Ensure Python 3.11 is active

Run feature engineering:

notebooks/feature-engineering.ipynb


Train and evaluate models:

notebooks/modeling.ipynb


Review results and visualizations in:

reports/figures/

Key Outcomes

Strong performance on highly imbalanced datasets

Emphasis on PR-AUC and F1-score for real-world reliability

Transparent, explainable models using SHAP

Scalable and reproducible pipeline suitable for production deployment
