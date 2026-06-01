# Customer Churn Prediction Analysis

## Project Overview
This project aims to analyze customer data and build a predictive machine learning model to identify customers who are likely to churn (leave the service). By understanding the key drivers of customer churn, the business can take proactive measures to improve retention, optimize pricing, and enhance customer satisfaction.

## Dataset
The analysis is based on a customer dataset (`CustomerChurn.csv`). The target variable is `Churn` (Yes/No), which indicates whether a customer has left within the last month. The dataset includes demographic information, account information (e.g., tenure, contract type, payment method), and services signed up for.

## Workflow

### 1. Data Cleaning & Preprocessing
- **Missing Values:** Addressed missing values in the `TotalCharges` column by converting it to numeric and filling nulls with the median.
- **Feature Selection:** Dropped the `customerID` column as it does not hold predictive power.
- **Encoding:** 
  - Mapped the target variable `Churn` to binary numerical values (1 for Yes, 0 for No).
  - Applied One-Hot Encoding (`pd.get_dummies`) to convert the remaining categorical variables into machine-readable numeric formats.

### 2. Exploratory Data Analysis (EDA)
Visualized key relationships in the data to uncover initial insights:
- **Churn Distribution:** Evaluated the baseline churn rate.
- **Contract Type:** Discovered that month-to-month contracts have a significantly higher churn rate compared to one or two-year contracts.
- **Monthly Charges:** Found that customers who churn tend to have higher median monthly charges.

### 3. Model Building
The data was split into an 80/20 train-test set to evaluate model generalizability. Two main algorithms were tested:
- **Logistic Regression:** Used as a baseline classification model.
- **Random Forest Classifier:** An ensemble learning method used to capture complex, non-linear relationships in the customer data.

### 4. Hyperparameter Tuning
To optimize the Random Forest model's performance, **Grid Search Cross-Validation (GridSearchCV)** was utilized. It tested combinations of hyperparameters including:
- `n_estimators` (Number of trees)
- `max_depth` (Maximum depth of trees)
- `min_samples_split` & `min_samples_leaf`

### 5. Feature Importance
The best-performing Random Forest model was used to rank feature importances. Variables such as `TotalCharges`, `MonthlyCharges`, and `Tenure` were identified as the strongest predictors of churn.

## Key Findings and Recommendations
- **Incentivize Long-term Contracts:** Month-to-month customers are at the highest risk. Offering discounts for upgrading to annual contracts could improve retention.
- **Targeted Retention Campaigns:** Utilize the model's predictions to identify the most at-risk customers and offer personalized interventions (special offers, proactive support).
- **Review Pricing Strategies:** Given that higher monthly charges correlate with higher churn, consider introducing tiered pricing options offering better perceived value.
