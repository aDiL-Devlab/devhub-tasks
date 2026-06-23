# Task 4: Predicting Medical Insurance Charges

## Objective
Estimate the medical insurance charge for an individual based on personal data like age, BMI, and smoking status.

## Approach

**Data Loading and Inspection**
- Loaded Medical Cost Personal dataset with 1,338 rows and 7 columns
- Found and removed 1 duplicate row
- No missing values found
- Charges are highly right-skewed with max value of 63,770

**Feature Engineering**
- Created a BMI category feature: Underweight, Normal, Overweight, Obese
- Created a smoker times BMI interaction feature after discovering that smoking combined with high BMI causes dramatically higher charges
- This interaction feature was the key improvement in model performance

**Preprocessing**
- Applied label encoding on smoker column (yes/no)
- Applied one-hot encoding on region column
- Scaled age and BMI using StandardScaler

**Modeling**
- Trained Linear Regression model
- First without interaction feature, then added smoker times BMI
- Evaluated using MAE, RMSE, and R2 score
- Key metric: RMSE, since large prediction errors are very costly for insurance companies

## Results and Insights

- Smoker status is the strongest predictor (correlation 0.79 with charges)
- Age (0.30) and BMI (0.20) are the next strongest predictors
- Scatter plot revealed an interaction effect: smoker with BMI above 30 causes dramatically higher charges
- Non-smokers show a gradual linear increase in charges with age

| Model | R2 Score | RMSE | MAE Percentage |
|---|---|---|---|
| Without interaction feature | 0.81 | 5,957 | 29.3% |
| With smoker times BMI feature | 0.89 | 4,560 | 19.6% |

- Adding one interaction feature improved R2 from 0.81 to 0.89
- RMSE dropped from 5,957 to 4,560 showing fewer large prediction errors
- This shows that understanding domain patterns (smoking plus obesity) matters more than adding more features
