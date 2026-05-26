# 📉 Telecom Customer Churn Analysis
### Tools Used: MySQL



## 🔍 Problem Statement
Customer churn is one of the most expensive problems in the telecom industry. This project analyzes a telecom dataset of 7,032 customers to identify the key drivers of churn and provide actionable business recommendations to improve retention.



## 📁 Dataset
- **Source:** Kaggle — Telecom Customer Churn Dataset
- **Size:** 7,032 customer records
- **Key Fields:** Contract type, tenure, monthly charges, internet service, payment method, churn status



## 🛠️ Tools Used
- **MySQL Workbench** — data exploration, segmentation, and insight extraction



## 💡 Key Business Insights
- **1 in 4 customers is churning** — 26% overall churn rate
- **Month-to-month contract customers** churn at significantly higher rates
- **First 12 months are critical** — early experience directly impacts retention
- **Electronic check users** show higher churn compared to auto-pay users
- **Higher monthly charges** correlate with increased churn



## 📊 Analyses Performed
1. Total Churn Rate — 26% of 7,032 customers churned
2. Contract Type Analysis — month-to-month vs annual churn comparison
3. Tenure Analysis — customers under 12 months have highest churn
4. Payment Method Analysis — electronic check users churn more
5. Monthly Charges Analysis — higher charges = higher churn
6. Internet Service Analysis — fiber optic users churn more than DSL



## 📝 Sample SQL Queries

```sql
-- Overall Churn Rate
SELECT CHURN, COUNT(*) AS count,
       COUNT(*) * 100 / (SELECT COUNT(*) FROM CLEANED_DATA) AS percentage
FROM CLEANED_DATA
GROUP BY CHURN;

-- Churn by Contract Type
SELECT CONTRACT, COUNT(*) AS TOTAL_CUSTOMER,
       SUM(CASE WHEN CHURN = 'YES' THEN 1 ELSE 0 END) AS CHURNED_COUNT
FROM CLEANED_DATA
GROUP BY CONTRACT;

-- Churn by Tenure Group
SELECT
  CASE
    WHEN TENURE < 12 THEN '0-1 Year'
    WHEN TENURE < 24 THEN '1-2 Years'
    ELSE '2+ Years'
  END AS TENURE_GROUP,
  COUNT(*) AS TOTAL,
  SUM(CASE WHEN CHURN = 'YES' THEN 1 ELSE 0 END) AS TOTAL_CHURN
FROM CLEANED_DATA
GROUP BY TENURE_GROUP;
```



## ✅ Business Recommendations
1. Offer annual plan incentives to month-to-month customers within 90 days
2. Create an early retention program for customers in their first 6 months
3. Promote auto-pay adoption with discounts
4. Review pricing for high monthly charge segments



## 🚀 Future Scope
- Build a Power BI dashboard to visualize churn trends
- Add predictive churn modeling using Python



## 👤 Author
**Devangi Mehta**
[LinkedIn](https://linkedin.com/in/devangi-mehta-012896241) | mehtadevangim@gmail.com
