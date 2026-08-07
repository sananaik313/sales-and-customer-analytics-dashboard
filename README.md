# Sales & Customer Analytics Dashboard

A Looker Studio dashboard providing a 360° view of sales performance, product profitability, and customer/operations metrics across 2023–2024.

## 📊 Overview

This dashboard is built in **Google Looker Studio** and is organized into three pages:

1. **Executive Overview** — high-level KPIs and trends
2. **Product Deep Dive** — category and product-level performance
3. **Customer & Operations** — customer segments, shipping, and top accounts

---

## 1️⃣ Executive Overview

**Key Metrics (Scorecards)**
| Metric | Value |
|---|---|
| Sales | 1M |
| Profit | 432K |
| Order_ID (order count) | 1K |
| Profit Margin % | 30.1% |

**Visuals**
- **Sales and Profit over time** — dual-line time series (Jan 2023–Dec 2024) tracking monthly Sales vs. Profit trends
- **State by Sales** — geo/bubble map showing sales concentration by state, color/size-scaled from ~26K to ~132K
- **Sales by Category** — bar chart comparing Technology, Office Supplies, and Furniture

---

## 2️⃣ Product Deep Dive

**Visuals**
- **Sales & Profit by Product Category** — horizontal bar chart across 10 sub-categories (Machines, Phones, Copiers, Accessories, Storage, Art, Bookcases, Paper, Chairs, Others)
- **Top 10 Most Profitable Products** — table with Product Name, Profit, Discount, and Sales (sortable, sorted by Profit)
- **Top 10 Products by Quantity** — line chart of unit volume across top Accessories & Art models
- **Sales by Category** — donut chart (Technology 51.5%, Office Supplies 28.9%, Furniture 19.6%)
- **Top 10 Products by Profit** — horizontal bar ranking, led by Accessories Model 1 (34.2K)

---

## 3️⃣ Customer & Operations

**Key Metrics (Scorecards)**
| Metric | Value |
|---|---|
| Total Customers | 150 |
| Average Order Value | 1197 |
| Average Ship Days | 4784 *(see data notes below)* |

**Visuals**
- **Sales by Shipping Mode** — bar chart (Standard, Second, First, Same Day)
- **Orders by Shipping Mode** — donut chart (Standard Class 55.6%, Second Class 21.3%, First Class 13.5%, Same Day 9.7%)
- **Sales by Customer Segment** — donut chart (Consumer 54.5%, Corporate 27.7%, Home Office 17.8%)
- **Top 10 Customers by Sales** — table with Customer Name, Sales, Profit, and Order count

---

## 🗂️ Suggested Data Source Structure

The dashboard assumes an underlying orders/sales dataset with fields similar to:

- `Order_ID`, `Order_Date`, `Ship_Date`, `Ship_Mode`
- `Customer_Name`, `Segment`, `State`
- `Category`, `Sub_Category`, `Product_Name`
- `Sales`, `Profit`, `Discount`, `Quantity`

*(This closely mirrors the structure of the classic "Sample Superstore" dataset.)*

---

## ⚠️ Data Notes / Known Issues

- **Average Ship Days (4784)** appears to be a sum/misconfigured aggregation rather than a true average — likely needs the calculated field's aggregation type changed to `AVG` (or divided by order count).
- **State by Sales map** is rendering as a world map rather than a US state map — check the geo dimension type (should be set to "State/Province" or "US State" instead of a generic geo field) and confirm the location is scoped to the US.
- Verify `Order_ID` is set to a **Count Distinct** aggregation where used as an order-count metric, since it also appears listed under customer tables.

---

## 🔧 How to Use / Edit This Dashboard

1. Open the dashboard in Looker Studio and click **Make a copy** (top-right menu) to create an editable version.
2. Reconnect the copy to your own data source under **Resource → Manage added data sources**.
3. Use the **date range control** (if added) to filter the time-series view.
4. Click into any table (e.g., Top 10 Customers, Top 10 Products) to re-sort by clicking column headers.
5. To update styling, use the **Theme and Layout** panel — the current theme uses a red/coral color palette.

---

## 📅 Reporting Period

Data covers **January 2023 – December 2024**.

---

## 📁 File Info

- **Tool**: Google Looker Studio
- **Pages**: 3 (Executive Overview, Product Deep Dive, Customer & Operations)
- **Export**: PDF snapshot (`Sales_And_Customer_Analytics_Dashboard.pdf`)
