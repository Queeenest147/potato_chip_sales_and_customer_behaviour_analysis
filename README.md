# Woolworths Retail Sales & Customer Behaviour Analytics

### Potato Chips Sales, Customer Insights & Purchasing Behaviour Analysis
This project analyzes Woolworths potato chip sales and customer purchasing behaviour to understand what customers buy, who drives sales, and how purchasing patterns change over time. Using Python and Pandas for data inspection, cleaning, feature engineering, and exploratory analysis, followed by Power BI for interactive visualization, the project examines key metrics such as total revenue, transactions, units sold, customer count, average spend per transaction, and purchase frequency. The analysis further explores customer segments by lifestage and premium customer status, product preferences by brand and packet size, and purchasing trends across months and quarters. The resulting four-dashboard Power BI solution provides actionable insights to support customer targeting, product strategy, marketing campaigns, and data-driven retail decision-making.

<p align="center">

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Google Colab](https://img.shields.io/badge/Google%20Colab-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=black)
![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-005571?style=for-the-badge)

</p>

---

## Table of Contents

- [Project Overview](#project-overview)
- [Business Problem / Objective](#business-problem--objective)
- [Dataset Description](#dataset-description)
- [Data Cleaning and Preparation](#data-cleaning-and-preparation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Dashboard Design](#dashboard-design)
  - [Executive Overview](#executive-overview)
  - [Customer Insights](#customer-insights)
  - [Product Performance](#product-performance)
  - [Purchasing Behaviour & Trends](#purchasing-behaviour--trends)
- [Key Metrics and Calculations](#key-metrics-and-calculations)
- [Key Findings / Insights](#key-findings--insights)
- [Recommendations](#recommendations)
- [Tools Used](#tools-used)
- [Conclusion](#conclusion)
- [Portfolio/CV Project Summary](#portfoliocv-project-summary)

# Business Problem / Objective
Woolworths needed to better understand customer purchasing behaviour and potato chip sales performance in order to make more informed retail decisions. The project aims to identify who buys, what they buy, and how they purchase, using transaction data to uncover customer preferences, product performance, and purchasing patterns. These insights can support customer targeting, marketing campaigns, product strategy, and sales planning.

# Dataset Description
The analysis uses two datasets:

| Dataset | Records | Columns | Purpose |
|---|---:|---:|---|
| **Transaction Data** | 264,836 | 8 | Purchase-level sales and product analysis |
| **Customer Data** | 72,637 | 3 | Customer segmentation and purchasing behaviour analysis |

## Dataset Dictionary

| Dataset | Column | Description |
|---|---|---|
| **Transaction** | `DATE` | Date of transaction |
| | `STORE_NBR` | Store identifier |
| | `LYLTY_CARD_NBR` | Customer loyalty card identifier |
| | `TXN_ID` | Transaction identifier |
| | `PROD_NBR` | Product identifier |
| | `PROD_NAME` | Product name |
| | `PROD_QTY` | Number of units purchased |
| | `TOT_SALES` | Total sales value |
| **Customer** | `LYLTY_CARD_NBR` | Customer loyalty card identifier |
| | `LIFESTAGE` | Customer lifestage segment |
| | `PREMIUM_CUSTOMER` | Customer purchasing/loyalty segment |

The transaction and customer datasets were linked using **`LYLTY_CARD_NBR`**, enabling the analysis of sales performance alongside customer characteristics.

# Data Cleaning and Preparation
# Data Cleaning and Preparation

Data cleaning and preparation were carried out in **Python using Pandas in Google Colab** before the data was imported into Power BI.

### Data Cleaning Steps

- Inspected the structure, dimensions, data types, and contents of both datasets.
- Checked both datasets for missing values; **no missing values were identified**.
- Identified and removed **one fully duplicated transaction record** to prevent double-counting.
- Converted the `DATE` column from an integer/Excel serial format into a proper datetime format.
- Validated the transaction date range from **1 July 2018 to 30 June 2019**.
- Checked numerical fields for negative or invalid zero values; no inappropriate values were identified.
- Validated customer segments to ensure only expected **LIFESTAGE** and **PREMIUM_CUSTOMER** categories were present.
- Validated customer and transaction identifiers, distinguishing legitimate repeated transaction IDs from actual duplicate records.
- Reviewed product names and identified inconsistent and abbreviated brand names for standardization.

# Dataset Inspection

The datasets were first inspected in **Python using Pandas** to understand their structure, dimensions, columns, data types, and key relationships.

- **Customer Data:** 72,637 records × 3 columns
- **Transaction Data:** 264,836 records × 8 columns
- `LYLTY_CARD_NBR` was identified as the common field linking both datasets.
- `DATE` was identified as requiring conversion from integer format to datetime.
- `PROD_NAME` was identified as containing information that could be used to derive product features such as brand and packet size.

---

## Data Quality Assessment

Several data-quality checks were performed before analysis:

- Checked for missing values — **none were identified**.
- Validated numerical fields for inappropriate negative or zero values.
- Confirmed that customer and transaction identifiers were valid.
- Checked `LIFESTAGE` and `PREMIUM_CUSTOMER` for unexpected categories — **none were found**.
- Reviewed product names for spelling inconsistencies and abbreviated brand names that required standardization.

---

## Duplicate Record Handling

A duplicate assessment identified **one fully duplicated transaction record**.

Because all fields, including `TXN_ID`, were identical, the record was considered a duplicate rather than a legitimate purchase. It was removed to prevent **double-counting of transactions, units sold, and revenue**.

Customer records contained no duplicate records. Repeated `TXN_ID` values in the transaction data were retained where they represented legitimate multiple product line items within the same transaction. :contentReference[oaicite:0]{index=0} :contentReference[oaicite:1]{index=1}

## Feature Engineering
Additional variables were created to support the analysis:

| Feature | Purpose |
|---|---|
| `Year` | Transaction year |
| `Month` | Numeric transaction month |
| `Month_Name` | Month name for reporting |
| `Quarter` | Calendar quarter |
| `PACKET_SIZE_G` | Packet size extracted from product name |
| `BRAND_NAME` | Standardized brand name |

These preparation steps produced a consistent, analysis-ready dataset for the subsequent **exploratory analysis in Python and dashboard development in Power BI**. :contentReference[oaicite:0]{index=0} :contentReference[oaicite:1]{index=1}

# Exploratory Data Analysis

The cleaned transaction dataset was analysed in **Python using Pandas** to identify key sales, product, customer, purchasing behaviour, and time-based patterns.

## Overall Business Performance

The overall performance analysis calculated:

- Total revenue
- Total transactions
- Total units sold
- Average spend per transaction
- Unique customer count
- Purchase frequency

<img width="1200" height="675" alt="image" src="https://github.com/user-attachments/assets/a7fcafd5-98e6-4ff9-a667-45ab1f9071dd" />

## Product Analysis

### Brand Performance

Compared total revenue generated across standardized chip brands to identify the strongest-performing brands.

### Packet Size Analysis

Compared packet sizes based on:

- Total units sold
- Total revenue

### Product Purchase Frequency

Identified the products appearing most frequently across transactions.

## Customer Analysis

Customer information was merged with the transaction dataset using `LYLTY_CARD_NBR`.

### Lifestage Analysis

Compared lifestage segments based on:

- Units purchased
- Total revenue
- Transaction frequency
- Average spend per transaction

### Premium Customer Analysis

Compared **Budget, Mainstream, and Premium** customer segments based on total revenue.

### Customer Revenue

Analysed total revenue generated by each lifestage segment.

### Customer Purchase Frequency

Compared transaction activity across lifestage segments.

### Average Spend per Transaction

Calculated the average transaction value for each lifestage using total revenue divided by transaction frequency.

## Purchasing Behaviour Analysis

### Brand Preference by Lifestage

Examined the number of units purchased for each brand across different lifestage segments.

### Packet Size Preference by Lifestage

Examined packet-size preferences across lifestage segments using units purchased.

### Premium Customer Spending Behaviour

Compared total revenue generated by Budget, Mainstream, and Premium customers.

## Sales Trend Analysis

### Monthly Sales Trends

Compared total revenue across months to identify the highest- and lowest-performing periods.

### Quarterly Sales Trends

Compared total revenue across calendar quarters.

### Units Sold Over Time

Analysed monthly unit sales to examine changes in purchasing volume over time.

---

# Dashboard Design

## Executive Overview

## Customer Insights

## Product Performance

## Purchasing Behaviour & Trends

---

# Key Metrics and Calculations

## Total Revenue

## Total Transactions

## Total Units Sold

## Unique Customers

## Average Spend per Transaction

## Purchase Frequency

---

# Key Findings / Insights

## Customer Insights

## Product Performance

## Purchasing Behaviour

## Sales Trends

---

# Recommendations

## Customer Targeting

## Product Strategy

## Marketing Campaigns

## Premium Customer Strategy

## Seasonal Sales Planning

---

# Tools Used

| Tool | Purpose |
|------|---------|
| **Python** | Data inspection, cleaning, feature engineering and exploratory analysis |
| **Pandas** | Data manipulation, transformation and aggregation |
| **Google Colab** | Python development and analysis environment |
| **Power BI** | Interactive dashboard development and data visualization |
| **DAX** | Analytical measures and calculations in Power BI |

---

# Conclusion

---

# Portfolio/CV Project Summary

---

## Author

**Esther Matthew**

Data Analyst | Power BI | Python | SQL | Excel
