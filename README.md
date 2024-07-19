# E-Commerce Churn Prediction
-------------------------------

## **Business Background**  

Treepedia, a prominent e-commerce company, is grappling with a significant business challenge: elevated customer churn rates. Customer churn, defined as the cessation of purchasing activity or engagement with the platform, has a direct impact on Treepedia's revenue generation and growth potential. Each churned customer represents lost revenue from potential future purchases.   

Understanding and proactively addressing churn is of paramount importance for Treepedia. By identifying the key drivers of churn and accurately predicting which customers are likely to discontinue their relationship with the company, Treepedia can implement targeted retention strategies to enhance customer loyalty and, ultimately, protect its revenue streams.  


 ----------------------------------
## **Business Problem**  

The central question this project seeks to answer is: How can Treepedia leverage its wealth of customer data, encompassing demographics, purchase history, satisfaction metrics, and other relevant factors, to accurately predict customer churn and mitigate its adverse effects on revenue?   


 ----------------------------------
## **Objectives**  

- Primary Objective: Minimize revenue loss due to churn by developing a predictive model capable of accurately identifying customers at high risk of churn.  
- Secondary Objective: Optimize the allocation of resources dedicated to retention efforts by minimizing false positive predictions, thereby ensuring that efforts are focused on customers genuinely at risk of churn.


-----------------------------------
## **Problem Solving Approach**   

Treepedia will employ a data-driven methodology utilizing tree-based machine learning models:

1. Data Preparation: Rigorously clean and preprocess historical customer data, ensuring data quality and suitability for tree-based algorithms.  
2. Exploratory Data Analysis (EDA): Conduct a comprehensive analysis and visualization of the data to identify salient patterns, trends, and correlations between customer attributes and churn behavior.  
3. Model Development: Develop and train a variety of tree-based models (e.g., decision trees, random forests, XGBoost) directly on the prepared dataset, leveraging their inherent ability to handle complex relationships without extensive feature engineering.  
4. Model Evaluation: Evaluate the performance of each model using recall (primary metric) and precision (secondary metric) to achieve a balance between identifying potential churners and avoiding misclassification of loyal customers.   
5. Model Selection and Optimization: Select the model that demonstrates superior performance in identifying churned customers, while considering the cost-benefit trade-off of retention strategies to find the optimal balance between recall and precision.   


-----------------------
### **Evaluation Metrics**   

- Primary Metric: Recall (minimize false negatives). The priority is to identify the maximum number of potential churners to prevent revenue loss.  
- Secondary Metric: Precision (minimize false positives). This is important to avoid wasting resources on retaining customers who would have remained loyal.   

### **Business Metrics**   

- Revenue Loss Due to Churn: The financial impact of customers who churned but were not predicted by the model.  
- Wasted Resources: The cost of resources allocated to retention efforts for customers who were incorrectly predicted to churn and would have likely remained loyal.  


-------------------------
### **Data Overview**   

The data set belongs to a leading online E-commerce company. An online retail (E-commerce) company wants to know the customers who are going to churn, so accordingly, they can approach customers to offer some promos.

| Feature                   | Description                                                   |
|---------------------------|---------------------------------------------------------------|
| **Tenure**                | Tenure of a customer in the company.                          |
| **WarehouseToHome**       | Distance between the warehouse to the customer’s home.        |
| **NumberOfDeviceRegistered** | Total number of devices registered on a particular customer. |
| **PreferedOrderCat**      | Preferred order category of a customer in the last month.     |
| **SatisfactionScore**     | Satisfactory score of a customer on service.                  |
| **MaritalStatus**         | Marital status of a customer.                                 |
| **NumberOfAddress**       | Total number of addresses added by a particular customer.     |
| **Complaint**             | Any complaint raised in the last month.                       |
| **DaySinceLastOrder**     | Days since the last order by the customer.                    |
| **CashbackAmount**        | Average cashback in the last month.                           |
| **Churn**                 | Churn flag.                                                   |


--------------
## Model-Business Explanation  

The core objective of the predictive model is to accurately forecast customer churn, allowing Treepedia to proactively implement retention strategies and minimize financial losses. The model aims to strike a balance between identifying customers at high risk of churn (minimizing false negatives) while avoiding unnecessary marketing expenditures on customers unlikely to churn (minimizing false positives).  
 
**4.1.1. Key Assumptions:**   

* **Average Customer Lifetime Value (CLTV):** $500 (based on average customer lifetime value in e-commerce)  

* **Marketing Budget:** 13.6% of total revenue from retained customers (this represents the maximum budget available for retention initiatives)   

* **Marketing Cost per Customer (If all retained customers are targeted):** \$68 (calculated as $184,756 / 2717 retained customers)  

**4.1.2. Financial Impact**  

* **True Positive (TP):** The model correctly predicts churn, resulting in a potential saving of \$432 per customer (\$500 CLTV - \$68 marketing cost).  *This represents revenue preserved by successfully retaining the customer through targeted interventions.*  

* **True Negative (TN):** The model correctly predicts no churn, allowing the company to retain the full customer value of $500. *This represents revenue from customers who remain loyal without needing additional retention efforts.*  

* **False Positive (FP):** The model incorrectly predicts churn, leading to an unnecessary marketing cost of $68 per customer. *This represents wasted resources on customers who wouldn't have churned regardless.*  

* **False Negative (FN):** The model incorrectly predicts no churn, resulting in a revenue loss of $500 per customer. *This is the most significant cost, as the company misses the opportunity to intervene and potentially retain the customer.*   

**4.1.3. Financial Impact Without Modeling (Baseline)**   

Based on a historical churn rate of 16.35%, without the model, Treepedia would incur:  

* **Total Customers:** 3,248  
* **Churn Rate:** 16.35%   
* **Total Churn:** 531 customers  
* **Total Revenue Loss:** 531 customers * \$500 = $265,500  

**4.1.4. Financial Impact with Perfect Model (100% Recall & Precision)**  

With a model achieving 100% recall (no false negatives) and 100% precision (no false positives), Treepedia would:  

* **Correctly Predict Churn (TP):** 531 customers  

* **Correctly Predict No Churn (TN):** 2,717 customers  

* **Revenue Loss Due to Churn (FN):** $0 (all churned customers are correctly identified)  

* **Cost of False Positives (FP):** $0 (no customers are incorrectly predicted to churn)  

* **Revenue Saved from True Positives (TP):** 531 customers * \$432 = $229,392  

* **Revenue from True Negatives (TN):** 2,717 customers * \$500 = $1,358,500  

* **Total Revenue with Model:** \$229,392 + \$1,358,500 = $1,587,892  

* **Net Revenue Increase with Model:** \$1,587,892 - \$1,358,500 = $229,392    


-------------
## Modeling  
 **The Best Model is XGBoost with RandomOverSampler**
