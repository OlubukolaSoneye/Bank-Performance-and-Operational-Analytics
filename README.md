# Bank-Performance-and-Operational-Analytics
The Performance Analytics dashboard analyses bank transaction data using Power BI to understand transaction volume, value, and system performance. It highlights how transactions are distributed across network bandwidth tiers and regions. 

## 📌 Project Overview
This Power BI dashboard analyzes bank transaction data to reveal patterns in transaction volumes, monetary values, and performance across network bandwidth tiers. Built using DAX measures and interactive visualizations, it enables stakeholders to make data-driven decisions about transaction infrastructure and resource allocation.

## 📌 Project Statement
Transaction systems rely on network capacity to operate efficiently. Without clear insight into how transactions are distributed across bandwidth levels, organisations risk inefficient resource allocation, performance bottlenecks, or unnecessary infrastructure costs. This analysis set out to answer the following questions:

1. How are transactions distributed across different bandwidth ranges?
2. Are higher-value or higher-volume transactions concentrated in specific bandwidth tiers?
3. Can bandwidth grouping reveal patterns that support capacity planning and operational monitoring?

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

## 🛠️ Tools Used
Power BI for data modelling, visualisation, and dashboard development
DAX for calculated measures and bandwidth grouping

## 📌 Dashboard Design and Exploration
The dashboard is structured to move from high-level performance metrics to more detailed analysis. Summary KPIs provide immediate visibility into transaction volume and value, while bandwidth group visuals highlight how activity is distributed across network capacity tiers. Interactive filters allow users to drill into specific transaction segments and explore patterns in more detail.

## 📌 Key Insights
The dashboard shows 1,000 transactions with a total value of approximately £771K. Transaction outcomes are almost evenly split, with 513 failed and 487 successful transactions, highlighting potential reliability issues within the transaction process. Transaction activity is most concentrated in the 150–250 Mbps bandwidth group, which records the highest volume of transactions. Lower bandwidth ranges handle fewer transactions, indicating that higher network capacity supports the bulk of processing. Transaction types are evenly distributed, with Transfers (37.4%), Deposits (31.6%), and Withdrawals (31%), suggesting no single transaction type disproportionately drives system load. Fraud-flagged transactions account for just over half of total activity (51.9%) and are again most concentrated in the 150–250 Mbps bandwidth tier, reinforcing the link between higher bandwidth usage and increased risk. Transaction and fraud activity are primarily concentrated in North America and Europe.

## 📌 Business Value
The concentration of activity and fraud in the 150–250 Mbps range highlights this tier as a priority for capacity planning, monitoring, and optimisation. The high proportion of failed transactions indicates areas where performance improvements could significantly increase system reliability. By linking transaction value, bandwidth usage, and fraud indicators, the dashboard supports targeted risk monitoring and more efficient allocation of infrastructure resources. 

## 📌 Conclusion
This project demonstrates how combining transaction metrics with bandwidth analysis can reveal where system demand and risk are highest. The Power BI dashboard provides a clear, practical view of transaction performance, supporting better operational monitoring and informed decisions around network capacity and fraud control.

Interact with the dashboard - https://app.powerbi.com/groups/me/reports/2e0b58a6-e735-4c45-92f4-31a6c571e1d5/d74678b5934723b76859?experience=power-bi


<p align="center">
  <img src="Screenshot 2026-02-21 at 13.15.28.png"250"/>
</p>

<p align="center">
  <img src="Screenshot 2026-02-21 at 13.15.37.png"250"/>
</p>

<p align="center">
  <img src="Screenshot 2026-02-21 at 13.15.45.png"250"/>
</p>
