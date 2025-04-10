# Customer Churn Analysis

In this project, I analyzed customer churn for a telecom company using a dataset containing customer demographics, subscription details, and service usage information. My goal was to identify patterns and key factors that influence customer churn.

## Dataset Overview

The dataset contains the following key features:

- **customerID**: A unique identifier for each customer.
- **gender**: The gender of the customer.
- **SeniorCitizen**: Indicates whether the customer is a senior citizen (1 = Yes, 0 = No).
- **Partner**: Whether the customer has a partner (Yes/No).
- **Dependents**: Whether the customer has dependents (Yes/No).
- **tenure**: The number of months the customer has been with the company.
- **PhoneService, MultipleLines**: Whether the customer has phone service or multiple lines.
- **InternetService**: Type of internet service (DSL/Fiber optic/No).
- **OnlineSecurity, DeviceProtection, TechSupport, StreamingTV, StreamingMovies**: Various additional services customers may have.
- **Contract**: Type of contract (Month-to-month/One year/Two year).
- **PaperlessBilling**: Whether the customer uses paperless billing (Yes/No).
- **PaymentMethod**: The method of payment (e.g., Electronic check, Mailed check).
- **MonthlyCharges, TotalCharges**: The customer's monthly charges and the total amount they have paid.
- **Churn**: Whether the customer churned (Yes/No).

## Exploratory Data Analysis (EDA) Process

### 1. **Understanding the Distribution of Key Variables**

The first step was to analyze the distribution of key variables in the dataset:
![](https://github.com/Ftsem/CustomerChurn-Python/blob/fdc5c8933b444c99139aed54837fc3845deca096/Assets/Screenshot%202025-04-10%20110147.png)
- **Churn**: The target variable was highly imbalanced. There were 5174 customers who did not churn (No), and 1869 customers who churned (Yes). This imbalance needed to be addressed in the modeling phase.


- **Numerical Variables**: Features such as **tenure**, **MonthlyCharges**, and **TotalCharges** were explored.
    - **Tenure**: Customers with short tenures seemed to be more likely to churn.
    - **MonthlyCharges**: Higher charges were associated with a higher likelihood of churn.
    - **TotalCharges**: Correlated with tenure, suggesting that longer-tenured customers tended to have higher total charges.

![](https://github.com/Ftsem/CustomerChurn-Python/blob/e90436502e39ea7ad5f50dee2bd1a1cd60582e19/Assets/Screenshot%202025-04-10%20110157.png)

### 2. **Univariate Analysis**

The distributions of **MonthlyCharges**, **TotalCharges**, and **Tenure** were visualized to understand their behavior. I also visualized the **Churn** distribution.

For categorical variables, I examined the counts of each category (e.g., **Contract** type, **PaymentMethod**, **Partner** status) to understand their relationship to churn.

!([]https://github.com/Ftsem/CustomerChurn-Python/blob/290ee2dbbdcafce4060f152d5839a2469def3521/Assets/Screenshot%202025-04-10%20110205.png)
### 3. **Bivariate Analysis: Churn vs. Key Features**

I explored how different features related to churn:

- **Churn vs. Tenure**: Customers who churned tended to have shorter tenures.
- **Churn vs. Monthly Charges**: Churned customers typically had higher monthly charges.
- **Churn vs. Total Charges**: Churned customers had lower total charges, suggesting shorter tenures.

#### Visualizing Churn by Contract, Payment Method, Partner, and Dependents:

![Churn vs. Contract](path_to_image/Churn_vs_Contract.png)

The images above show how different features such as **Contract** type, **PaymentMethod**, **Partner**, and **Dependents** affect churn rates.

### 4. **Correlation and Feature Importance**

To better understand which features had the strongest relationship with churn, I calculated the correlation matrix for the numerical features and visualized it using heatmaps. The correlations helped pinpoint which features were most closely linked to churn.

Some notable correlations:
- **Tenure** and **Total Charges** were positively correlated, indicating that customers with longer tenures tend to have higher total charges.
- **Monthly Charges** had a moderate correlation with churn, with higher charges being linked to a higher likelihood of churn.

Feature importance was also explored using tree-based models, which helped identify which features were the most important predictors of churn.

## Insights and Recommendations

Based on my analysis, I derived several actionable insights:

1. **Reduce Churn for Month-to-Month Contracts**:
   - **Observation**: Customers with Month-to-month contracts had significantly higher churn rates.
   - **Recommendation**: Encourage customers on Month-to-month contracts to switch to longer-term contracts (one or two years) through incentives like discounts or exclusive benefits. This would likely help reduce churn.

2. **Target Higher-Paying Customers**:
   - **Observation**: Higher-paying customers were more likely to churn.
   - **Recommendation**: Investigate why higher-paying customers are churning. Are they dissatisfied with the service? Offering personalized customer service or retention efforts like discounts or loyalty programs could be beneficial.

3. **Leverage Long Tenure**:
   - **Observation**: Longer-tenured customers were less likely to churn.
   - **Recommendation**: Implement a loyalty program to reward long-tenured customers with exclusive perks or discounts. Additionally, monitor customers with shorter tenures and provide them with incentives to stay longer (e.g., discounts after 6 or 12 months).

4. **Encourage Long-Term Contracts**:
   - **Observation**: Customers on longer contracts (One year or Two years) are less likely to churn.
   - **Recommendation**: Offer promotions or discounts to encourage new customers to sign longer-term contracts. For existing month-to-month customers, create offers to transition them to longer-term contracts, emphasizing the benefits of staying longer.

5. **Target Non-Partner/Non-Dependent Customers**:
   - **Observation**: Customers without partners or dependents tend to churn more.
   - **Recommendation**: Target customers without partners or dependents with personalized retention strategies such as offering more engaging services, loyalty programs, or family-oriented plans. These individuals may need extra motivation to stay.

6. **Investigate Payment Method Issues**:
   - **Observation**: Customers using **Electronic check** have higher churn rates compared to those using other payment methods.
   - **Recommendation**: Investigate the reasons why electronic check users are churning more. This could be related to payment convenience or dissatisfaction with the service. Offering alternative, more convenient digital payment methods (e.g., mobile wallets, credit/debit cards) might help reduce churn.

7. **Enhance Service Offering for Customers Without Premium Services**:
   - **Observation**: Customers without premium services like **TechSupport** or **InternetService** are more likely to churn.
   - **Recommendation**: Provide attractive bundles for customers who are not subscribed to additional services. For example, customers without **TechSupport** could be offered discounted prices for adding this service. Similarly, those without **InternetService** could be targeted with discounted internet packages.

8. **Personalized Retention for Early-Stage Customers**:
   - **Observation**: New customers (with shorter tenures) are at higher risk of churning.
   - **Recommendation**: Implement personalized retention campaigns for new customers (those with a tenure of 1-6 months). These campaigns could include loyalty rewards, discounts, or exclusive offers to strengthen their connection with the company early on.

9. **Monitor High-Risk Groups**:
   - **Observation**: Features like **Tenure** and **Contract Type** heavily influence churn.
   - **Recommendation**: Use predictive analytics to identify high-risk customers (e.g., those with low tenure or month-to-month contracts) and implement targeted retention strategies. These could include proactive outreach by customer service teams, personalized offers, or special discounts to retain these customers.

