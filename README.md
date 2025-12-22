# Fraud Detection for E-Commerce and Bank Transactions

## Project Overview
This project focuses on building robust, accurate, and explainable fraud detection models for **e-commerce transactions** and **bank credit card transactions**. The solution addresses the critical challenge of **severely imbalanced data** while balancing fraud prevention with customer experience.

Using advanced machine learning techniques, feature engineering, geolocation analysis, and explainable AI (SHAP), the project aims to detect fraudulent activities effectively and provide actionable business insights.

---

## Business Context
Fraud detection systems must carefully manage the trade-off between:
- **False Positives**: Legitimate transactions incorrectly flagged as fraud (poor customer experience)
- **False Negatives**: Fraudulent transactions missed (direct financial loss)

This project evaluates models using metrics suitable for imbalanced classification and emphasizes interpretability to support real-world deployment.

---

## Datasets

### 1. E-Commerce Fraud Dataset (`Fraud_Data.csv`)
- `user_id` – Unique user identifier
- `signup_time` – User registration timestamp
- `purchase_time` – Transaction timestamp
- `purchase_value` – Transaction amount
- `device_id` – Device identifier
- `source` – Traffic source (SEO, Ads, etc.)
- `browser` – Browser used
- `sex` – User gender
- `age` – User age
- `ip_address` – Transaction IP address
- `class` – Target variable (1 = Fraud, 0 = Legitimate)

### 2. IP Geolocation Dataset (`IpAddress_to_Country.csv`)
- `lower_bound_ip_address`
- `upper_bound_ip_address`
- `country`

Used to enrich transactions with geographic information.

### 3. Credit Card Dataset (`creditcard.csv`)
- `Time` – Seconds since first transaction
- `V1` to `V28` – PCA-transformed features
- `Amount` – Transaction amount
- `Class` – Target variable (1 = Fraud, 0 = Legitimate)

---

## Repository Structure

```text
fraud-detection/
├── data/                 # Ignored by git (raw & processed data)
│   ├── raw/
│   └── processed/
├── notebooks/
│   ├── eda-fraud-data.ipynb
│   ├── eda-creditcard.ipynb
│   ├── feature-engineering.ipynb
│   ├── modeling.ipynb
│   ├── shap-explainability.ipynb
│   └── README.md
├── src/
│   └── __init__.py
├── scripts/
│   └── README.md
├── models/               # Saved model artifacts
├── tests/
│   └── __init__.py
├── .github/workflows/
│   └── unittests.yml
├── .vscode/
│   └── settings.json
├── requirements.txt
├── README.md
└── .gitignore
