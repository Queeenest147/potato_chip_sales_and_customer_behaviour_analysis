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
- [Dataset Inspection](#dataset-inspection)
- [Data Cleaning and Preparation](#data-cleaning-and-preparation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Dashboard Design](#dashboard-design)
- [Key Metrics and Calculations](#key-metrics-and-calculations)
- [Key Findings / Insights](#key-findings--insights)
- [Recommendations](#recommendations)
- [Conclusion](#conclusion)
- [Tools Used](#tools-used)
- [Author](#author)

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

<img width="800" height="500" alt="image" src="https://github.com/user-attachments/assets/a7fcafd5-98e6-4ff9-a667-45ab1f9071dd" />

## Product Analysis

### Brand Performance

Compared total revenue generated across standardized chip brands to identify the strongest-performing brands.

### Packet Size Analysis

Compared packet sizes based on:

- Total units sold
- Total revenue

<img width="900" height="300" alt="image" src="https://github.com/user-attachments/assets/04d8d75b-430a-43f4-9035-f0eea3d994da" />

<img width="900" height="300" alt="image" src="https://github.com/user-attachments/assets/f7083357-714f-49a4-ba36-55d2f0775bf7" />


### Product Purchase Frequency

Identified the products appearing most frequently across transactions.

<img width="900" height="300" alt="image" src="https://github.com/user-attachments/assets/2a98480f-3ae2-497a-bddb-d21103a91091" />


## Customer Analysis

Customer information was merged with the transaction dataset using `LYLTY_CARD_NBR`.

### Lifestage Analysis

Compared lifestage segments based on:

- Units purchased
- Total revenue
- Transaction frequency
- Average spend per transaction

<img width="900" height="300" alt="image" src="https://github.com/user-attachments/assets/7e916968-6d01-4b0d-a926-d227c51136c3" />

---

<img width="705" height="303" alt="image" src="https://github.com/user-attachments/assets/9e9ed6fb-2063-476e-9b43-785caa744477" />


## Purchasing Behaviour Analysis

### Brand Preference by Lifestage

Examined the number of units purchased for each brand across different lifestage segments.

<img width="900" height="300" alt="image" src="https://github.com/user-attachments/assets/1e9897a5-dee3-465c-bf84-e7b194a05d11" />


### Packet Size Preference by Lifestage

Examined packet-size preferences across lifestage segments using units purchased.

<img width="900" height="300" alt="image" src="https://github.com/user-attachments/assets/17dc4963-d298-417a-ae8c-c60ded8ce934" />


### Premium Customer Spending Behaviour

Compared total revenue generated by Budget, Mainstream, and Premium customers.

<img width="900" height="500" alt="image" src="https://github.com/user-attachments/assets/9e377b72-63dd-495a-a74a-e350a376f43d" />


## Sales Trend Analysis

### Monthly Sales Trends

Compared total revenue across months to identify the highest- and lowest-performing periods.

<img width="900" height="300" alt="image" src="https://github.com/user-attachments/assets/197d05fd-4058-46c9-a1e5-d5932f42a832" />


### Quarterly Sales Trends

Compared total revenue across calendar quarters.

<img width="900" height="300" alt="image" src="https://github.com/user-attachments/assets/2fb6a451-31bb-4162-9076-08cc0d1fab3b" />


### Units Sold Over Time

Analysed monthly unit sales to examine changes in purchasing volume over time.

<img width="900" height="300" alt="image" src="https://github.com/user-attachments/assets/593abfd6-dd83-4351-813c-9d1dea73700b" />


---

# Dashboard Design

## Executive Overview

<img width="737" height="411" alt="image" src="https://github.com/user-attachments/assets/dca10115-25e0-40a7-a87d-420b3397096c" />

### Key Performance Indicators
* Total Revenue: Represents the total sales revenue generated during the analysis period, which is $1.93M.
* Total Transactions: Shows 265k customer transactions were recorded.
* Total Units Sold: 505K chips were purchased.
* Average Spend: $7.35 is the average amount spent per transaction.
* Purchase Frequency: The average number of transactions per customer is 3.62.
  
### Top 7 Brands by Revenue

This horizontal bar chart ranks the seven highest-revenue brands. Kettle generated the highest revenue, followed by Doritos and Smiths, highlighting the strongest-performing brands.

<img width="306" height="160" alt="image" src="https://github.com/user-attachments/assets/3d1059d7-f51d-4e01-87f9-3011580d0db4" />


### Top 10 Packet Sizes by Revenue

This chart compares revenue across the ten highest-performing packet sizes. The 175g packet size generated the highest revenue, followed by 150g, showing stronger revenue performance among larger packet sizes.

<img width="306" height="160" alt="image" src="https://github.com/user-attachments/assets/a41d82d2-8d1d-407b-beee-c078c9540e2d" />

### Revenue Made in Each Quarter

This column chart compares total revenue across the four quarters. Quarter 4 recorded the highest revenue, while Quarter 2 recorded the lowest, showing some variation in quarterly sales performance.

<img width="306" height="160" alt="image" src="https://github.com/user-attachments/assets/507f89dc-3f6f-406c-9f2d-cccb74e96d0f" />


### Monthly Revenue Trend

This line chart shows how revenue changed throughout the analysis period. Revenue generally remained relatively stable but showed a gradual decline toward the final months, with the lowest point occurring in the final month shown.

<img width="306" height="160" alt="image" src="https://github.com/user-attachments/assets/4daf552d-e16d-4728-b1b4-b6cd4f9fff1e" />


## Customer Insights

<img width="737" height="430" alt="image" src="https://github.com/user-attachments/assets/b8a556ce-c9f0-467f-9ae8-b446240432ff" />

### Key Performance Indicators

* **Total Customers:** The total number of customers represented in the transaction data is 264.84k.
* **Average Revenue:** The average revenue generated per customer is $26.63.
* **Units per Customer:** The average number of chip units purchased by each customer is 6.95.
* **Average Spend:** The average amount spent per transaction is $7.35.
* **Purchase Frequency:** The average number of transactions made per customer 3.62.

### Chips Quantity by Lifestage

This bar chart compares the total quantity of chips purchased across lifestage groups. **Older Singles/Couples** recorded the highest quantity purchased, while **New Families** recorded the lowest.

<img width="224" height="155" alt="image" src="https://github.com/user-attachments/assets/13bb7ae5-f49f-49f0-8020-62f53e42b0a3" />


### Revenue by Lifestage

This chart compares revenue generated by each lifestage. **Older Singles/Couples** generated the highest revenue, followed by **Retirees**, while **New Families** generated the lowest.

<img width="223" height="154" alt="image" src="https://github.com/user-attachments/assets/af0888d8-5ec1-47c4-b89a-b792ffc223ea" />


### Lifestage That Purchases More Frequently

This column chart compares purchase frequency across lifestage groups. **Older Families** and **Young Families** show the highest purchasing activity, while **Young Singles/Couples** are among the lower-frequency groups.

<img width="221" height="145" alt="image" src="https://github.com/user-attachments/assets/a99f4b0e-0cd4-419a-9310-a802594f7277" />


### Lifestage That Spends the Most per Transaction

This horizontal bar chart compares average transaction spending across lifestages. The values are relatively close, ranging from approximately **$7.2 to $7.4**, with **Older Singles/Couples, Midage Singles/Couples, Retirees, and Older Families** among the highest.

<img width="223" height="150" alt="image" src="https://github.com/user-attachments/assets/d8a35079-0bd4-486b-901f-d7894b3576d0" />


### Lifestage Filter

The lifestage slicer allows users to focus the dashboard on a specific customer lifestage and examine its purchasing behaviour across the other visuals.

### Premium Customer Filter

The premium customer slicer allows the analysis to be filtered by **Budget, Mainstream, or Premium** customer status.

### Lifestage × Premium Customer Spending

The matrix compares revenue across **lifestage and premium customer segments**, allowing users to identify which combinations generate the highest revenue.



## Product Performance

<img width="737" height="430" alt="image" src="https://github.com/user-attachments/assets/f01c8e2e-8333-4dcb-90ee-b0e1f1b034ef" />

### Key Performance Indicators

* **Total Revenue:** The total revenue generated from chip sales is $1.93M.
* **Total Units Sold:** The total number of chip units sold is 505K.
* **Top Product:** The highest-performing product based on the selected product-performance measure Dorito Corn.
* **Top Brand:** Kettle is the highest-performing brand.
* **Top Packet Size:** The 175g packet is the leading packet size.

#### Units of Products Sold by Brands

This column chart compares the total units sold across brands. **Smiths** recorded the highest unit sales, followed by **Doritos**, while **Cheezels** recorded the lowest among the brands displayed.

<img width="220" height="154" alt="image" src="https://github.com/user-attachments/assets/938340a4-c66f-4007-8585-155643a6e456" />


#### Top 8 Products that Drive Revenue

This horizontal bar chart ranks the eight products generating the highest revenue. The leading product generated approximately **$40K**, followed by other high-performing products with revenues around **$33K–$36K**.

<img width="220" height="298" alt="image" src="https://github.com/user-attachments/assets/5d4a5fc6-6b4a-4e1d-8a1d-6883a682d0c7" />


#### Top 5 Products by Quantity

This chart identifies the five products with the highest unit sales. The leading product recorded approximately **6.5K units**, with the remaining top products showing similarly strong sales volumes.

<img width="220" height="146" alt="image" src="https://github.com/user-attachments/assets/6ec344d8-18bc-4ab2-9dfd-bb3ec15d7731" />


#### Units of Products Sold by Packet Sizes

This chart compares units sold across packet sizes. The **175g** packet recorded the highest unit sales at approximately **12.7K units**, followed by the **150g** packet at approximately **12.1K units**.

<img width="220" height="139" alt="image" src="https://github.com/user-attachments/assets/3bcb5580-7446-4427-a216-bb65e0d0dff0" />


#### Quarter Filter

The quarter slicer allows users to filter the product-performance analysis by a specific quarter.

<img width="114" height="105" alt="image" src="https://github.com/user-attachments/assets/4645a8ff-e34e-480d-af7e-a790161a0dad" />


#### Month Filter

The month slicer allows users to examine product performance for a selected month, making it easier to compare product and brand performance across different periods.

<img width="114" height="159" alt="image" src="https://github.com/user-attachments/assets/5acf9a50-29a1-4590-9ade-3779125c61fb" />


## Purchasing Behaviour & Trends

<img width="737" height="430" alt="image" src="https://github.com/user-attachments/assets/7aa9c287-8c6a-44fb-b4ff-3be6387a2ba3" />

### Key Performance Indicators

* **Top Month:** December recorded the highest unit sales during the analysis period.
* **Top Quarter:** The fourth quarter (Q4) recorded the strongest overall performance.
* **Top Revenue Lifestage:** This lifestage (Older Singles/Couples) generated the highest revenue among the customer groups.
* **Average Spend:** The average amount spent per transaction is $7.35.
* **Purchase Frequency:** The average number of transactions per customer is 3.62.

### Revenue by Premium Customer Segment

This bar chart compares revenue generated by **Mainstream, Budget, and Premium** customers. **Mainstream customers** generated the highest revenue at approximately **$750K**, followed by Budget customers at about **$676K**, while Premium customers generated approximately **$507K**.

<img width="225" height="157" alt="image" src="https://github.com/user-attachments/assets/d2f81db9-0f42-4395-b08d-ef43bcea836c" />


### Brand Preference by Lifestage

This matrix compares the quantity of each chip brand purchased across different lifestage groups. It allows the business to identify **which brands are most preferred by each customer segment** and compare purchasing patterns across lifestages.

<img width="415" height="133" alt="image" src="https://github.com/user-attachments/assets/2cdbed75-fdbf-450a-8238-50a86e5af712" />


### Monthly Units Sold

This line chart shows monthly changes in unit sales throughout the year. Unit sales fluctuated across the months, with **December recording the highest volume at approximately 44K units**, while **February recorded the lowest at approximately 39K units**.

<img width="225" height="157" alt="image" src="https://github.com/user-attachments/assets/c62545ea-3791-4e49-89ec-a702829913e9" />


### Packet Size Preference by Lifestage

This matrix compares the quantity purchased across different packet sizes for each lifestage. It helps identify **which packet sizes are preferred by specific customer segments** and supports more targeted product planning.

<img width="452" height="117" alt="image" src="https://github.com/user-attachments/assets/c63c8ae7-221f-4461-a705-4b7b93a67294" />


### Quarter Filter

The quarter slicer allows users to analyse purchasing behaviour within a selected quarter.

<img width="114" height="105" alt="image" src="https://github.com/user-attachments/assets/4645a8ff-e34e-480d-af7e-a790161a0dad" />

### Premium Customer Filter

The premium customer slicer allows users to compare purchasing behaviour across **Budget, Mainstream, and Premium** customer segments.

<img width="113" height="89" alt="image" src="https://github.com/user-attachments/assets/d5cd0c47-5e51-4680-97e7-fbfd51cb7be1" />



---

# Recommendations

## Customer Targeting

Prioritize **Older Singles/Couples**, which generated the highest revenue, while developing targeted offers for other lifestage groups based on their purchasing patterns.

## Product Strategy

Focus product availability and promotions on strong-performing products and brands, particularly **Kettle**, **Smiths**, and the **175g packet size**, while using lifestage preferences to guide product selection.

## Marketing Campaigns

Develop **lifestage-specific campaigns** using the brand and packet-size preferences identified in the analysis. This can help make promotions more relevant to each customer segment.

## Premium Customer Strategy

Since **Mainstream customers generated the highest revenue**, marketing should not focus exclusively on Premium customers. The business should also develop strategies to retain Mainstream customers and encourage Budget and Premium customers to increase their spending.

## Seasonal Sales Planning

Increase promotional and inventory planning ahead of **Q4 and December**, which recorded the strongest sales performance. This can help the business prepare for periods of increased customer demand.


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

This project provided a data-driven analysis of **Woolsworth's retail sales and customer purchasing behaviour** using Python and Power BI. The analysis examined overall sales performance, customer lifestage and premium status, product and brand performance, packet-size preferences, purchasing frequency, and sales trends over time.

The findings provide useful insights into **who the customers are, what they purchase, and how they purchase**, helping support more informed decisions around customer targeting, product strategy, marketing campaigns, and seasonal sales planning.

---

## Author

**Esther Matthew**

Data Analyst | Power BI | Python | SQL | Excel
