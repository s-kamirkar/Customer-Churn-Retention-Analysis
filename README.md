# Customer Churn & Retention Analysis

## Project Overview

This project analyzes customer churn for a telecommunications company and combines **exploratory data analysis, statistical testing, correlation analysis, and machine learning** to identify factors associated with customer churn and predict customers who may be at risk of leaving.

The project moves beyond descriptive analysis by building a **Logistic Regression model** that assigns each customer a churn probability and categorizes customers into different risk levels.

The objective is to help retention teams understand **why customers churn** and **which customers should be prioritized for retention efforts**.

---

## Business Objectives

- Identify the major factors associated with customer churn.
- Understand how customer characteristics and service choices relate to churn.
- Statistically test important relationships with churn.
- Build a machine learning model to predict customer churn.
- Evaluate the model using Accuracy, Precision, Recall, and F1 Score.
- Compare model performance against a simple majority-class baseline.
- Generate churn probabilities for individual customers.
- Segment customers into Low, Medium, and High churn-risk categories.
- Translate analytical findings into actionable retention recommendations.

---

## Dataset

The project uses the **IBM Telco Customer Churn dataset**, containing information about **7,043 customers** and 21 customer, service, billing, and churn-related attributes.

### Important Variables

- `customerID` — Unique customer identifier
- `gender` — Customer gender
- `SeniorCitizen` — Whether the customer is a senior citizen
- `Partner` — Whether the customer has a partner
- `Dependents` — Whether the customer has dependents
- `tenure` — Number of months the customer has stayed with the company
- `PhoneService` — Whether the customer has phone service
- `InternetService` — Type of internet service
- `OnlineSecurity` — Online security subscription
- `TechSupport` — Technical support subscription
- `Contract` — Contract type
- `PaymentMethod` — Payment method
- `MonthlyCharges` — Monthly customer charges
- `TotalCharges` — Total charges
- `Churn` — Whether the customer left the company

---

## Tools & Technologies

- **Python**
- **Pandas** — Data manipulation and analysis
- **NumPy** — Numerical operations
- **Matplotlib** — Data visualization
- **Seaborn** — Statistical visualization
- **SciPy** — Statistical testing
- **Scikit-learn** — Machine learning and model evaluation
- **Jupyter Notebook** — Analysis environment
- **Git & GitHub** — Version control and project management

---

## Project Workflow

The analysis follows the workflow below:

1. Data Understanding
2. Data Cleaning
3. Exploratory Data Analysis
4. Statistical Analysis
5. KPI Analysis
6. Correlation Analysis
7. Logistic Regression
8. Model Evaluation
9. Churn Driver Analysis
10. Customer Risk Segmentation
11. Business Insights & Recommendations

---

## Data Cleaning

The dataset was checked and prepared before analysis.

Key cleaning steps included:

- Checked for duplicate customer records.
- Converted `TotalCharges` into a numerical format.
- Identified missing values in `TotalCharges`.
- Missing `TotalCharges` values were replaced with `0` because the affected customers had zero tenure.
- Verified data types and dataset consistency before analysis.

---

## Exploratory Data Analysis

The analysis examined churn across several important customer characteristics.

### Churn Rate by Contract

Contract type showed a strong difference in customer churn.

- **Month-to-month:** 42.71% churn
- **One-year:** 11.27% churn
- **Two-year:** 2.83% churn

Month-to-month customers therefore represent a particularly important retention segment.

### Churn and Customer Tenure

Churned customers had substantially shorter relationships with the company.

- Median tenure of churned customers: **10 months**
- Median tenure of retained customers: **38 months**

This indicates that customers in the early stages of their relationship may require additional engagement and retention efforts.

### Churn by Internet Service

Fiber optic customers showed elevated churn.

- **Fiber optic:** 41.89% churn
- **DSL:** 18.96% churn

This makes fiber optic customers an important segment for further investigation.

### Churn by Payment Method

Customers using electronic checks showed a particularly high churn rate.

- **Electronic check:** 45.29% churn

### Monthly Charges

Churned customers had higher monthly charges than retained customers.

- Median monthly charges for churned customers: **$79.65**
- Median monthly charges for retained customers: **$64.43**

This suggests that pricing and perceived value may be relevant areas for retention analysis.

---

## Statistical Analysis

Statistical tests were performed to determine whether selected customer characteristics had statistically significant relationships with churn.

### Chi-Square Tests

Chi-square tests were used for categorical variables.

Significant associations with churn were found for:

- **Contract**
- **Payment Method**

These results support the patterns observed during exploratory analysis.

### Independent T-Test

An independent t-test was used to compare `MonthlyCharges` between churned and retained customers.

The results indicated a statistically significant difference in monthly charges between the two groups.

---

## Correlation Analysis

A correlation matrix was created for the numerical variables:

- `tenure`
- `MonthlyCharges`
- `TotalCharges`
- `Churn`

### Key Correlations

| Variable | Correlation with Churn |
|---|---:|
| Tenure | **-0.352** |
| MonthlyCharges | **+0.193** |
| TotalCharges | **-0.198** |

### Interpretation

- **Tenure** has a moderate negative correlation with churn, indicating that longer-tenure customers tend to have lower churn rates.
- **MonthlyCharges** have a weak positive correlation with churn, indicating that customers with higher monthly charges tend to show somewhat higher churn.
- **TotalCharges** have a weak negative correlation with churn.
- `tenure` and `TotalCharges` have a strong positive correlation because customers who stay longer generally accumulate higher total charges.

Correlation indicates association and should not be interpreted as proof of causation.

---

# Churn Prediction Using Logistic Regression

## Machine Learning Objective

A Logistic Regression model was developed to predict whether a customer is likely to churn.

The target variable was:

- `0` = No Churn
- `1` = Churn

### Features Used

The model uses:

- `tenure`
- `MonthlyCharges`
- `TotalCharges`
- `Contract`
- `InternetService`
- `PaymentMethod`
- `TechSupport`
- `OnlineSecurity`
- `SeniorCitizen`

Categorical variables were one-hot encoded and numerical variables were standardized.

---

## Leakage-Safe Preprocessing

The machine learning workflow uses a **Scikit-learn Pipeline and ColumnTransformer**.

The dataset was first divided into training and testing sets. Preprocessing was then learned only from the training data.

The pipeline performs:

- Standardization of numerical features
- One-hot encoding of categorical features
- Logistic Regression classification

This prevents information from the test dataset from influencing the preprocessing stage and helps avoid train/test data leakage.

---

## Train-Test Split

The dataset was divided using an **80/20 train-test split**.

- Training data: **80%**
- Test data: **20%**
- `random_state = 42`
- Stratified split was used to preserve the churn distribution.

The final test set contains **1,409 customers**.

---

## Model Evaluation

The model was evaluated using:

- Accuracy
- Precision
- Recall
- F1 Score

Because this is a customer-retention problem, identifying potential churners is particularly important.

### Final Model Performance

A **35% churn-probability threshold** was selected using validation data.

| Metric | Result |
|---|---:|
| Accuracy | **77.08%** |
| Precision | **55.19%** |
| Recall | **72.46%** |
| F1 Score | **62.66%** |

### Baseline Comparison

The majority-class baseline accuracy is **73.46%**.

The Logistic Regression model therefore improves over the baseline by **3.62 percentage points**.

This provides context for the model's accuracy rather than evaluating the 77.08% figure in isolation.

---

## Threshold Selection

Instead of automatically using the default 50% classification threshold, several probability thresholds were evaluated using validation data.

The threshold affected the balance between precision and recall.

A **35% threshold** was selected because it provided the strongest validation F1 score among the tested thresholds while maintaining relatively high recall.

For this retention use case, the threshold was chosen to **prioritize recall over precision**, because identifying more potential churners is more valuable than minimizing false alarms.

---

## Confusion Matrix

At the selected 35% threshold, the model produced the following results on the test dataset:

| | Predicted No Churn | Predicted Churn |
|---|---:|---:|
| **Actual No Churn** | 815 | 220 |
| **Actual Churn** | 103 | 271 |

This means the model correctly identified **271 actual churners**, while **103 actual churners were missed**.

The model also generated some false alarms, where customers predicted to churn ultimately did not churn.

---

# Churn Driver Analysis

The Logistic Regression coefficients were examined to understand which features were associated with higher or lower predicted churn.

### Stronger Positive Churn Associations

The model identified several features with positive coefficients, including:

- **Fiber optic internet service**
- **Electronic check payment method**
- **Higher monthly charges**
- **Senior citizen status**

Positive coefficients indicate higher predicted churn probability relative to the relevant reference category or feature scale.

### Stronger Negative Churn Associations

Features with negative coefficients included:

- **One-year contracts**
- **Two-year contracts**
- **Online security subscription**
- **Technical support subscription**
- **Longer tenure**

Negative coefficients indicate lower predicted churn probability relative to the relevant reference category or feature scale.

These coefficients represent model associations and should not be interpreted as proof that a feature directly causes churn.

---

# Customer Risk Segmentation

The model's churn probabilities were converted into three practical customer risk categories.

| Risk Category | Churn Probability |
|---|---:|
| **Low Risk** | < 35% |
| **Medium Risk** | 35% – 60% |
| **High Risk** | > 60% |

### Test Dataset Risk Distribution

| Risk Category | Customers | Share |
|---|---:|---:|
| **High Risk** | 202 | 14.3% |
| **Medium Risk** | 289 | 20.5% |
| **Low Risk** | 918 | 65.2% |
| **Total** | **1,409** | **100%** |

This segmentation allows retention teams to prioritize customers based on predicted churn risk.

---

# Key Business Findings

- **Month-to-month customers had the highest churn rate at 42.71%.**
- Churned customers had a median tenure of **10 months**, compared with **38 months** for retained customers.
- **Fiber optic customers had a churn rate of 41.89%.**
- **Electronic check users had a churn rate of 45.29%.**
- Churned customers had higher median monthly charges (**$79.65**) than retained customers (**$64.43**).
- Contract type and payment method showed statistically significant associations with churn.
- Tenure showed a negative correlation with churn.
- The Logistic Regression model achieved **72.46% recall** and **62.66% F1 Score** at the selected threshold.
- The predictive model identified **202 customers as High Risk** and **289 as Medium Risk** in the test dataset.

---

# Business Recommendations

### 1. Target Month-to-Month Customers

Offer suitable incentives, discounts, or additional benefits to encourage month-to-month customers to move to longer-term contracts.

### 2. Investigate Fiber Optic Churn

Examine pricing, service quality, customer experience, and technical support issues affecting fiber optic customers.

### 3. Review Electronic Check Users

Investigate whether payment-related friction exists and encourage convenient alternative payment methods where appropriate.

### 4. Strengthen Early Customer Engagement

Develop onboarding and engagement programs for newer customers during their initial months with the company.

### 5. Review Pricing and Perceived Value

Investigate customers with higher monthly charges and determine whether tailored plans or additional benefits could improve retention.

### 6. Prioritize High-Risk Customers

Use predicted churn probabilities to prioritize retention campaigns and allocate customer-success resources toward customers with greater predicted risk.

### 7. Use Predictions as a Prioritization Tool

Churn predictions indicate risk rather than certainty. Predictions should therefore be combined with customer context before taking retention actions.

---

# Project Structure

```text
Customer-Churn-Retention-Analysis/
│
├── data/
│   └── raw/
│       └── WA_Fn-UseC_-Telco-Customer-Churn.csv
│
├── notebooks/
│   └── 01_customer_churn_analysis.ipynb
│
├── output/
│   └── Figures/
│       ├── churn_rate_by_contract.png
│       └── churn_rate_by_payment_method.png
│
├── README.md
└── requirements.txt