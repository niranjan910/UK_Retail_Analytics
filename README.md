# 🛍️ UK Online Retail Analytics (2010–2011)

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
👉 Dashboard images live in the `images/` folder. *(Replace sample paths once added!)*

---

### 1️⃣ Sales Overview
![Sales Overview](images/sales-overview.png)

**Key Findings:**
- Strong holiday spike in **November**; revenue peaks near £1.9M.
- **April** is the lowest revenue month.
- Mid-year (May–Aug) shows steady sales ~£0.72M–£0.77M.
- Clear seasonal patterns — useful for forecasting.

---

### 2️⃣ Cancellations & Returns
![Returns & Cancellations](images/returns-cancellations.png)

**Key Findings:**
- Overall cancellation/return rates are very low (~1%).
- Most issues occur within the **UK**, peaking in holiday months (Sept–Nov).
- Specific products show high return volumes (e.g., certain gift items).
- Estimated **revenue loss from returns**: £881K+.

---

### 3️⃣ Order Patterns
![Order Patterns](images/order-patterns.png)

**Key Findings:**
- Order volumes peak in **November (~3.7K orders)**.
- **February** is the lowest (post-holiday slump).
- Core buying hours: **10 AM–3 PM**, especially around lunch.
- Busiest days: first 10 days of each month.

---

### 4️⃣ Customer Insights
![Customer Insights](images/customer-insights.png)

**Key Findings:**
- **High-value customers (37%) generate 80%+ of revenue.**
- Majority are **low-value** — an opportunity for marketing.
- Most customers are from **UK**, **Germany**, **France**, **Netherlands**, **Italy**.
- International sales are growing in **Asia, Australia**, and parts of **Africa**.

---

### 5️⃣ Geographic Sales
![Geographic Sales](images/geographic-sales.png)

**Key Findings:**
- **UK = 84%** of total revenue.
- Non-UK sales: **15%** — steady but with expansion potential.
- **Ireland, Germany, Netherlands** are strong non-UK markets.
- New sales opportunities exist in **Europe & Asia**.

---

### 6️⃣ Product Performance
![Product Performance](images/product-performance.png)

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

**Enjoy exploring — and feel free to fork or build on it!**
