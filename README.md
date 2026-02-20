# 📊 Sales & Profit Overview | Product Performance & Profitability Dashboard

> **An end-to-end Power BI analytics project analyzing 8,314 orders across 2021–2024, covering $1.93M in total sales and $247.96K in profit uncovering product profitability gaps, category performance, and geographic revenue distribution to drive smarter business decisions.**

---

## Table of Contents

- [Business Context & Objectives](#-business-context--objectives)
- [Data Sources & Preparation](#-data-sources--preparation)
- [Analytical Methodology & Approach](#-analytical-methodology--approach)
- [Dashboard Pages](#-dashboard-pages)
- [Key Metrics Summary](#-key-metrics-summary)
- [Key Insights & Findings](#-key-insights--findings)
- [Product Profitability Analysis](#-product-profitability-analysis)
- [Geographic & Customer Analysis](#-geographic--customer-analysis)
- [Business Recommendations](#-business-recommendations)
- [Implementation, Monitoring & Next Steps](#-implementation-monitoring--next-steps)
- [Tools & Technologies](#-tools--technologies)
- [Data Model & DAX](#-data-model--dax)
- [How to Use This Dashboard](#-how-to-use-this-dashboard)
- [Author](#-author)

---

## Business Context & Objectives

### The Business Problem
Retail and e-commerce businesses often operate with a dangerous blind spot strong top-line sales figures that mask serious profitability problems underneath. A product category can generate millions in revenue while simultaneously destroying profit through discounting, returns, and operational inefficiencies.

This project was built to eliminate that blind spot. The goal was to build a comprehensive sales and profitability intelligence system that allows business leaders to see not just what is selling but what is actually making money, what is losing money, and where strategic action is needed.

### Business Objectives

**1. Track Core Sales & Profit KPIs with Year-over-Year Comparison**
Monitor total orders, sales, quantity, and profit with prior year benchmarks and percentage growth indicators to assess business trajectory.

**2. Identify Profitable vs Loss-Making Products and Categories**
Move beyond revenue reporting to true profitability analysis identifying which products and subcategories are generating returns and which are eroding the bottom line.

**3. Analyse Seasonal Sales and Profit Patterns**
Understand monthly trends in sales and profit to identify seasonal peaks, dips, and anomalies that require operational response.

**4. Map Revenue and Profit Performance by Geography**
Identify highest and lowest performing states to support targeted sales strategies and regional resource allocation decisions.

**5. Segment and Rank Customers by Value**
Identify high-value customers driving disproportionate revenue and profit and flag customers generating sales at a net loss.

---

## 📂 Data Sources & Preparation

### Data Source
| Detail | Description |
|---|---|
| Dataset | Retail orders dataset (2021–2024) |
| Total Records | 8,314 orders |
| Period Covered | January 1, 2021 – December 31, 2024 |
| Key Fields | OrderID, OrderDate, CustomerID, CustomerName, ProductName, Category, Sub-Category, Quantity, UnitPrice, Discount, Sales, Profit, State, Country |

### Data Cleaning & Preparation Steps

**Data Validation:**
- Checked for and removed duplicate OrderIDs
- Validated date fields ensured all OrderDate values fall within the 2021–2024 range
- Confirmed no NULL values in critical fields (Sales, Profit, Category, State)
- Cross-checked total Sales and Profit figures against source aggregates

**Calculated Columns Created:**
- `Profit Margin %` = `DIVIDE([Total Profit], [Total Sales])`
- `Year` = `YEAR(OrderDate)` for time-based filtering
- `Month` = `MONTH(OrderDate)` for seasonal analysis
- `Revenue Net of Discount` = `(Quantity * UnitPrice) - Discount`

**Power Query Transformations:**
- Standardized Category names (removed trailing spaces and inconsistencies)
- Split Product breakdown into Category → Sub-Category → Product hierarchy
- Created a Calendar table for time intelligence functions
- Filtered out test/cancelled orders with $0 sales value

---

## 🔬 Analytical Methodology & Approach

### The Analytical Framework
This project uses a **three-layer profitability analysis framework:**

```
Layer 1 - Portfolio Overview (Are we growing?)
       ↓
Layer 2 - Profitability Diagnostics (Where are we making and losing money?)
       ↓
Layer 3 - Geographic & Customer Intelligence (Who and where is driving performance?)
```

### Dashboard Design Approach
Three dedicated pages were built — each answering a specific business question:

- **Overview** → *How is the business performing overall?*
- **Profitability** → *Which products and categories are profitable vs loss-making?*
- **Sales & Geography** → *Who are our best customers and which states drive the most value?*

### Profitability Classification Methodology
Products were classified into three performance tiers using profit thresholds:

| Tier | Criteria |
|---|---|
| 🟢 Top Performer | Total Revenue ≥ $1,400,000 |
| 🟡 Average Performer | Total Revenue $1,300,000 – $1,399,999 |
| 🔴 Low Performer | Total Revenue < $1,300,000 |

Sub-categories were ranked by profit margin percentage to identify **stars** (high margin) vs **dogs** (negative or near-zero margin).

---

## 📊 Dashboard Pages

### Page 1 — Overview
The executive summary page. Displays total orders, sales, quantity, and profit KPIs with prior year comparisons and YoY growth percentages. Features a monthly sales and profit trend line chart, a category quantity donut chart, and a product breakdown drill-down from Category → Sub-Category → Product.

![Overview Dashboard](Sales%20Overview.png)

### Page 2 — Profitability
The profitability diagnostic page. Shows unprofitable orders percentage, total loss figure, a Sales vs Profit scatter plot to identify problem products, profit margin % by sub-category bar chart, and ranked tables of the Top 10 most profitable and Bottom 10 most loss-making products.

![Profitability Dashboard](Sales%20Profitability.png)

### Page 3 — Sales & Geography
The geographic and customer intelligence page. Features total sales by year bar chart, a US state map showing sales distribution, a top 10 states table with profit margin analysis, and a top customer value table showing sales, profit, and margin by customer.

![Geography Dashboard](Sales%20Geography.png)

---

## 📈 Key Metrics Summary

| Metric | Current Year | Prior Year | YoY Growth |
|---|---|---|---|
| Total Orders | 8,314 | 6,680 | ▲ 24.5% |
| Total Sales | $1,930,000 | $1,563,593 | ▲ 23.36% |
| Total Quantity | 32,000 | 25,388 | ▲ 24.11% |
| Total Profit | $247,960 | $192,962 | ▲ 28.50% |

---

##  Key Insights & Findings

### 1. Profit is Growing Faster Than Sales — A Positive Signal
Total profit grew 28.50% YoY while sales grew 23.36% meaning **profit is outpacing revenue growth.** This indicates improving operational efficiency or a gradual shift toward higher-margin products. This trend should be actively protected and accelerated.

### 2. Furniture is Generating Sales but Destroying Profit
Furniture generated $17.89K in quantity sold but produced a **net loss of $12,327.** This is the single most critical finding in the entire report — a category that is actively consuming resources while delivering negative returns. Tables and Bookcases are the primary offenders with consistently negative profit margins.

### 3. 18.6% of All Orders Are Unprofitable
Nearly 1 in 5 orders results in a loss representing **$123,375 in total losses** across the portfolio. This is not a rounding error it is a structural profitability problem that requires systematic investigation.

### 4. Office Supplies is the Profit Engine
Despite not being the highest revenue category, Office Supplies generated **$45,255 in profit** the highest of all three categories. Within Office Supplies, Paper ($27,976) and Storage ($17,478) are the star sub-categories.

### 5. Technology Leads Revenue but Has Inconsistent Margins
Technology generated $37,562 in profit on the highest revenue volume ($121.86K quantity). However, the Machines and Supplies sub-categories show near-zero or negative margins — dragging down what should be the highest-performing category.

### 6. October is a Consistent Profit Dip Month
The monthly trend reveals a **notable profit dip in October** every year before a strong Q4 recovery. This pattern suggests seasonal demand shifts or promotional discounting in October that compresses margins — warranting a pricing strategy review for that month specifically.

### 7. Sales Peaked in 2023 Then Declined in 2024
Annual sales trajectory: 2021 ($484K) → 2022 ($470.5K) → 2023 ($609.1K) → 2024 ($365.3K). The 2024 figure appears lower likely reflecting a partial year in the dataset. The 2023 peak represents the strongest performance year and should be benchmarked against.

---

##  Product Profitability Analysis

### Top 10 Most Profitable Products

| Product | Total Profit | Total Sales | Profit Margin |
|---|---|---|---|
| Ativa V4110MDD Micro-Cut Shredder | $3,772.95 | $7,699.89 | 49.0% |
| Zebra ZM400 Thermal Label Printer | $3,343.53 | $6,965.70 | 48.0% |
| Fellowes PB500 Electric Punch | $9,278.24 | $20,081.64 | 46.2% |
| Ibico EPK-21 Electric Binding System | $6,274.77 | $13,985.93 | 44.86% |
| Canon imageCLASS 2200 Advanced Copier | $16,239.96 | $39,899.89 | 40.7% |
| Plantronics Savi W720 Wireless Headset | $3,696.28 | $9,367.29 | 39.46% |
| Canon PC1060 Personal Laser Copier | $4,570.94 | $11,619.83 | 39.34% |

### Bottom 10 Loss-Making Products

| Product | Total Loss | Total Sales | Profit Margin |
|---|---|---|---|
| Cubify CubeX 3D Printer | ($8,879.97) | $11,099.96 | -80.0% |
| Lexmark MX611dhe Laser Printer | ($4,589.97) | $16,829.90 | -27.27% |
| Cisco TelePresence EX90 | ($1,811.08) | $22,638.48 | -8.0% |
| Chromcraft Bull-Nose Oval Conference Table | ($1,774.15) | $6,281.17 | -28.25% |
| Bush Advantage Collection Racetrack Table | ($1,187.79) | $7,508.51 | -15.82% |
| Bretford Height-Adjustable Table | ($1,081.07) | $3,965.30 | -27.26% |
| Hon 94000 Series Round Tables | ($921.13) | $4,738.87 | -19.44% |

### Profit Margin by Sub-Category (Best to Worst)
🟢 **Stars:** Labels, Paper, Envelopes, Copiers, Fasteners, Accessories
🟡 **Average:** Art, Binders, Appliances, Furnishings, Phones, Storage, Chairs
🔴 **Dogs:** Machines, Supplies, Bookcases, Tables

---

## Geographic & Customer Analysis

### Top 6 States by Sales & Profit

| State | Total Profit | Total Sales | Total Orders | Profit Margin |
|---|---|---|---|---|
| California | $63,144.57 | $390,145.54 | 1,674 | 16.18% |
| New York | $57,223.84 | $246,517.74 | 921 | 23.21% |
| Texas | ($21,067.08) | $151,436.60 | 832 | -13.91% |
| Washington | $30,236.17 | $117,661.47 | 409 | 25.70% |
| Pennsylvania | ($11,853.20) | $95,494.86 | 479 | -12.41% |
| Florida | ($3,870.14) | $79,303.61 | 321 | -4.88% |

**Critical Finding:** Texas is the 3rd highest revenue state but generates a **$21,067 net loss** making it the most financially damaging state in the portfolio. Every sale in Texas is currently destroying value.

### Top Customer Value Analysis

| Customer | Total Sales | Total Profit | Orders | Margin |
|---|---|---|---|---|
| Raymond Buch | $14,986.78 | $6,939.17 | 16 | 46.30% |
| Sanjit Chand | $14,142.34 | $5,757.42 | 22 | 40.71% |
| Adrian Barton | $13,037.43 | $5,202.84 | 14 | 39.91% |
| Ken Lonsdale | $14,153.23 | $805.46 | 28 | 5.69% |
| Becky Martin | $11,789.64 | ($1,659.97) | 16 | -14.08% |

---

##  Business Recommendations

### 1.  Urgently Review the Furniture Category
Furniture is generating a net loss of $12,327 specifically Tables (-$1,774 to -$1,081 per product) and Bookcases. Three options should be evaluated: (a) reprice furniture products to reflect true cost, (b) renegotiate supplier costs to restore margin, or (c) discontinue the worst-performing SKUs entirely. Doing nothing is not an option.

### 2.  Address the Texas Problem Immediately
Texas generates $151K in sales but loses $21K in profit the worst state-level performance in the portfolio. A regional pricing audit should be conducted to identify whether the losses are driven by excessive discounting, high shipping costs, or product mix. Until resolved, marketing spend in Texas should be frozen.

### 3.  Double Down on Office Supplies — Especially Paper and Labels
Paper (49%+ margins on top products) and Labels are the highest-margin sub-categories in the entire business. Increasing inventory depth, improving availability, and running targeted promotions in these sub-categories would directly improve overall portfolio profitability.

### 4.  Investigate the October Profit Dip
The recurring October profit dip suggests either seasonal promotional discounting or demand-driven cost spikes. A pricing and discount analysis specifically for October orders should be conducted to determine the root cause and implement a margin protection strategy.

### 5.  Prioritize High-Margin Customers for Retention
Raymond Buch (46.3% margin), Sanjit Chand (40.71%), and Adrian Barton (39.91%) are the most profitable customers by margin. These customers should be in an active retention programme — dedicated account management, early access to new products, and loyalty incentives. Losing one of these customers has an outsized impact on profitability.

### 6.  Investigate Loss-Making Customer Relationships
Becky Martin generates $11,789 in sales but produces a $1,659 net loss across 16 orders. This pattern high volume, negative profit — suggests excessive discounting or product returns. A customer-level profitability review should be conducted for all customers with negative margins.

---

##  Implementation, Monitoring & Next Steps

### Current Implementation
This dashboard is built on a 4-year historical dataset (2021–2024) and is designed for quarterly business reviews and monthly profitability monitoring. All KPIs update dynamically when filtered by year using the year buttons at the top of each page.

### Recommended Monitoring Cadence

| Metric | Monitoring Frequency | Alert Threshold |
|---|---|---|
| Overall Profit Margin % | Monthly | Flag if < 10% |
| Furniture Category Profit | Monthly | Flag if still negative after action |
| Unprofitable Orders % | Monthly | Flag if > 20% |
| Texas State Profit | Monthly | Flag if still negative after review |
| Top 10 Customer Retention | Quarterly | Flag if any top 5 customer churns |
| October Profit Margin | Annually | Flag if < prior year October |

### Next Steps for This Project

**Short Term (1–3 months):**
- Connect to live sales database for real-time dashboard refresh
- Add a discount impact analysis quantifying exactly how much profit is lost to discounting per product and category
- Build a what-if parameter allowing stakeholders to simulate the profit impact of price changes

**Medium Term (3–6 months):**
- Develop a customer lifetime value (CLV) model to predict future customer profitability
- Add a returns analysis page quantifying the profit impact of product returns by category
- Integrate shipping cost data to identify whether logistics costs are driving state-level losses

**Long Term (6–12 months):**
- Build a demand forecasting model using historical sales patterns to optimise inventory levels
- Expand geographic analysis to ZIP code level for hyper-local sales strategy
- Develop an automated profitability alert system — notifying managers when any category, state, or product crosses a negative margin threshold

---

##  Tools & Technologies

| Tool | Purpose |
|---|---|
| **Power BI Desktop** | Dashboard development and visualization |
| **DAX** | KPI measures, YoY comparisons, profitability classification |
| **Power Query (M)** | Data cleaning, transformation, and calendar table |
| **Microsoft Excel** | Initial data validation and exploration |

---

##  Data Model & DAX

### Key DAX Measures

```dax
-- Total Sales
Total Sales = SUM(Orders[Sales])

-- Total Profit
Total Profit = SUM(Orders[Profit])

-- Profit Margin %
Profit Margin % = DIVIDE([Total Profit], [Total Sales])

-- Total Orders
Total Orders = DISTINCTCOUNT(Orders[OrderID])

-- Prior Year Sales
PY Sales = CALCULATE([Total Sales], SAMEPERIODLASTYEAR('Calendar'[Date]))

-- YoY Sales Growth %
YoY Sales % = DIVIDE([Total Sales] - [PY Sales], [PY Sales])

-- Prior Year Profit
PY Profit = CALCULATE([Total Profit], SAMEPERIODLASTYEAR('Calendar'[Date]))

-- YoY Profit Growth %
YoY Profit % = DIVIDE([Total Profit] - [PY Profit], [PY Profit])

-- Unprofitable Orders %
Unprofitable Orders % = 
DIVIDE(
    CALCULATE(COUNT(Orders[OrderID]), Orders[Profit] < 0),
    COUNT(Orders[OrderID])
)

-- Total Loss (from unprofitable orders)
Total Loss = 
CALCULATE(
    SUM(Orders[Profit]), 
    Orders[Profit] < 0
)

-- Product Performance Classification
Product Tier = 
SWITCH(TRUE(),
    [Total Sales] >= 1400000, "Top Performer",
    [Total Sales] >= 1300000, "Average Performer",
    "Low Performer"
)
```

---

## 📂 How to Use This Dashboard

1. **Clone or download** this repository
2. Open `Sales and Profit Overview.pbix` in **Power BI Desktop**
3. Use the **Year buttons** (2021, 2022, 2023, 2024) at the top to filter by year
4. Use the **Date range slicer** for custom period analysis
5. Navigate between **Overview**, **Profitability**, and **Sales & Geography** pages
6. On the Profitability page — use the **Category and Sub-Category filters** to drill into specific product areas
7. Click any **state on the map** to filter all visuals to that state's performance
8. Use the **Product Breakdown** sankey chart on the Overview page to drill from Category → Sub-Category → Product

---

## 👤 Author

**Faleye Olumide David**
Data Analyst | Power BI Sales Analyst | Business Intelligence Analyst

📍 Nigeria
🔗 [LinkedIn](https://www.linkedin.com/in/olumide-david-79b17526a/)
🌐 Portfolio: *datascienceportfol.io* (coming soon)

---

> 💬 *"Revenue tells you what customers are buying. Profit tells you what your business is actually worth."*

---

⭐ If you found this project useful or insightful, consider giving it a star on GitHub!
