# Bank-Performance-and-Operational-Analytics
The Performance Analytics dashboard analyses bank transaction data using Power BI to understand transaction volume, value, and system performance. It highlights how transactions are distributed across network bandwidth tiers and regions. 

## 📌 Project Overview
This Power BI dashboard analyzes bank transaction data to reveal patterns in transaction volumes, monetary values, and performance across network bandwidth tiers. Built using DAX measures and interactive visualizations, it enables stakeholders to make data-driven decisions about transaction infrastructure and resource allocation.

## 📌 Project Statement
Transaction systems rely on network capacity to operate efficiently. Without clear insight into how transactions are distributed across bandwidth levels, organisations risk inefficient resource allocation, performance bottlenecks, or unnecessary infrastructure costs. This analysis set out to answer the following questions:

How are transactions distributed across different bandwidth ranges?
Are higher-value or higher-volume transactions concentrated in specific bandwidth tiers?
Can bandwidth grouping reveal patterns that support capacity planning and operational monitoring?

## 📌 Dataset Overview
Each record in the dataset captures: a unique Transaction ID that identifies each individual transaction, the Transaction Amount representing the monetary value processed, and the Slice Bandwidth measured in Mbps, which indicates the network bandwidth consumed during processing.

## 📌 Methodology - Data Preparation and Modelling
The dataset was reviewed to ensure consistency and suitability for analysis. The modelling process included:

1. Creating calculated measures for total transaction value and transaction count.
2. Grouping raw bandwidth values into meaningful ranges using DAX.
3. Ensuring clean relationships to support accurate aggregation and filtering.

## 📌 Key Measures and Calculations
Total Transaction Amount - This measure calculates the total value of all transactions

```DAX
Total Transaction Amount = SUM('bank transaction_data'[Transaction Amount])
```

```DAX
Total Transactions = DISTINCTCOUNT('bank transaction_data'[Transaction ID])
```

```DAX
Bandwidth Group = SWITCH ( TRUE(), [Slice Bandwidth (Mbps)] >= 50 && [Slice Bandwidth (Mbps)] < 100, "50–100 Mbps", [Slice Bandwidth (Mbps)] >= 100 && [Slice Bandwidth (Mbps)] < 150, "100–150 Mbps", [Slice Bandwidth (Mbps)] >= 150 && [Slice Bandwidth (Mbps)] <= 250, "150–250 Mbps", "Out of Range" )
```

<p align="center">
  <img src="Screenshot 2026-02-21 at 12.17.55.png"450"/>
</p>

## 📌 Multicollonearity
The scatter plot reveals that the variables Departure_Delay and Arrival_Delay are highly correlated.
<p align="center">
  <img src="Screenshot 2026-02-21 at 12.18.06.png"450"/>
</p>

Data Modelling was done using Logistic Regression models and Decision tree models, Here is the result of the best performing model

From the models created, the most optimal model from the project is the DT-Entropy-Multiway Split, with a ROC Index of 0.98, indicating how well it can distinguish between classes. The most likely positive instances are efficiently targeted by attaining a high Cumulative Lift 3. Its low false negative rate of 54 and somewhat low false positive rate of 167 make it reliable for use in decision-making.
<p align="center">
  <img src="Screenshot 2026-02-21 at 12.18.18.png"450"/>
</p>
