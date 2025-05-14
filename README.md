# 📊 Customer Churn Analysis Dashboard (Power BI)

This Power BI project provides a comprehensive dashboard to monitor and analyze customer churn trends over time. It includes key performance indicators (KPIs), visual breakdowns by plan and region, and time-based insights powered by a custom date table.

---

## 🚀 Features

- **KPIs**: Total Customers, Active Customers, Churned Customers, Churn Rate (%)
- **Visuals**:
  - Pie chart showing Active vs Churned customers
  - Bar charts for churn by region and plan
  - Line chart for monthly customer joins and churns
  - Table view of customer-level data
- **Slicers**: Gender, Region, Plan, Status
- **Date Table**: Enables consistent time-based analysis with full support for year/month trends and custom date hierarchies
- **DAX Measures**: Used for churn rate, monthly trends, and performance comparisons

---

## 📂 Files Included

- `Customer_Churn_Dataset.csv`: Sample dataset with customer details
- `Customer_Churn_Analysis.pbix`: Power BI report file
- `README.md`: Project documentation



## 🧠 Key DAX Measures

```dax
Churn Rate (%) = 
DIVIDE(
    [Churned Customers],
    [Total Customers],
    0
) * 100

Joins Per Month = 
CALCULATE(
    COUNT(Customer_Churn_Dataset[CustomerID]),
    USERELATIONSHIP(Customer_Churn_Dataset[JoinDate], DateTable[Date])
)

Churns Per Month = 
CALCULATE(
    COUNT(Customer_Churn_Dataset[CustomerID]),
    Customer_Churn_Dataset[Status] = "Churned",
    USERELATIONSHIP(Customer_Churn_Dataset[EndDate], DateTable[Date])
)
