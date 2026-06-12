# Global Phone Sales & Portfolio Analytics

[![Power BI](https://img.shields.io/badge/Business_Intelligence-Power_BI-yellow?style=flat\&logo=powerbi)](https://powerbi.microsoft.com/)
[![Data Modeling](https://img.shields.io/badge/Data_Modeling-Dimensional_Model-blue?style=flat)](#)
[![DAX](https://img.shields.io/badge/Analytics-DAX-orange?style=flat)](#)

## Executive Overview

Global Phone Sales & Portfolio Analytics is a Power BI business intelligence solution developed to evaluate smartphone portfolio performance, regional sales trends, and mobile operator distribution effectiveness across international markets.

The project combines dimensional data modeling, DAX-based analytical calculations, and interactive visual reporting to provide insights into revenue generation, profitability, market performance, and channel distribution patterns.

The dashboard simulates a commercial reporting environment where business stakeholders can monitor product performance, evaluate profitability, and identify opportunities for operational improvement across brands, countries, and telecom operators.

---

## Dashboard Preview

<img width="1272" height="722" alt="image" src="https://github.com/user-attachments/assets/22e0c5be-a122-4370-9376-698072d8369e" />


---

## Business Problem

Revenue alone does not provide a complete picture of business performance. Organizations often require additional visibility into profitability, channel effectiveness, and regional performance to support strategic decision-making.

Key business challenges addressed by this project include:

* Identifying products that generate strong revenue but lower profitability.
* Evaluating dependence on specific telecom operators and distribution channels.
* Detecting regional variations in profit margins and sales performance.
* Providing consolidated portfolio-level insights for commercial decision-making.

---

## Objectives

* Analyze smartphone portfolio performance across multiple brands.
* Compare revenue generation and profitability across products and markets.
* Assess distribution patterns across telecom operators.
* Monitor country-level sales performance and margin efficiency.
* Deliver a centralized reporting solution for business stakeholders.

---

## Dataset Overview

The solution is built using two primary datasets:

| Dataset Component | Type            | Records | Primary Columns                                                                       |
| ----------------- | --------------- | ------- | ------------------------------------------------------------------------------------- |
| Phone Sales       | Fact Table      | 2,998   | Date, Country, Distributor, Brand, Operator, Unit Cost, Amount, Unit Price, Sales     |
| Date_Phones       | Dimension Table | 1,825   | Date, Year, Quarter, Month, Month Name, Month & Year, Week Day, Day Name, Week Number |

---

## Data Architecture

The data model follows a dimensional design consisting of a transactional fact table connected to a dedicated calendar dimension. This structure supports efficient filtering, time-based analysis, and optimized report performance within Power BI.

### Relationship Structure

```text
Phone Sales (Fact Table)
        │
        │ Many-to-One (*:1)
        │ Single Direction Filter
        ▼
Date_Phones (Dimension Table)
```

### Model Benefits

* Efficient filter propagation across reporting visuals.
* Simplified data model design.
* Support for time-intelligence calculations.
* Improved report performance and maintainability.

---

## Analytical DAX Engine

Key business metrics were developed using explicit DAX measures to ensure accurate calculations across different filter contexts and reporting dimensions.

### Total Revenue

Measures total sales revenue generated across all transactions.

```DAX
Total_Revenue =
SUM('Phone Sales'[Sales])
```

### Total Profit

Calculates profitability at the transaction level using row-by-row evaluation.

```DAX
Total_Profit =
SUMX(
    'Phone Sales',
    ('Phone Sales'[Unit Price] - 'Phone Sales'[Unit Cost])
    * 'Phone Sales'[Amount]
)
```

### Profit Margin %

Measures profitability relative to total revenue.

```DAX
Profit_Margin_% =
DIVIDE(
    [Total_Profit],
    [Total_Revenue],
    0
)
```

---

## Dashboard Design

The dashboard is organized into three analytical layers designed to guide users from high-level performance indicators to detailed operational insights.

## Executive KPI Summary

* **Total Revenue ($39.34M):** Represents the top-line absolute gross sales volume generated across all global transactions.
* **Net Profit ($14.19M) & Profit Margin (36.07%):** Calculated through a precise row-by-row iteration layer. In global consumer electronics retail, a sustained **36.07% cumulative profit margin** indicates an exceptionally healthy pricing structure and excellent baseline operational efficiency.

---

## Deep-Dive Visualization Analysis

### 1. Product Portfolio Matrix: Volume vs. Efficiency (Scatter Plot)
This is a customized **BCG Matrix Framework** embedded within the scatter visualization. By plotting **Total Quantity Sold (Volume)** on the X-axis against **Profit Margin % (Efficiency)** on the Y-axis, the data segments product lines into clear operational quadrants:

* **The Stars ⭐️ (High Volume, High Margin):** `Huawei` stands out prominently at the top-center. It commands a massive **60%+ profit margin** with a stable mid-tier sales volume. This represents a high-value portfolio line that needs aggressive marketing and protection.
* **The Cash Cows 🐄 (High Volume, Moderate Margin):** `Apple` and `LG` sit heavily on the far right of the canvas, moving between **10K to 12K units**. While their margins are moderate (ranging between 30% and 40%), their sheer sales velocity drives the absolute majority of the company's continuous cash flow.
* **The Dogs / Question Marks 🐕 (Low Volume, Low Margin):** `Motorola` and `Samsung` sit in the lower-left quadrant. They suffer from lower consumer volume and weaker structural margins, indicating a need for category adjustments or inventory optimization to stop cost bleed.

### 2. Brand Profitability  (Clustered Bar Chart)
This visualization explicitly exposes an **Inverse Profit Margin Paradox** within the product tiers:
* **The Revenue vs. Profit Delta:** `Apple` is the undisputed leader in generating *Total Revenue*. However, looking closely at `Huawei`, its gross revenue is less than half of Apple's, yet its *Total Profit* yield matches Apple almost dollar-for-dollar.
* **Strategic Insight:** High sales velocity does not automatically equal profitability. Huawei drives incredible net financial density to the company's bottom line using a fraction of the inventory footprint required by flagship competitors.

### 3. Operator & Brand Breakdown (100% Stacked Bar)
This chart acts as an operational **Supply Chain & Distribution Channel Risk Analysis**, mapping how vulnerable brand portfolios are to wholesale telecom carrier networks:
* **Channel Concentration Risks:** Looking at the `Tuenti` carrier bar at the top, `Apple` occupies a massive, disproportionate share of that channel's total volume. Across the board, product flow is heavily concentrated within `Tuenti`, `Entel`, and `Bitel`, while `Movistar` at the bottom remains significantly underutilized.
* **Strategic Insight:** This exposes a high distribution risk. If supply contracts or logistics agreements with Tuenti or Entel face disruptions, a critical portion of the global sales pipeline will instantly freeze. Commercial teams must use this data to diversify carrier allocations.

### 4. Revenue vs. Profit Margin Regional Breakdown (Matrix Heatmap)
This operational matrix leverages conditional formatting via a dynamic color gradient layer to map underlying business performance. While the matrix table is explicitly sorted in descending order by **Total Revenue (Sales)**, the background cell color of the revenue column is conditionally based on **Profit Margin %** (ranging from light blue for low margins to vibrant blue for high margins). This engineering layer immediately exposes critical regional margin leakages:

* **High-Volume Execution Corridors:** `El Salvador` ($256,120) and `Colombia` ($245,092) prove to be highly efficient, anchoring global operations by driving the highest absolute sales while securing the dense majority of the total profit share (**6.46% and 6.16%** respectively).
* **The Revenue vs. Efficiency Disconnect (Margin Leakage):** The conditional formatting gradient exposes major pricing and cost anomalies down the pipeline:
    * **Venezuela vs. France:** `Venezuela` sits much lower on the sales ledger ($138,087) compared to `France` ($138,804). However, its vibrant blue cell color flags an exceptional **3.94% Total Profit Share**, completely outperforming France's weaker **3.47%** return despite France having higher gross sales.
    * **Brasil & Chile vs. High-Volume Clusters:** `Brasil` ($174,999) and `Chile` ($157,433) trigger deep blue heat signatures, yielding a disproportionately high profit share (**4.69% and 4.17%**) compared to higher-ranked regions like Portugal or Denmark. 
* **Strategic Insight:** Sorting purely by top-line metrics masks operational flaws. By using conditional heat-mapping based on efficiency rather than volume, corporate leadership can instantly isolate which geographic territories are suffering from high shipping overheads, aggressive localized discounting, or weak retail price points, allowing them to shift inventory to high-margin corridors.

### 5. Monthly Revenue Trajectory (Time-Series Line Chart)
This analytical trend line maps the continuous commercial velocity of the business across the fiscal year to evaluate continuous market demand:
* **Seasonal Volatility & Post-Season Dip:** The timeline displays an intense peak in **October**, where monthly revenue sky-rockets to its highest point of **$4.5M**. Following this peak, there is a sharp, aggressive drop throughout November, with a low baseline stabilization in December.
* **Strategic Insight:** This identifies a classic retail demand pattern—potentially driven by major holiday pre-ordering, wholesale distribution stocking cycles, or specific hardware release windows in October. The drastic post-peak plunge highlights a critical need for tactical end-of-year clearance campaigns or Q4 pricing adjustments to flatten the seasonal revenue valley.

### 6. Distributor Volume Analysis
* This chart bridges logistics tracking with retail execution, identifying exactly which partners are moving inventory. 
* `Oeschle` and `Plaza Vea` are clearly identified as the anchor distribution channels, carrying the heavy operational load for major volume drivers like Apple and LG.
---

## Tools & Technologies

* **Power BI Desktop** – Data modeling, DAX development, and dashboard design.
* **Power Query** – Data transformation and preparation.
* **DAX** – Business calculations and KPI development.
* **Microsoft Excel** – Source data validation and verification.

---

## Repository Structure

```text
├── data/
│   ├── Business-Intel_Phone-Sales.xlsx - Phone Sales.csv
│   └── Business-Intel_Phone-Sales.xlsx - Date_Phones.csv
│
├── models/
│   └── Global_Phone_Sales_Analytics.pbix
│
├── images/
│   └── Dashboard_Overview.png
│
└── README.md
```

---

## Project Highlights

* Dimensional Data Modeling
* DAX-Based KPI Development
* Interactive Power BI Dashboard Design
* Revenue and Profitability Analysis
* Telecom Distribution Analysis
* Executive Reporting and Commercial Insights
