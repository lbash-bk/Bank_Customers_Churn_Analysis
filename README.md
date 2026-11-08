# Bank Customer Churn Analysis

An end-to-end data analytics project investigating customer churn patterns in a banking dataset using Python and Microsoft Power BI.

## Project Overview

Customer churn occurs when customers discontinue their relationship with a business. For banks, understanding why customers leave is important for improving customer retention and maintaining long-term business relationships.

This project explores customer churn using demographic, geographic, and account-related information. Python was used for data cleaning and exploratory data analysis (EDA), while Power BI was used to develop an interactive dashboard for communicating key findings.

The objective was to identify customer segments with relatively high churn rates, understand patterns associated with customer departures, and provide actionable business recommendations.

## Project Objectives

- Analyse the bank's overall customer churn rate.
- Identify geographic and demographic patterns associated with churn.
- Examine the relationship between customer activity and churn.
- Investigate churn across different numbers of bank products.
- Compare account balances between retained and churned customers.
- Build an interactive Power BI dashboard.
- Provide data-driven recommendations to support customer retention.

## Tools and Technologies

| Tool | Purpose |
|---|---|
| Python | Data cleaning and analysis |
| Pandas | Data manipulation and analysis |
| NumPy | Numerical operations |
| Jupyter Notebook | Exploratory data analysis |
| Microsoft Power BI | Dashboard development |
| DAX | Measures and calculated columns |
| Excel / CSV | Data inspection and storage |

## Dataset

The original dataset consisted of two worksheets:

1. Customer Info
2. Account Info

The worksheets were cleaned and merged using `CustomerId`.

**Final dataset:**
- 10,000 customer records
- 13 columns

### Key Variables

| Variable | Description |
|---|---|
| CustomerId | Unique customer identifier |
| CreditScore | Customer credit score |
| Geography | Customer's country |
| Gender | Customer gender |
| Age | Customer age |
| Tenure | Number of years with the bank |
| Balance | Customer account balance |
| NumOfProducts | Number of bank products held |
| HasCrCard | Credit card ownership (1 = Yes, 0 = No) |
| IsActiveMember | Membership activity (1 = Active, 0 = Inactive) |
| EstimatedSalary | Estimated customer salary |
| Exited | Customer churn indicator (1 = Churned, 0 = Retained) |

## Data Cleaning and Preparation

Data cleaning and preparation were performed using Python and Pandas.

The main steps included:

1. Loaded and inspected both Excel worksheets.
2. Examined data types, missing values, duplicates, and inconsistent entries.
3. Removed duplicate records and duplicate customer identifiers.
4. Replaced missing surnames with `Unknown`.
5. Imputed missing Age values using the median.
6. Cleaned EstimatedSalary by removing currency symbols and commas.
7. Replaced invalid `-999999` salary placeholders with missing values and imputed them using the median.
8. Standardized Geography values into France, Germany, and Spain.
9. Converted Balance and EstimatedSalary to numeric data types.
10. Converted HasCrCard and IsActiveMember into binary indicators.
11. Checked and retained a single Tenure column.
12. Merged the two datasets using CustomerId.
13. Exported the final cleaned dataset as `bank_churn_cleaned.csv`.

## Exploratory Data Analysis

Exploratory data analysis was performed in four stages.

### 1. Univariate Analysis

Examined individual variables to understand the distribution of customers.

Key observations:
- France represented 50.14% of customers.
- Germany represented 25.09%.
- Spain represented 24.77%.
- Male customers represented 54.57% of the dataset.
- Approximately 70.55% of customers had a credit card.
- Approximately 51.51% were active members.

**Overall Customer Churn**

| Customer Status | Number of Customers | Percentage |
|---|---:|---:|
| Retained | 7,963 | 79.63% |
| Churned | 2,037 | 20.37% |
| Total | 10,000 | 100% |

### 2. Bivariate Analysis

Examined relationships between customer characteristics and churn.

**Churn by Geography**

| Geography | Churned Customers | Churn Rate |
|---|---:|---:|
| France | 810 | 16.15% |
| Germany | 814 | 32.44% |
| Spain | 413 | 16.67% |

**Churn by Gender**

| Gender | Churn Rate |
|---|---:|
| Female | 25.07% |
| Male | 16.46% |

**Churn by Age Group**

| Age Group | Churn Rate |
|---|---:|
| 18–25 | 7.53% |
| 26–35 | 8.50% |
| 36–45 | 19.62% |
| 46–55 | 50.57% |
| 56–65 | 48.32% |
| 66+ | 13.26% |

**Churn by Membership Status**

| Membership Status | Churn Rate |
|---|---:|
| Active | 14.27% |
| Inactive | 26.85% |

**Churn by Number of Products**

| Number of Products | Churn Rate |
|---|---:|
| 1 | 27.71% |
| 2 | 7.58% |
| 3 | 82.71% |
| 4 | 100% |

The three- and four-product categories had relatively small sample sizes, so their high churn rates require cautious interpretation.

### 3. Multivariate Analysis

Investigated combinations of customer characteristics to identify more detailed patterns.

Key observations:
- Germany recorded higher churn rates across male and female customer segments.
- Female customers had higher churn rates than male customers across all three countries.
- Inactive members generally recorded higher churn rates across geographic and age groups.
- Customers aged 46–55 and 56–65 showed particularly high churn rates.
- Customers holding three products recorded high churn rates across all three countries.

### 4. Correlation Analysis

Correlation analysis examined linear relationships between numerical variables and the churn indicator.

| Variable | Correlation with Churn |
|---|---:|
| Age | +0.285 |
| Balance | +0.119 |
| IsActiveMember | -0.156 |
| CreditScore | -0.027 |
| NumOfProducts | -0.048 |
| EstimatedSalary | +0.012 |
| Tenure | -0.014 |
| HasCrCard | -0.007 |

Age had the strongest positive linear correlation with churn among the listed characteristics. Active membership had a negative correlation with churn.

Correlation does not establish causation, and linear correlation may not capture all category-based or nonlinear patterns.

## Power BI Dashboard

An interactive dashboard was developed using Microsoft Power BI. It consists of two report pages.

### Page 1: Customer Churn Overview

Provides a high-level view of customer retention and churn.

**Key components:**
- Total Customers
- Churned Customers
- Retained Customers
- Churn Rate
- Retention Rate
- Churned Customers by Geography
- Churn Rate by Geography
- Churn Rate by Gender
- Churn Rate by Age Group
- Churn Rate by Active Membership Status

![Customer Churn Overview](screenshots/churn_overview.png)

### Page 2: Customer Behaviour and Churn Drivers

Explores customer characteristics and their relationship with churn.

**Key components:**
- Churn Rate by Number of Products
- Average Customer Balance by Churn Status
- Churned Customers by Geography and Gender
- Customer Distribution by Geography
- Churn Rate by Credit Card Ownership

![Customer Behaviour and Churn Drivers](screenshots/customer_behaviour.png)

The dashboard includes interactive slicers for exploring customer segments by geography, gender, age group, and membership status.

## Key Findings

The analysis revealed the following:

1. **Overall churn:** 2,037 customers had exited, representing 20.37% of the customer base.
2. **Geographic differences:** Germany had the highest churn rate at 32.44%.
3. **Age-related patterns:** Customers aged 46–55 and 56–65 recorded the highest churn rates.
4. **Gender differences:** Female customers had a higher churn rate (25.07%) than male customers (16.46%).
5. **Customer engagement:** Inactive members had a churn rate of 26.85%, compared with 14.27% among active members.
6. **Product ownership:** Customers with three or four products had unusually high churn rates, although these groups were small.
7. **Account balance:** Churned customers had a higher average balance (91,108.54) than retained customers (72,745.30).
8. **Credit card ownership:** Customers with and without credit cards had very similar churn rates.

## Business Insights and Recommendations

Based on the findings, the following recommendations are proposed:

### 1. Investigate Customer Churn in Germany
The bank should investigate regional differences in customer experience, service quality, product suitability, and customer satisfaction.

### 2. Improve Customer Engagement
Inactive customers should be monitored, with targeted engagement programmes designed to improve their banking activity and overall experience.

### 3. Focus on High-Churn Age Groups
The bank should investigate the needs of customers aged 46–65 and assess whether existing products and services meet their expectations.

### 4. Review Multi-Product Customer Experiences
The bank should investigate why customers holding three or four products have unusually high churn rates before making decisions about product bundling or sales strategies.

### 5. Monitor High-Balance Customer Exits
Further investigation should establish the financial importance of customers who leave with relatively high account balances.

### 6. Establish Continuous Churn Monitoring
The bank should regularly monitor churn rate, retention rate, customer activity, and geographic performance through an updated dashboard.

These recommendations are based on observed patterns and should be validated through further investigation and measured retention initiatives.

## Limitations and Future Work

This project focuses on descriptive analytics and does not establish the causes of customer churn.

Limitations include:
- Some customer segments, particularly customers with three or four products, have relatively small sample sizes.
- Median imputation may affect the distribution of selected numerical variables.
- The dataset does not contain detailed customer feedback or reasons for account closure.
- Correlation analysis captures linear relationships and may not represent more complex patterns.
- Statistical significance testing and predictive modelling were not included.

**Potential future improvements:**
- Perform statistical hypothesis testing.
- Develop customer segmentation models.
- Build a machine-learning model to predict customer churn.
- Evaluate model performance and identify important churn predictors.
- Explore deployment of a churn prediction model as a software product.

## Conclusion

This project demonstrated how Python and Microsoft Power BI can be used together to transform raw banking data into meaningful business insights.

Through data cleaning, exploratory data analysis, and interactive visualization, the project identified important customer segments and characteristics associated with higher churn rates.

The findings highlight the importance of geographic performance, customer engagement, age-related patterns, and product ownership when investigating customer retention.

The completed dashboard provides an interactive platform for exploring these patterns and supports more informed customer retention decisions.

Overall, the project strengthened practical skills in data cleaning, exploratory data analysis, descriptive statistics, DAX, data visualization, and business insight communication.

---

**Project Category:** Data Analytics

**Dataset Size:** 10,000 records × 13 columns

**Tools:** Python, Pandas, NumPy, Jupyter Notebook, Microsoft Power BI, DAX

**Dashboard:** Two interactive report pages
