# Task 2: Credit Risk Prediction (Loan Default)

## Objective
Predict whether a loan applicant is likely to default on a loan using the Kaggle Loan Prediction Dataset.

## Approach

**Data Loading and Inspection**
- Loaded dataset with 20,000 rows and 22 columns
- No missing values or duplicates found
- Dataset is imbalanced: 79.9% paid back, 20.1% defaulted

**Feature Selection**
- Used correlation analysis for numerical columns and groupby mean for categorical columns
- Selected features: debt to income ratio, credit score, interest rate, employment status, loan amount, annual income
- Dropped weak predictors like gender, marital status, and education level

**Feature Engineering and Preprocessing**
- Applied one-hot encoding on employment status
- Applied standard scaling on numerical features

**Modeling**
- Trained Logistic Regression as baseline model
- Applied SMOTE to handle class imbalance
- Evaluated using accuracy, precision, recall, and confusion matrix
- Key metric: recall for defaulters (class 0), since missing a defaulter is more costly for the bank

## Results and Insights

- Debt to income ratio (-0.22) and credit score (0.19) are the strongest numerical predictors
- Unemployed applicants have only 18% loan payback rate, the highest default risk group
- Retired applicants almost never default (99% payback rate)
- Logistic Regression without SMOTE: accuracy 88%, defaulter recall 0.57 (too many defaulters missed)
- After applying SMOTE: defaulter recall improved to 0.72
- Trade-off: precision dropped from 0.79 to 0.52, but this is acceptable since catching defaulters is the priority
