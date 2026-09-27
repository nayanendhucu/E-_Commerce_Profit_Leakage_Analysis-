# E-Commerce Profit Leakage Analysis

### Advanced Excel Business Analytics Case Study

> **Investigating why high e-commerce revenue does not necessarily translate into strong contribution profitability.**

This project is an end-to-end **Excel-first business analytics case study** covering data-quality investigation, cleaning, analytical transformation, profitability modelling, profit-leakage analysis, scenario modelling and executive dashboarding.

## Executive Summary

The analysis works across approximately **75,000 order records** together with product, customer, returns and inventory data.

The central business question is:

> **Where is profitability leaking, and what operational or commercial factors are contributing to weak contribution margin?**

Rather than treating revenue as profit, the project evaluates **Contribution Margin** after COGS, shipping, payment fees, return costs and refund costs.

### Key metrics

| Metric | Result |
|---|---:|
| Order records | ~75K |
| Net Sales | ~858.1M |
| Contribution Margin | ~-239.3M |
| Contribution Margin % | ~-27.89% |
| Average Discount | ~12.72% |
| Negative-Margin Products | 1,187 |

> Metrics should be interpreted in the context of the workbook's assumptions and data limitations.

---

## Business Problem

High sales volume can create the appearance of strong business performance while significant costs reduce actual contribution profitability.

This project investigates:

- Which products generate revenue but weak or negative contribution?
- How does discount intensity relate to contribution margin?
- Which categories show higher return behaviour?
- Which products have negative contribution margins?
- What inventory risks can be identified from the available data?
- How does a controlled reduction in discounting affect contribution margin?
- Which cost drivers should management investigate?

---

## Project Workflow

```
RAW DATA
   ↓
DATA QUALITY INVESTIGATION
   ↓
CLEANING & STANDARDIZATION
   ↓
ANALYTICAL TRANSFORMATION
   ↓
KPI / CONTRIBUTION MODEL
   ↓
PROFITABILITY ANALYSIS
   ↓
PROFIT LEAKAGE ANALYSIS
   ↓
SCENARIO MODELLING
   ↓
EXECUTIVE DASHBOARD
   ↓
MANAGEMENT RECOMMENDATIONS
```

---

## Data Sources

The workbook contains datasets covering:

- Orders
- Products
- Customers
- Returns
- Inventory

Cleaned analytical datasets include:

- `tblOrders_clean`
- `tblProducts_clean`
- `tblCustomers_clean`
- `tblReturns_clean`
- `tblInventory_clean`

The raw and cleaned layers are maintained separately so the cleaning process remains auditable.

---

# 1. Data Quality Investigation

Before performing business analysis, the underlying datasets were systematically investigated.

### Checks included

- Duplicate records
- Missing values
- City inconsistencies
- State inconsistencies
- Category inconsistencies
- Invalid dates
- Negative quantities
- Mixed discount formats
- Cross-dataset matching
- Return/order matching
- Inventory consistency

Examples of issues investigated included duplicate Order IDs, missing Customer IDs, inconsistent state values, category spelling variations, invalid dates, negative quantities and mixed discount formats.

The purpose of this stage was to prevent data-quality problems from distorting downstream business conclusions.

---

# 2. Data Cleaning & Standardization

The project uses separate raw and cleaned datasets.

Cleaning included:

- Standardizing text values
- Mapping inconsistent city/state values
- Standardizing product categories
- Validating dates
- Validating numeric fields
- Investigating duplicates
- Investigating missing values
- Cross-dataset validation

Mapping tables were used where appropriate rather than silently overwriting source information.

---

# 3. Analytical Transformation

A dedicated `Orders_Analysis` layer was created to combine the information required for business analysis.

Key analytical fields include:

- Order ID
- Customer ID
- Product ID
- Quantity
- Unit Price
- Discount
- Order Date
- Selling Price
- Category
- Supplier
- Reorder Point
- Lead Time
- COGS
- Gross Sales
- Discount Amount
- Net Sales
- Shipping Cost
- Payment Fees
- Return Cost
- Refund Cost
- Contribution Margin
- Contribution Margin %
- Year
- Month
- Quarter
- Week
- Day of Week

### Contribution Margin

```
Contribution Margin
=
Net Sales
- COGS
- Shipping Cost
- Payment Fees
- Return Cost
- Refund Cost
```

This makes the analysis more useful than a revenue-only report because it considers several direct profitability drivers.

---

# 4. Product Profitability

Products are evaluated using:

- Units Sold
- Net Sales
- Contribution Margin
- Contribution Margin %
- Return Rate
- Profitability Classification

Products are classified into:

- Negative Margin
- Low Margin
- Medium Margin
- High Margin

The workbook identifies **1,187 negative-margin products**.

### Business interpretation

A product can generate substantial sales while still destroying contribution value when its associated costs exceed the contribution generated by its net sales.

---

# 5. Revenue Illusions

A dedicated analysis compares:

- Revenue
- Units Sold
- Contribution Margin %

The purpose is to identify cases where:

> **High revenue does not necessarily mean strong profitability.**

This shifts the analysis from a sales-only perspective toward a profitability perspective.

---

# 6. Discount Leakage

Discounts are segmented into:

- 0–5%
- 5–10%
- 10–15%
- 15–20%
- 20–30%
- 30%+

Each band is evaluated using:

- Order count
- Revenue
- Contribution Margin
- Contribution Margin %

The observed average discount is approximately **12.72%**.

The objective is to understand whether increasing discount intensity is associated with worsening contribution economics.

---

# 7. Return Behaviour

Return behaviour is analysed at category level using:

- Units Sold
- Returned Units
- Return Rate

Returns are also incorporated into contribution economics through:

- Return Cost
- Refund Cost

This allows the analysis to connect operational return behaviour with financial impact.

---

# 8. Inventory Risk

Inventory analysis evaluates:

- Product ID
- Stock
- Units Sold
- Reorder Point
- Risk Classification

Risk categories include:

- Stockout Risk
- Reorder Risk
- No Sales Recorded
- Normal

### Data limitation

The available inventory demand signals are limited. Inventory-level Units Sold is largely zero and the available stockout signals do not provide sufficient evidence for a reliable demand-based revenue-at-risk estimate.

Therefore, unsupported lost-sales values were **not manufactured** for the dashboard.

This is an important analytical decision: a business metric should not be presented as fact when the underlying data cannot support it.

---

# 9. Customer Profitability

Customer-level analysis evaluates:

- Revenue
- Contribution Margin
- Contribution Margin %

This helps distinguish customers who generate high sales from customers who generate strong contribution value.

---

# 10. Controlled Scenario Analysis

A controlled discount-reduction scenario model compares:

| Scenario | Average Discount | Contribution Margin | CM % |
|---|---:|---:|---:|
| Current | 12.72% | ~-239.3M | ~-27.89% |
| 10% Discount Reduction | ~11.45% | ~-180.3M | ~-19.66% |
| 15% Discount Reduction | ~10.81% | ~-173.7M | ~-18.81% |

### Important assumption

These are **illustrative scenarios, not forecasts**.

The model changes the discount assumption while holding COGS, shipping, payment fees, return costs and refund costs fixed.

Under these assumptions, lower discounting improves contribution margin, but discount reduction alone does not eliminate the overall negative contribution margin.

---

# 11. Executive Dashboard

The workbook includes an executive **Profit Leakage & Risk Control Tower** dashboard.

### KPI cards

- Net Sales
- Contribution Margin
- Contribution Margin %
- Return Rate
- Negative-Margin Products

### Visual analysis

- Product Profitability Matrix
- Contribution Margin by Discount Level
- Return Rate by Category
- Inventory Risk
- Discount Reduction Scenario Impact
- Category Revenue vs Contribution Margin

The dashboard is designed to move from high-level financial KPIs to specific profitability and operational risk areas.

---

# 12. Key Business Findings

### Revenue is not the same as profitability

High sales can coexist with weak or negative contribution margin at product level.

### Discounting is a profitability driver

The discount analysis and controlled scenarios show that discount intensity materially affects contribution economics under the model assumptions.

### Returns create additional leakage

Return and refund costs directly affect contribution margin and should be investigated at product/category level.

### Inventory conclusions require caution

The available inventory demand signals are not strong enough to support a reliable demand-based revenue-at-risk estimate.

### Discount reduction alone is insufficient

Improving contribution margin also requires investigation of:

- COGS
- Shipping
- Payment fees
- Return costs
- Refund costs
- Product pricing

---

# 13. Management Recommendations

1. Review negative- and low-margin products.
2. Investigate high-revenue products with weak contribution margins.
3. Test controlled discount reductions rather than relying on broad discounting.
4. Investigate products/categories with elevated return rates.
5. Improve inventory-sales data linkage.
6. Review COGS and supplier economics.
7. Review shipping and payment-fee structures.
8. Investigate return and refund costs.

---

# 14. Excel Techniques Used

### Core Excel functions

- XLOOKUP
- SUMIFS
- COUNTIFS
- SUMPRODUCT
- UNIQUE
- AVERAGEIFS
- IF
- IFERROR

### Analytical techniques

- Data-quality profiling
- Data standardization
- Mapping tables
- Cross-dataset validation
- KPI modelling
- Contribution-margin analysis
- Profitability classification
- Scenario modelling
- Dashboard design
- Business recommendation development

---

# 15. Analytical Judgment

One of the key principles demonstrated in this project is:

> **Knowing when not to estimate.**

The inventory data did not provide enough reliable demand information to support a defensible stockout-based revenue-at-risk number.

Instead of creating an impressive-looking but unsupported metric, the limitation was documented.

This reflects a core Data Analyst practice:

**Use the data to support conclusions — not to manufacture them.**

---
## Portfolio Workbook

The original Excel workbook contains the complete project workflow, including the full raw datasets, cleaned datasets, transformation layers, analytical calculations, and dashboard.

Because the complete working workbook is too large for practical GitHub hosting, I created a **GitHub-optimized portfolio version** of the workbook.

### GitHub Portfolio Version

The portfolio workbook retains the key cleaned datasets, analytical outputs, business analysis, scenario modelling and executive dashboard while removing the large raw-data components and unnecessary file weight.

This version is provided so recruiters and reviewers can open and explore the analytical work directly without needing to download the full working dataset.
### 📊 Excel Workbook

[Download the GitHub Portfolio Workbook](./Excel/E-Commerce_Profit_Leakage_Analysis_Portfolio_25MB_fixed.xlsx)

> **Portfolio note:** The complete working workbook is larger because it contains the full datasets and detailed project layers. A reduced portfolio version is provided here for practical GitHub hosting while preserving the key analytical outputs and dashboard.
### Workbook Versions

| Version | Purpose |
|---|---|
| Full Working Workbook | Complete analysis workflow, including full datasets and detailed Excel work |
| GitHub Portfolio Workbook | Reduced-size version containing the key cleaned/analytical outputs and dashboard |

> **Note:** The GitHub version is a presentation/portfolio copy of the project. The full working workbook is retained separately as the master analysis file.

# 16. Project Deliverables

The repository is intended to contain:

```
E-Commerce-Profit-Leakage-Analysis/
│
├── README.md
├── Excel/
│   └── E-Commerce_Profit_Leakage_Analysis.xlsx
├── Dashboard/
│   ├── dashboard.png
│   └── dashboard_closeup.png
├── Screenshots/
│   ├── data_quality.png
│   ├── product_profitability.png
│   ├── discount_leakage.png
│   ├── return_analysis.png
│   ├── inventory_risk.png
│   └── scenario_analysis.png
└── Documentation/
    ├── Data_Quality_Summary.md
    ├── Business_Findings.md
    └── Methodology.md
```

---

# 17. Resume Version

### E-Commerce Profit Leakage Analysis | Excel

- Analyzed ~75K e-commerce order records across orders, products, customers, returns and inventory data, performing data-quality investigation, cleaning, standardization and analytical transformation to build an end-to-end profitability model.

- Developed product profitability, discount leakage, return behaviour, customer profitability and inventory-risk analyses using XLOOKUP, SUMIFS, COUNTIFS, SUMPRODUCT, UNIQUE and contribution-margin modelling.

- Built an executive Excel dashboard and controlled discount-reduction scenario model, identifying revenue–profitability gaps and evaluating how discount changes affected contribution margin while documenting limitations in the underlying inventory data.

---

# 18. LinkedIn Project Description

**E-Commerce Profit Leakage Analysis | Advanced Excel**

Built an end-to-end Excel analytics project to investigate why high e-commerce revenue was not necessarily translating into strong contribution profitability.

Worked across ~75K orders plus product, customer, returns and inventory data, covering data-quality investigation, cleaning, transformation, contribution-margin modelling, product profitability, discount leakage, return behaviour, inventory risk, customer profitability and scenario analysis.

The final output includes an executive dashboard and controlled discount-reduction model, with explicit documentation of data limitations where the available inventory signals did not support reliable revenue-at-risk estimation.

---

## Tools

**Microsoft Excel | Data Cleaning | Business Analytics | Profitability Analysis | KPI Modelling | Scenario Analysis | Dashboarding**

---

## Project Status

**Excel analysis and dashboard: Completed**

Future extension:

- Power BI executive reporting
- Deeper cost-driver analysis
- Additional profitability segmentation
- Interactive management reporting
