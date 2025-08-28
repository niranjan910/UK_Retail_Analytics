# UK Online Retail Analytics (2010–2011)

This project follows the principle of the **Capstone / Data Analytics Methodology**, which involves the following steps:

1. `Business Problem Understanding` – Defining the real-world challenge and project objectives.  
2. `Data Loading` – Importing the dataset into the analysis environment (Excel, Python, SQL, etc.).  
3. `Data Understanding` – Exploring dataset structure, column types, shape, and missing values.  
4. `Data Exploration` – Performing column-level checks, distributions, and identifying anomalies.  
5. `Data Cleaning` – Handling missing values, duplicates, outliers, and inconsistencies.  
6. `Feature Engineering` – Creating new variables (e.g., Revenue, InvoiceMonth, flags for cancellations).  
7. `Data Analysis` – Aggregating and summarizing data to extract business insights.  
8. `EDA (Exploratory Data Analysis)` – Visualizing patterns, trends, and relationships using plots/charts.  
9. `Final Report / Storytelling` – Presenting findings through dashboards, reports, and business recommendations.  


`Business Problem`
An online retail company is struggling to improve revenue and customer retention. While they have large ammount of transactional data, they lack insights into which products drive sales which customer are most valuable and how purchasing patterns vary across regions and time.

The company wants to answer critical questions:
1. Who are the most valuable customers and how do we retain them?
2. Which products and categories generate the highest revenue and which products often seel together?
3. What are the seasonal or monthly sales patterns and how can inventory be managed accordingly?
4. Which markets (countries) should we focous for the expansion or targeted promotions?
5. How do we returns and cancellations (negative quantities) affect overall revenue?

`Data Loading`
This data set is taken from UCI and it consists of total 541909 rows and 8 columns 
- The name of all the rows are - `InvoiceNo`,`StockCode`,`Description`,`Quantity`,`InvoiceDate`,`UnitPrice`,`CustomerID`,`Country`
- The Data Types of each Columns are as -
1. `InvoiceNo`              object
2. `StockCode`              object
3. `Description`            object
4. `Quantity`                int64
5. `InvoiceDate`    datetime64[ns]
6. `UnitPrice`             float64
7. `CustomerID`            float64
8. `Country`                object
- The number of missing values in each column is -
1. `InvoiceNo`              0
2. `StockCode`              0
3. `Description`            1454
4. `Quantity`               0
5. `InvoiceDate`            0 
6. `UnitPrice`              0
7. `CustomerID`             135080
8. `Country`                0

`Data Exploration`
- `InvoiceNo`
1. **Basic Characteristics**
   - Total rows: **541,909**
   - Unique invoices: **25,900**
   - No missing values
   - Data type: `object`

2. **Duplicates**
   - Found **20,378 rows** where the same `InvoiceNo` and `StockCode` appear multiple times.  
   - This may indicate **duplicate entries** or cases where the same product was billed in separate lines.

3. **Cancellations**
   - Cancelled invoices are identified by an `InvoiceNo` starting with **"C"**.
   - Total cancelled invoices: **3,836**
   - Total cancelled rows: **9,288**
   - Business Insight: Cancellations represent **~14.8%** of all invoices (3836 / 25900), which is significant and should be accounted for in revenue calculations.

4. **Invoice Number Format**
   - Invoice length is consistent: **6 digits** for most records, with a few having **7 digits**.
   - Non-numeric invoices (all cancellations) detected, e.g. `C536379`, `C536383`.

5. **Basket Size (Items per Invoice)**
   - Average items per invoice: **20.5**
   - Median items per invoice: **10**
   - Minimum items per invoice: **1**
   - Maximum items per invoice: **1110**
   - Business Insight: Most customers purchase a small number of items, but some bulk orders exist (possible B2B clients).

6. **Quantity & Revenue per Invoice**
   - Average quantity per invoice: **~200**
   - Average revenue per invoice: **~£376**
   - Revenue ranges widely from **-£168,469** (due to cancellations/returns) to **£168,469**.
   - Business Insight: Negative revenues highlight the impact of cancellations/returns and must be adjusted for accurate sales reporting.

7. **Invoices per Customer**
   - Total unique customers: **4,372**
   - Average invoices per customer: **5.07**
   - Median invoices per customer: **3**
   - Some customers placed **up to 248 invoices**.
   - Business Insight: Indicates **loyal/repeat customers** and provides a base for **RFM analysis**.

8. **Invoices per Day**
   - Total active days: **305**
   - Average invoices per day: **~85**
   - Peak day: **218 invoices**
   - Business Insight: Sales activity varies by day, and daily trends can guide **inventory planning**.



This project analyzes a real-world **UK online retail dataset** containing **540,000+ transactions** from Dec 2010 to Dec 2011.  
The goal is to transform messy raw data into **clear business insights** through **data cleaning**, **DAX measures**, **visual analysis**, and **interactive Power BI dashboards**.

It answers key business questions, such as:
- 📈 What are the sales trends across the year?
- 🔄 Which products are cancelled or returned the most?
- 👥 Who are our most valuable customers?
- 🌍 Where are we selling the most — and where can we grow next?

---

## 📂 Dataset Overview

The dataset captures all sales orders for one year.  
Each row = **one product line** on an invoice.

| Column Name     | Description                                                                          |
|-----------------|--------------------------------------------------------------------------------------|
| `InvoiceNo`     | Unique order ID — if it starts with 'C', the invoice was cancelled.                  |
| `StockCode`     | Product/item code.                                                                   |
| `Description`   | Name or short description of the product.                                            |
| `Quantity`      | Number of units ordered. Negative = returned.                                        |
| `InvoiceDate`   | Date and timestamp when the order was placed.                                        |
| `UnitPrice`     | Price per unit (GBP).                                                                |
| `CustomerID`    | Unique customer ID. Some transactions have missing IDs.                              |
| `Country`       | Customer’s country.                                                                  |

---

## 🧹 Data Cleaning Highlights

Key actions taken to clean & prepare the data for analysis:

- 🔍 **Missing values**: Filled unknown product names with **"Unknown Product"**, missing Customer IDs with placeholder **99999**.
- 📌 **New columns**:
  - `Is_Cancelled` — flags invoices starting with ‘C’
  - `Is_Return` — flags negative quantities
- ✏️ **Text cleanup**: Standardized case, trimmed spaces, removed junk like “?”, “missing”, etc.
- 📅 **Date split**: Separated `InvoiceDate` into **Invoice_Date** and **Invoice_Time** for better time-based analysis.
- 🗂️ **StockCode categories**: Grouped special codes (e.g., POST, Gift, Service) into `StockCode_Type` for better product classification.

---

## 📊 Dashboards & Key Analysis

This project delivers **6 interactive dashboards**, each tackling a different **business goal**.

---

### 1️⃣ Sales Overview  
![Sales Overview](Dashboards/Sales%20Overview.png)

**Key Findings:**
- Strong holiday spike in **November**; revenue peaks near £1.9M.
- **April** is the lowest revenue month.
- Mid-year (May–Aug) shows steady sales ~£0.72M–£0.77M.
- Clear seasonal patterns — useful for forecasting.

---

### 2️⃣ Cancellations & Returns  
![Returns & Cancellations](Dashboards/Return%20&%20Cancellation.png)

**Key Findings:**
- Overall cancellation/return rates are very low (~1%).
- Most issues occur within the **UK**, peaking in holiday months (Sept–Nov).
- Specific products show high return volumes (e.g., certain gift items).
- Estimated **revenue loss from returns**: £881K+.

---

### 3️⃣ Order Patterns  
![Order Patterns](Dashboards/Order%20Pattern.png)

**Key Findings:**
- Order volumes peak in **November (~3.7K orders)**.
- **February** is the lowest (post-holiday slump).
- Core buying hours: **10 AM–3 PM**, especially around lunch.
- Busiest days: first 10 days of each month.

---

### 4️⃣ Customer Insights  
![Customer Insights](Dashboards/Customer%20Insight.png)

**Key Findings:**
- **High-value customers (37%) generate 80%+ of revenue.**
- Majority are **low-value** — an opportunity for marketing.
- Most customers are from **UK**, **Germany**, **France**, **Netherlands**, **Italy**.
- International sales are growing in **Asia, Australia**, and parts of **Africa**.

---

### 5️⃣ Geographic Sales  
![Geographic Sales](Dashboards/Geographic%20sales.png)

**Key Findings:**
- **UK = 84%** of total revenue.
- Non-UK sales: **15%** — steady but with expansion potential.
- **Ireland, Germany, Netherlands** are strong non-UK markets.
- New sales opportunities exist in **Europe & Asia**.

---

### 6️⃣ Product Performance  
![Product Performance](Dashboards/Product%20Performance.png)

**Key Findings:**
- **3,900+ unique products** sold — wide range.
- Top items include **Zinc T-Light Holder Stars**, **Winkie Candle Stick**, etc.
- Some products result in net loss due to excessive returns.
- Long-tail items sell infrequently — may need rationalizing for better inventory control.

---

## 🚧 Challenges & Learnings

Working with real retail data brought real-life roadblocks:
- 📌 Lots of **missing or dirty product names**.
- 📌 **Returns/cancellations** mixed into the same field (`Quantity`).
- 📌 No clear product categories — inferred manually.
- 📌 **High data volume (~540K rows)** — handled with DAX optimizations in Power BI.
- 📌 Partial or missing customer data — handled with placeholders.
- 📌 Time-based trends needed custom columns for daily/hourly breakdowns.

---

## 📁 Repository Contents

This repo is a **complete end-to-end Power BI analytics showcase**, ideal for students, data analysts, or hiring managers.

- ✅ **Clean dataset** ready for BI work.
- ✅ **All DAX measures documented**.
- ✅ **Power BI (.pbix) file** with visuals and interactive filters.
- ✅ **Documentation** covering data cleaning, DAX logic, and key observations.
- ✅ **Visual dashboards** that answer real business questions.

---

> 📈 **Goal:** Show how messy raw data can turn into meaningful, actionable insights for better decisions.

---

**Enjoy exploring — and feel free to fork or build on it! 🚀**
