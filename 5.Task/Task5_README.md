# Task 5: Bank Marketing Campaign (Loan Acceptance Prediction)

## Objective
Predict which customers are likely to accept a personal loan offer so the bank can run a more targeted and cost-effective marketing campaign instead of contacting every customer.

## Approach

**Data Loading and Inspection**
- Loaded Bank Marketing dataset with 45,211 rows and 17 columns
- No missing values or duplicates found
- Some columns like job and education contained "unknown" values acting as hidden missing data
- Renamed target column y to loan accepted for clarity
- Target variable is highly imbalanced: only 11.7% accepted the loan

**Exploratory Data Analysis**
- Univariate: age peaks between 30 and 45, balance is highly right-skewed, duration is right-skewed
- Bivariate: longer call duration strongly linked to acceptance, debt-free customers more likely to accept, May is peak month
- Multivariate: heatmap showed duration (0.39) is the strongest numerical predictor

**Feature Engineering and Preprocessing**
- Applied label encoding on binary columns: loan, default, housing
- Applied one-hot encoding on multi-category columns: job, marital, education, contact, month, poutcome
- Used Random Forest feature importance to select top 15 features
- Top features: duration, balance, age, day, poutcome success, pdays, campaign
- Scaled age, balance, and duration using StandardScaler

**Modeling**
- Trained Logistic Regression, Decision Tree, and Random Forest
- Used class weight balanced to handle class imbalance
- Key metric: recall, since missing a potential loan buyer costs the bank more than making an extra call

## Results and Insights

- Call duration is the most important feature: customers who accept spend significantly more time on the call
- Customers with no credit default and no existing loans are most likely to accept
- High balance customers surprisingly rarely accept loan offers
- Previous campaign success (poutcome success) is a strong signal for acceptance
- May, June, July, and August are the best months for marketing campaigns

| Model | Recall | Accuracy | Precision |
|---|---|---|---|
| Logistic Regression | 0.79 | 0.83 | 0.40 |
| Decision Tree | 0.80 | 0.80 | 0.36 |
| Random Forest | 0.84 | 0.79 | 0.35 |

- Random Forest is the best model, capturing 920 out of 1,091 actual loan acceptors
- The trade-off is lower precision (0.35), meaning some non-acceptors will also be contacted
- This is an acceptable trade-off since the cost of an extra marketing call is much lower than the revenue lost from missing a real buyer
