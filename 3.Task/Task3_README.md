# Task 3: Customer Churn Prediction (Bank Customers)

## Objective
Identify which bank customers are likely to leave (churn) so the bank can take proactive steps to retain them.

## Approach

**Data Loading and Inspection**
- Loaded Churn Modelling dataset with 10,000 rows and 14 columns
- No missing values or duplicates found
- Dropped 3 identifier columns: RowNumber, CustomerId, Surname
- Dataset is imbalanced: 80% stayed, 20% churned

**Exploratory Data Analysis**
- Univariate analysis: age is right-skewed, balance shows large zero-balance group
- Bivariate analysis: churned customers are older, have higher balance, and are mostly inactive members
- Multivariate: heatmap confirmed age (0.29) and balance (0.12) are top numerical predictors

**Feature Engineering and Preprocessing**
- Applied one-hot encoding on Geography
- Applied label encoding on Gender
- Scaled Age and Balance using StandardScaler
- Selected features: Age, Balance, NumOfProducts, IsActiveMember, Geography, Gender

**Modeling**
- Trained Logistic Regression, Decision Tree, and Random Forest
- Used class weight balanced to handle class imbalance
- Key metric: recall for churned customers (class 1)
- Tested feature importance: Age, Balance, NumOfProducts are top 3 predictors

## Results and Insights

- Older customers churn more, especially those with higher balances
- 3 to 4 product customers show very high churn (suspicious pattern, possibly dissatisfied customers)
- Inactive members are significantly more likely to churn
- Germany has the highest churn rate despite having fewer customers

| Model | Recall | Accuracy | Precision |
|---|---|---|---|
| Logistic Regression | 0.73 | 0.72 | 0.39 |
| Decision Tree | 0.82 | 0.74 | 0.41 |
| Random Forest | 0.79 | 0.79 | 0.49 |

- Decision Tree is best for catching churners (highest recall 0.82)
- Random Forest gives the best overall balance between recall, precision, and accuracy
- Retraining with only Age, Balance, and NumOfProducts gave almost the same results, confirming they are the most important features
