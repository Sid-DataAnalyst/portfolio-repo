# Superstore Sales Performance Dashboard
### Retail Sales & Profitability Analytics in Power BI

**Tool:** Microsoft Power BI Desktop

## 1. Project Overview
This project uses the well-known Sales Superstore dataset — a retail transactions dataset covering orders, products, customers, and shipping — to build an interactive Power BI sales performance dashboard. It tracks total sales, profit, order volume, and customer counts, and breaks performance down by product category, sub-category, customer segment, and time period.

The dashboard is a multi-page report: a summary landing page ("Sales DB") plus two supporting drill-through pages ("P1" and "P2") that let a user click into a specific metric (e.g., Total Profit) and land on a more detailed breakdown.

## 2. Business Objective
- What are our total sales, profit, order volume, and customer count for the selected period?
- Which product categories and sub-categories generate the most (and least) sales?
- How does sales performance trend across the year, by quarter and month?
- How is revenue distributed across customer segments (Corporate, Home Office, Consumer, Small Business)?
- How do sales vary by region and by shipping method?
- Where should the business focus to grow high-margin categories and shed low-performing sub-categories?

## 3. Dataset Description
Source: `data/Sales_Superstore_Dataset` — standard retail analytics training dataset (Orders/Sales fact table + Returns table + product/customer/geography fields).

| Field | Description |
|---|---|
| Order ID / Row ID | Unique identifiers for each order line item |
| Order Priority | Priority level (e.g., High, Medium, Critical) |
| Product Name / Category / Sub-Category | Product hierarchy |
| Product Container / Base Margin | Packaging and margin attributes |
| Region / State or Province / Postal Code | Geographic dimensions |
| Customer Segment | Corporate, Home Office, Consumer, Small Business |
| Sales / Profit / Quantity Ordered / Unit Price | Core transactional measures |
| Shipping Cost / Ship Mode / Ship Date | Fulfillment details |
| Returns (Order ID) | Related table flagging returned orders |

## 4. Tools & Skills Demonstrated

| Area | Details |
|---|---|
| BI Tool | Microsoft Power BI Desktop |
| Data Modeling | Multi-table model (Orders/Sales fact + Returns table) joined by Order ID |
| DAX | Aggregation measures for sales, profit, order count, distinct customer count |
| Visuals Used | KPI cards, horizontal bar charts, line/trend chart, donut chart, slicers |
| Interactivity | Multi-select slicers (Date range, Product Category, Region, Customer Segment, Ship Mode) |
| Navigation | Drill-through configured on Total Profit, routing to detail pages P1 and P2 |
| Design | Clean card-based KPI layout, consistent blue corporate theme |

## 5. Data Model
- **Fact table:** Orders/Sales — one row per order line (Sales, Profit, Quantity Ordered, Unit Price, Shipping Cost, product/customer/region keys).
- **Returns table:** linked via Order ID, used to flag/exclude returned orders.
- **Date table:** Year → Quarter → Month hierarchy driving the trend line and date slicer.
- **Geography/product hierarchies:** Region → State/Province → Postal Code; Category → Sub-Category → Product Name.

## 6. Key Measures

| Measure | Purpose |
|---|---|
| Total Sales | SUM of Sales |
| Total Profit | SUM of Profit |
| Total Orders | Distinct count of Order ID / Row ID |
| Total Customers | Distinct count of customers |

Extendable: Average Order Value, Profit Margin %, Average Shipping Cost.

## 7. Dashboard Pages

**Page 1 — Sales DB (Landing Page):** KPI strip (Total Sales 2.85M, Total Profit 447.20K, Total Orders 2,185, Total Customers 1,589), Total Sales by Sub-Category (bar), Total Sales by Year/Quarter/Month (line), Total Sales by Category (bar), Total Sales by Customer Segment (donut), filter panel.

**Pages 2 & 3 — P1 and P2 (Drill-Through Detail):** Configured as drill-through targets on Total Profit with "Keep all filters" enabled, for order-level or profit-focused breakdowns.

## 8. Key Insights
- **Overall performance:** $2.85M in sales, $447.2K in profit (~15.7% margin) for the period shown (Jan–Nov 2013).
- **Category mix:** Technology leads at $1.21M, ahead of Furniture ($0.90M) and Office Supplies ($0.75M).
- **Sub-category concentration:** Office Machines/Supplies, Telephones, and Chairs are the top 3 (~$0.37M–$0.44M each); Labels, Scissors, and Rubber Bands are negligible.
- **Segment split:** Corporate leads at 38.6% (~$1.1M); Consumer, Small Business, Home Office each ~19–22%.
- **Seasonality:** Dips to ~$0.14M–0.17M mid-year, peaks ~$0.38M around September.

## 9. How to Use
Adjust the date range slider; use Category/Region/Segment/Ship Mode checkboxes to slice every visual; hover for exact values; right-click to drill through to P1/P2 with filters preserved.

## 10. Potential Enhancements
- Profit Margin % measure
- Geographic map visual (Region/State)
- Return Rate % from the Returns table
- Year-over-Year comparison
- Top/Bottom 10 Products table
- Average Order Value and Average Shipping Cost measures

## 11. Project Files

| File | Description |
|---|---|
| `data/Sales_Superstore_Dataset` | Source retail transactions data |
| `Sales_Analysis_Overview.pbix` | Power BI report file |
| `README.md` | This documentation |
