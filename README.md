# Fraud Detection for E-Commerce and Bank Transactions

## Project Overview
This project focuses on building robust, accurate, and explainable fraud detection models for **e-commerce transactions** and **bank credit card transactions**. The solution addresses the critical challenge of **severely imbalanced data** (where fraud cases are rare) while balancing fraud prevention with customer experience.

Using advanced machine learning techniques, feature engineering, and geolocation analysis, the project aims to detect fraudulent activities effectively and provide actionable business insights.

---

## Business Context
Fraud detection systems must carefully manage a difficult trade-off:
- **Financial Loss (False Negatives)**: Every missed fraudulent transaction is a direct cost to the company.
- **Customer Friction (False Positives)**: Legitimate users flagged as fraud may stop using the platform.

This project prioritizes **Average Precision (PR-AUC)** and **F1-Score** to ensure the model is stable and reliable for real-world deployment.

---

## Technical Environment
To ensure reproducibility, this project uses a local Conda environment with specific library versions to avoid compatibility issues (specifically with NumPy 2.0).

- **Python Version**: 3.11
- **Core ML Library**: `scikit-learn==1.3.2`
- **Environment Manager**: Conda (local `.conda` prefix)
- **Dependencies**: Listed in `requirements.txt`

### Setup Instructions
```bash
# To install dependencies in your local environment
pip install -r requirements.txt
fraud-detection/
├── .conda/               # Local environment files (ignored by git)
├── data/                 # Data storage (ignored by git)
│   ├── raw/              # Original CSV files
│   └── processed/        # Model-ready data (after feature engineering)
├── notebooks/
│   ├── eda-fraud-data.ipynb
│   ├── feature-engineering.ipynb
│   └── modeling.ipynb     # Baseline comparison, Tuning, and Evaluation
├── reports/              # Visual and written analysis
│   ├── figures/          # Saved plots (PR curves, SHAP values)
│   └── summary.md        # Final model selection rationale
├── models/               # Saved .pkl or .joblib model artifacts
├── src/                  # Modular Python scripts
├── requirements.txt      # Project dependencies
├── README.md             # Project documentation
└── .gitignore            # Files to exclude from version control

Methodology & Modeling
1. Handling Imbalance
We utilized SMOTE (Synthetic Minority Over-sampling Technique) on the training data to balance the classes. This ensures the model learns the characteristics of fraudulent transactions rather than simply guessing the majority class.

2. Model Evaluation
We implemented a rigorous evaluation pipeline in modeling.ipynb:

Baseline Comparison: Logistic Regression vs. Random Forest Ensemble.

Cross-Validation: 5-Fold Stratified Cross-Validation reporting Mean and Standard Deviation to ensure model stability.

Hyperparameter Tuning: Explicit optimization using GridSearchCV to find the best n_estimators, max_depth, and min_samples_split.

3. Final Model Selection
The Random Forest Classifier was selected as the final model. It consistently outperformed the baseline in Average Precision, demonstrating a superior ability to handle non-linear relationships in transaction data.

Datasets
1. E-Commerce Fraud Dataset (Fraud_Data.csv)
Includes user registration time, purchase time, device IDs, and IP addresses. Used to calculate "time-to-purchase" and "device frequency" features.

2. IP Geolocation Dataset (IpAddress_to_Country.csv)
Used to map transaction IP addresses to specific countries, enabling geographic fraud analysis.

3. Credit Card Dataset (creditcard.csv)
Contains PCA-transformed features of bank transactions. This dataset is used to test model robustness on highly anonymized, high-dimensional data.

How to Run
Clone the repository.

Ensure your Python environment is set to 3.11.

Run notebooks/feature-engineering.ipynb to generate processed data.

Run notebooks/modeling.ipynb to train and evaluate the models.

Check reports/figures/ for performance visualizations.
---

### Final Check of the Rubric
By using this README and the code we built:
1. **Repository Organization**: You have a `reports/` folder (Check).
2. **Task 2 (Preprocessing)**: SMOTE is mentioned and visualized (Check).
3. **Task 3 (Modeling)**: GridSearchCV, Cross-Validation (Mean/Std), and Selection Rationale are all included (Check).

**Would you like me to help you create a one-paragraph "Summary Report" to put inside that new `reports/` folder?**
