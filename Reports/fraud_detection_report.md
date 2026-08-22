# Caishen Bank Fraud Detection Project

## 1. Business Problem

Caishen Bank is looking to identify fraudulent activity within customer-facing bank accounts. The goal of this project is to develop a machine learning model that can identify potentially fraudulent transactions and support the bank's fraud detection efforts.

The objective of this project is to create a minimum viable product (MVP) using historical transaction data. The final solution uses an ensemble classification model to predict whether a transaction is fraudulent.

---

## 2. Dataset

The dataset contains 6,362,620 financial transactions.

The target variable is whether a transaction was fraudulent.

The transaction types include:

- CASH_OUT
- PAYMENT
- CASH_IN
- TRANSFER
- DEBIT

The dataset is highly imbalanced because fraudulent transactions represent a very small portion of all transactions.

The transaction counts by type were:

| Transaction Type | Count |
|---|---:|
| CASH_OUT | 2,237,500 |
| PAYMENT | 2,151,495 |
| CASH_IN | 1,399,284 |
| TRANSFER | 532,909 |
| DEBIT | 41,432 |

---

## 3. Initial Exploratory Data Analysis

Initial exploratory data analysis (EDA) was performed to understand the structure of the dataset and identify patterns that could help detect fraudulent transactions.

The analysis examined:

- Transaction types
- Transaction amounts
- Account balances
- Changes in account balances
- Fraudulent versus non-fraudulent transactions
- Relationships between transaction amounts and account balances

The analysis showed that the dataset was highly imbalanced, with legitimate transactions greatly outnumbering fraudulent transactions.

Because of this imbalance, accuracy alone was not considered an appropriate measure of model performance. Precision, recall, F1-score, the confusion matrix, and ROC-AUC were also evaluated.

---

## 4. Data Cleaning and Preprocessing

The data was cleaned and prepared for machine learning.

Additional features were created to capture relationships between transaction amounts and account balances, including:

- `balance_change`
- `balance_error`

The categorical `type` variable was converted into numerical features using one-hot encoding.

The final modeling dataset contained 12 features.

The dataset was divided into training and testing sets using a stratified split.

### Training Set

5,090,096 transactions

### Testing Set

1,272,524 transactions

Stratification was used to maintain the proportion of fraudulent transactions in both the training and testing datasets.

---

## 5. Baseline Model: Logistic Regression

A Logistic Regression model was developed as a baseline classification model.

Because fraudulent transactions were heavily underrepresented, balanced class weights were used to give additional importance to the minority fraud class.

The Logistic Regression model achieved:

**ROC-AUC: 0.9874**

The model demonstrated strong overall discrimination between fraudulent and legitimate transactions. However, the severe class imbalance made fraud detection particularly challenging.

The Logistic Regression model provided a useful baseline for comparison with the ensemble model.

---

## 6. Ensemble Model: Random Forest

A Random Forest classifier was developed as the required ensemble classification model.

Random Forest combines multiple decision trees to make predictions. Each decision tree evaluates patterns in the transaction data, and the trees work together to produce the final classification.

The initial Random Forest model achieved:

**ROC-AUC: 0.9996**

The initial model's fraud-class results were:

| Metric | Fraud Class |
|---|---:|
| Precision | 0.97 |
| Recall | 1.00 |
| F1-score | 0.98 |

The confusion matrix showed:

- 1,270,829 legitimate transactions correctly classified
- 49,178 legitimate transactions incorrectly classified as fraudulent
- 1,515 fraudulent transactions correctly classified
- 128 fraudulent transactions missed

The initial Random Forest demonstrated a substantial improvement over the Logistic Regression baseline.

---

## 7. Hyperparameter Tuning

Hyperparameter tuning was performed to identify an effective Random Forest configuration.

Because the full dataset contained more than six million transactions, a representative sample of 200,000 transactions was used for hyperparameter tuning to reduce computational time.

The tuning sample contained 215 fraudulent transactions.

Three-fold cross-validation was performed across six parameter combinations.

The best parameters were:

```text
n_estimators: 50
max_depth: 20
min_samples_split: 2
min_samples_leaf: 1