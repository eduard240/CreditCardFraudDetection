# CreditCardFraudDetection

# 💳 Credit Card Fraud Detection using Random Forest

This project focuses on detecting fraudulent transactions in credit card data using the **Random Forest** algorithm, evaluated under 3 different data balancing strategies: **undersampling**, **SMOTE**, and **original imbalanced data**.

---

##  Dataset

- **Source**: [Kaggle - Credit Card Fraud Detection](https://www.kaggle.com/mlg-ulb/creditcardfraud)
- Contains **284,807 transactions** from European cardholders in 2013.
- Features `V1` to `V28` are anonymized using PCA.
- `Amount` is the transaction value.
- `Class` is the target:
  - `0 = legitimate`
  - `1 = fraud`

---

##  Project Workflow

### 1. **Exploratory Data Analysis (EDA)**
- Inspected structure, balance, and outliers
- Visualized class distribution
- Outliers were kept to preserve rare fraud cases

### 2. **Preprocessing**
- Dropped `Time` column (non-informative)
- Removed duplicates
- Stratified train-test split (80/20)
- Scaled `Amount` using `StandardScaler`

### 3. **Sampling Strategies**
- **Undersampling** – downsampled legitimate transactions to match frauds
- **SMOTE** – oversampled minority class with synthetic examples
- **Original** – trained on raw, imbalanced data (no sampling)

---

## Models: Random Forest

All experiments were done using the **RandomForestClassifier**, tested under 3 data scenarios:

### Model 1: Random Forest on Undersampled Data
- High recall (~90%) but **very low precision (~3%)**
- Too many false positives (predicts fraud too often)
- Not suitable for production

### Model 2: Random Forest on SMOTE Data
- Balanced results
- Precision ~81%, Recall ~88%, F1-score ~85%
- Best balance between catching fraud and avoiding false alarms

### Model 3: Random Forest on Original Data (No Sampling)
- Precision ~97%, Recall ~76%, F1-score ~85%
- Surprisingly strong results due to well-separated features (PCA)

---

## Evaluation Metrics

- **Confusion Matrix**
- **Precision / Recall / F1-score**
- Focused analysis on:
  - **TP (True Positives)**: caught frauds
  - **FP (False Positives)**: legitimate flagged as fraud (bad for users)
  - **FN (False Negatives)**: missed frauds (dangerous for the bank)

---

## Key Insights

- **SMOTE and Original data performed best**
- **Undersampling severely degraded precision**
- Random Forest can perform well even on imbalanced data if features are clean and well-separated
- In fraud detection, **minimizing False Negatives (FN)** is often prioritized over avoiding False Positives (FP)

---

## Author

Project built by [Your Name], focusing on practical and explainable fraud detection with tree-based models.
