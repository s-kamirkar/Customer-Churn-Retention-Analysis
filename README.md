# Customer Churn & Retention Analysis

## Project Overview

This project analyzes customer churn patterns to identify customer segments and factors associated with higher churn. The analysis combines exploratory data analysis, statistical testing, KPI analysis, and business recommendations to support customer retention strategies.

## Business Objectives

- Measure the overall customer churn rate
- Identify customer segments with higher churn
- Analyze the relationship between contract type, tenure, services, payment methods, and churn
- Evaluate differences in monthly charges between churned and retained customers
- Quantify the business impact associated with churn
- Develop data-driven customer retention recommendations

## Dataset

The project uses the **Telco Customer Churn** dataset containing customer-level information such as:

- Customer demographics
- Contract type
- Tenure
- Internet and additional services
- Payment method
- Monthly charges
- Total charges
- Churn status

**Dataset size:** 7,043 customers and 21 attributes.

## Tools & Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- SciPy
- Jupyter Notebook

## Analysis Performed

### 1. Data Cleaning

- Checked dataset structure and data types
- Identified and handled blank values in `TotalCharges`
- Converted `TotalCharges` to numeric format
- Checked for duplicate records
- Validated categorical values and whitespace inconsistencies

### 2. Exploratory Data Analysis

Analyzed churn patterns across:

- Contract type
- Customer tenure
- Monthly charges
- Internet service
- Technical support
- Payment method

### 3. Statistical Analysis

Statistical tests were performed to validate observed patterns:

- Chi-Square test — Contract Type vs Churn
- Chi-Square test — Payment Method vs Churn
- Independent two-sample t-test — Monthly Charges vs Churn

### 4. KPI Analysis

Key business metrics calculated include:

| KPI | Result |
|---|---:|
| Overall Churn Rate | 26.54% |
| Retention Rate | 73.46% |
| Average Monthly Charge | $64.76 |
| Average Customer Tenure | 32.37 months |
| Total Charges Associated with Churned Customers | $2.86M |
| Monthly Charges Associated with Churned Customers | $139.13K |

## Key Findings

- Month-to-month customers had the highest churn rate at **42.71%**.
- Churned customers had a median tenure of **10 months**, compared with **38 months** for retained customers.
- Fiber optic customers had a churn rate of **41.89%**.
- Electronic check users had the highest churn rate at **45.29%**.
- Churned customers had higher median monthly charges (**$79.65**) than retained customers (**$64.43**).
- Contract type and payment method showed statistically significant associations with churn.
- Monthly charges differed significantly between churned and retained customers.

## Business Recommendations

1. Target month-to-month customers with retention offers and incentives for longer-term contracts.
2. Strengthen onboarding and proactive support during the first year.
3. Investigate pricing, service quality, and customer experience for fiber optic customers.
4. Review the payment experience for electronic check users and encourage alternative payment methods.
5. Prioritize higher-value customers when designing retention campaigns.
6. Continuously monitor churn and retention KPIs to identify emerging patterns.

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
│
├── output/
│   └── figures/
│       ├── churn_rate_by_contract.png
│       └── churn_rate_by_payment_method.png
│
├── README.md
└── requirements.txt

## Dataset

The project uses the **Telco Customer Churn** dataset from Kaggle...