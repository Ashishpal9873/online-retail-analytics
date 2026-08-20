# 📊 Online Retail Analytics

## Sales Performance & Customer Segmentation Analysis

An end-to-end data analytics portfolio project based on the **UCI Online Retail Dataset**, containing 541,909 transactions from a UK-based online gift retailer between December 2010 and December 2011.

The project focuses on two major areas:

- 📈 Sales Performance Analysis
- 👥 Customer Segmentation using RFM Analysis and K-Means Clustering

## 🔗 Project Repository

GitHub: https://github.com/Ashishpal9873/online-retail-analytics

## 📌 Project Overview

This project transforms raw online retail transaction data into meaningful business insights through data cleaning, exploratory analysis, visualization, RFM customer segmentation, and machine learning.

### Project Workflow

Raw Dataset → Data Cleaning → Sales Performance Analysis → Customer Segmentation → Business Insights

## 📂 Dataset

**Source:** UCI Machine Learning Repository – Online Retail Dataset

- **Raw Transactions:** 541,909
- **Period:** December 2010 – December 2011
- **Business Type:** Online Retail / Gift Retailer
- **Primary Market:** United Kingdom

### Main Fields

| Column | Description |
|---|---|
| InvoiceNo | Invoice/transaction number |
| StockCode | Product code |
| Description | Product description |
| Quantity | Quantity purchased |
| InvoiceDate | Date and time of transaction |
| UnitPrice | Price per unit |
| CustomerID | Unique customer identifier |
| Country | Customer's country |

Dataset Source: https://archive.ics.uci.edu/dataset/352/online+retail

## 🎯 Tasks Completed

### Task 1 — Sales Performance Analysis

The sales analysis focuses on understanding overall business performance and purchasing patterns.

- Total revenue
- Total orders
- Average Order Value
- Customer count
- Repeat purchase rate
- Monthly revenue trends
- Top-performing products
- Regional/country sales
- Weekday purchasing patterns
- Hourly purchasing patterns
- New vs. repeat customer revenue

### Task 2 — Customer Segmentation

Customer segmentation is performed using **RFM Analysis** and **K-Means Clustering**.

**RFM** stands for:

- **Recency** – How recently a customer purchased
- **Frequency** – How frequently a customer purchases
- **Monetary** – How much a customer spends

### Customer Segments

1. 🏆 Champions
2. 💎 Loyal Customers
3. ⚠️ At Risk
4. 🚨 Can't Lose Them
5. 🆕 New Customers
6. 🌟 Potential Loyalists
7. 👀 Needs Attention
8. 💤 Hibernating / Lost

## 🤖 K-Means Clustering

K-Means clustering is used to independently validate the RFM-based customer segmentation.

- Number of clusters: **4**
- `random_state`: **42**
- `n_init`: **10**
- RFM values transformed using `log1p`
- Features standardized using `StandardScaler`

Clusters are labeled based on average Monetary value into High, Mid, Low and Lowest-Value groups.

## 🧹 Data Cleaning

The following cleaning steps were applied:

1. Removed rows with missing or blank product descriptions.
2. Identified and excluded cancelled invoices.
3. Removed transactions where `Quantity <= 0`.
4. Removed transactions where `UnitPrice <= 0`.
5. Calculated transaction revenue:

`TotalPrice = Quantity × UnitPrice`

6. Customer segmentation was performed only for records with a valid `CustomerID`.

## 📈 Key Results

### Sales Performance

- **Total Revenue:** £10,666,684.54
- **Total Orders:** 19,960
- **Customers:** 4,338
- **Average Order Value:** £534.40
- **Repeat Purchase Rate:** 65.6%

### Major Findings

- Revenue shows strong seasonal behavior.
- Sales performance peaks during **Q4**, particularly September–November.
- The **United Kingdom** generates the majority of revenue.
- Netherlands, EIRE, Germany, and France are among the leading international markets.
- Most orders occur between approximately **10:00 and 15:00**.
- Saturday has effectively no recorded order volume.

## 👥 Customer Segmentation Results

- **Customers Segmented:** 4,338
- **Segmented Revenue:** £8,911,407.90

### Champions

- **962 customers**
- Approximately **22%** of customers
- Generate approximately **65%** of segmented revenue

### High-Value At-Risk Customers

**At Risk:**
- 288 customers
- £372,310 revenue

**Can't Lose Them:**
- 166 customers
- £369,840 revenue

These customers represent an important **win-back opportunity**, as they previously demonstrated high purchasing value but have become inactive.

## 🐛 Important Segmentation Bug Fix

During the project audit, a rule-ordering issue was identified in the RFM segmentation logic.

The broader **At Risk** condition was originally evaluated before the more specific **Can't Lose Them** condition.

Because higher Frequency and Monetary values also satisfy the broader conditions, some customers were incorrectly classified.

### Fix

The more specific **Can't Lose Them** condition was evaluated first.

After correction:

- **Can't Lose Them:** 166 customers / £369,840
- **At Risk:** 288 customers / £372,310

All dashboards, reports, and notebook outputs use the corrected segmentation logic.

## 📊 Dashboards

The project includes two interactive dashboards built using **Plotly**.

### Sales Performance Dashboard

Provides insights into:

- Revenue
- Orders
- Average Order Value
- Monthly trends
- Product performance
- Country-level sales
- Customer behavior
- Purchasing time patterns

### Customer Segmentation Dashboard

Provides insights into:

- RFM segments
- Customer distribution
- Revenue contribution
- K-Means clusters
- High-value customers
- At-risk customers

## 📁 Project Structure

```text
online-retail-analytics/
│
├── README.md
├── requirements.txt
├── .gitignore
├── vercel.json
├── index.html
├── validate_project.py
│
├── dashboard/
│   ├── sales_dashboard.html
│   └── customer_segmentation_dashboard.html
│
├── notebooks/
│   ├── OnlineRetail.csv
│   ├── Task1_Sales_Performance_Dashboard.ipynb
│   └── Task2_Customer_Segmentation_Analysis.ipynb
│
├── src/
│   ├── analysis_core.py
│   ├── generate_task1_assets.py
│   ├── generate_task2_assets.py
│   ├── build_dashboard1.py
│   ├── build_dashboard2.py
│   ├── build_report1.py
│   ├── build_report2.py
│   ├── build_notebook1.py
│   └── build_notebook2.py
│
├── data/
├── reports/
└── figures/
