# Customer Churn & Retention Analysis

## Project Overview

This project analyzes customer churn patterns and builds a predictive model to identify customers who are at higher risk of leaving.

The analysis combines:

- Data cleaning and exploratory data analysis
- Statistical hypothesis testing
- Correlation analysis
- Logistic regression
- Churn probability prediction
- Customer risk segmentation
- Business-focused retention recommendations

The goal is to move from simply understanding **why customers churn** to identifying **which customers are most at risk of churn** so that retention strategies can be targeted effectively.

---

## Business Objectives

- Measure overall customer churn and retention
- Identify customer segments with higher churn rates
- Analyze factors associated with customer churn
- Statistically validate important churn relationships
- Build a machine learning model to predict churn
- Estimate individual customer churn probability
- Segment customers into Low, Medium, and High risk categories
- Translate analytical findings into actionable retention strategies

---

## Dataset

The project uses the **Telco Customer Churn** dataset containing customer-level information such as:

- Customer demographics
- Contract type
- Tenure
- Internet service
- Additional services
- Payment method
- Monthly charges
- Total charges
- Churn status

**Dataset size:** 7,043 customers and 21 attributes

---

## Tools & Technologies

- **Python**
- **Pandas**
- **NumPy**
- **Matplotlib**
- **Seaborn**
- **SciPy**
- **Scikit-learn**
- **Jupyter Notebook**
- **Git & GitHub**

---

## Analysis Performed

### 1. Data Cleaning

- Checked dataset structure and data types
- Identified and handled blank values in `TotalCharges`
- Converted `TotalCharges` to numeric format
- Checked for duplicate records
- Validated categorical variables

### 2. Exploratory Data Analysis

Analyzed churn patterns across:

- Contract type
- Customer tenure
- Monthly charges
- Internet service
- Technical support
- Online security
- Payment method

### 3. Statistical Analysis

Statistical tests were performed to validate observed patterns:

- Chi-Square test — Contract Type vs Churn
- Chi-Square test — Payment Method vs Churn
- Independent two-sample t-test — Monthly Charges vs Churn

### 4. Correlation Analysis

Correlation analysis was performed between numerical variables and churn.

Key observations:

- Tenure showed a negative relationship with churn.
- Monthly charges showed a positive relationship with churn.
- Tenure and total charges showed a strong positive relationship.

Correlation was used to identify relationships between variables and does not imply causation.

---

## 5. Churn Prediction — Logistic Regression

A Logistic Regression model was developed to predict customer churn.

### Features Used

- Tenure
- Monthly Charges
- Total Charges
- Contract
- Internet Service
- Payment Method
- Tech Support
- Online Security
- Senior Citizen

Categorical variables were converted into numerical features using one-hot encoding.

The dataset was divided into:

- **80% training data**
- **20% test data**

### Model Evaluation

The model was evaluated using:

- Accuracy
- Precision
- Recall
- F1 Score
- Confusion Matrix

A probability threshold of **0.35** was selected using validation data to improve the model's ability to identify potential churners.

### Final Test Performance

| Metric | Result |
|---|---:|
| Accuracy | 77.15% |
| Precision | 55.31% |
| Recall | 72.46% |
| F1 Score | 62.73% |

The 0.35 threshold prioritizes identifying more potential churners, making recall particularly relevant for a customer-retention use case.

---

## 6. Churn Driver Analysis

Logistic regression coefficients were analyzed to identify features associated with higher or lower predicted churn.

### Stronger Positive Churn Associations

- Fiber optic internet service
- Electronic check payment method
- Senior citizen status

### Stronger Negative Churn Associations

- Two-year contracts
- One-year contracts
- Online security
- Tech support

These coefficients represent model associations and should not be interpreted as proof of causation.

---

## 7. Customer Risk Segmentation

The model's churn probabilities were converted into three practical risk categories:

| Risk Category | Churn Probability |
|---|---:|
| Low Risk | < 35% |
| Medium Risk | 35% – 60% |
| High Risk | > 60% |

### Test Dataset Risk Distribution

| Risk Category | Customers | Share |
|---|---:|---:|
| Low Risk | 919 | 65.2% |
| Medium Risk | 287 | 20.4% |
| High Risk | 203 | 14.4% |
| **Total** | **1,409** | **100%** |

This segmentation allows retention teams to prioritize customers based on predicted churn risk.

---

## Key Business Findings

- Month-to-month customers had the highest churn rate at **42.71%**.
- Churned customers had a median tenure of **10 months**, compared with **38 months** for retained customers.
- Fiber optic customers had a churn rate of **41.89%**.
- Electronic check users had the highest churn rate at **45.29%**.
- Churned customers had higher median monthly charges (**$79.65**) than retained customers (**$64.43**).
- Contract type and payment method showed statistically significant associations with churn.
- Monthly charges differed significantly between churned and retained customers.
- The predictive model identified **203 customers as High Risk** and **287 as Medium Risk** in the test dataset.

---

## Business Recommendations

1. **Reduce month-to-month churn**
   - Encourage customers to move toward longer-term contracts through targeted incentives.

2. **Strengthen early customer retention**
   - Focus onboarding and proactive engagement efforts on newer customers.

3. **Investigate fiber optic churn**
   - Analyze pricing, service quality, and customer experience among fiber optic customers.

4. **Improve payment experience**
   - Investigate the high churn associated with electronic check payments and encourage alternative payment methods where appropriate.

5. **Prioritize high-risk customers**
   - Use predicted churn probabilities to focus retention campaigns on customers most likely to leave.

6. **Use targeted retention strategies**
   - Combine customer risk scores with contract type, tenure, service usage, and charges to design more personalized interventions.

---

## Project Structure

```text
IBM_CUSTOMER_CHURN/
│
├── data/
│   └── raw/
│       └── WA_Fn-UseC_-Telco-Customer-Churn.csv
│
├── notebooks/
│   └── 01_customer_churn_analysis.ipynb
├── output/
│   └── Figures/
│       ├── churn_rate_by_contract.png
│       └── churn_rate_by_payment_method.png
│
├── README.md
└── requirements.txt