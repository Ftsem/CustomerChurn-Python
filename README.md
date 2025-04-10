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
#### Observations
The Churn column is imbalanced, with 5174 non-churned customers and only 1869 churned customers. This indicates that the company has a higher retention rate, but the imbalance should be taken into account during model training.

### 2. ** Visualizing Numerical Features Distribution**
![](https://github.com/Ftsem/CustomerChurn-Python/blob/81e8068283040ea5b9746226d637ea19abf2fff3/Assets/Screenshot%202025-04-10%20110157.png)
#### Observations
Tenure: The distribution of tenure shows that most customers have been with the company for a relatively short period (less than 20 months). This suggests a significant portion of customers have only recently started using the service, which might be a risk for churn.

Monthly Charges: There’s a moderate spread in monthly charges, with a concentration in the mid-range ($20 to $80).

Total Charges: The TotalCharges feature has a skewed distribution, with the majority of customers having paid lower total charges, possibly indicating that newer customers tend to churn before accumulating higher charges.

### 3. ** Churn vs Numerical Features **
![](https://github.com/Ftsem/CustomerChurn-Python/blob/81e8068283040ea5b9746226d637ea19abf2fff3/Assets/Screenshot%202025-04-10%20110205.png)
#### Observations
Churn vs Tenure: Customers who churn tend to have shorter tenures. The median tenure for churned customers is significantly lower compared to non-churned customers, which suggests that new customers have a higher likelihood of churning.

Churn vs Monthly Charges: There’s a notable difference in the distribution of monthly charges between churned and non-churned customers. Customers who churn tend to have slightly higher monthly charges. This could imply that customers on more expensive plans are either dissatisfied or financially constrained.

Churn vs Total Charges: Similar to the tenure variable, churned customers have lower total charges, further confirming that new customers (with lower charges) are more likely to churn.

### 4. **  Churn vs Categorical Features **
![](https://github.com/Ftsem/CustomerChurn-Python/blob/81e8068283040ea5b9746226d637ea19abf2fff3/Assets/Screenshot%202025-04-10%20110221.png)
#### Observations
Churn vs Contract: Customers on Month-to-month contracts exhibit the highest churn rate, while customers on longer-term contracts (One year, Two year) have a significantly lower churn rate. This suggests that the company might retain customers better when they commit to longer-term contracts.

Churn vs PaymentMethod: The Electronic check payment method is associated with higher churn rates, which may indicate that customers using this payment method have issues with service or billing.

Churn vs Partner and Dependents: Customers without a Partner or Dependents tend to churn more. This might indicate that those who are part of a family or household are more likely to stay as they have a higher level of commitment to the service.

### 5. ** Feature Importance using Random Forests **
![](https://github.com/Ftsem/CustomerChurn-Python/blob/81e8068283040ea5b9746226d637ea19abf2fff3/Assets/Screenshot%202025-04-10%20120551.png)
#### Observations
The Contract, Tenure, and Monthly Charges features had the most significant importance in predicting customer churn, as expected based on the EDA. These are the features that the model would rely on the most when making predictions.


### 6. ** Correlation Matrixs **
![](https://github.com/Ftsem/CustomerChurn-Python/blob/81e8068283040ea5b9746226d637ea19abf2fff3/Assets/Screenshot%202025-04-10%20120543.png)
#### Observations

Tenure and Total Charges: These two features have a positive correlation, which makes sense because customers who have been with the company longer are likely to have paid more overall.

Monthly Charges and Churn: There’s a moderate negative correlation between MonthlyCharges and Churn. This suggests that higher monthly charges might correlate with a higher likelihood of churn, especially for customers who are dissatisfied with the cost or value they are receiving.





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

