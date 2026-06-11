# 📱 Global Phone Sales & Portfolio Analytics

[![Power BI](https://img.shields.io/badge/Business_Intelligence-Power_BI-yellow?style=flat\&logo=powerbi)](https://powerbi.microsoft.com/)
[![Data Modeling](https://img.shields.io/badge/Data_Modeling-Dimensional_Model-blue?style=flat)](#)
[![DAX](https://img.shields.io/badge/Analytics-DAX-orange?style=flat)](#)

## 📋 Executive Overview

Global Phone Sales & Portfolio Analytics is a Power BI business intelligence solution developed to evaluate smartphone portfolio performance, regional sales trends, and mobile operator distribution effectiveness across international markets.

The project combines dimensional data modeling, DAX-based analytical calculations, and interactive visual reporting to provide insights into revenue generation, profitability, market performance, and channel distribution patterns.

The dashboard simulates a commercial reporting environment where business stakeholders can monitor product performance, evaluate profitability, and identify opportunities for operational improvement across brands, countries, and telecom operators.

---

## 📸 Dashboard Preview

<img width="1272" height="722" alt="image" src="https://github.com/user-attachments/assets/22e0c5be-a122-4370-9376-698072d8369e" />


---

## 🎯 Business Problem

Revenue alone does not provide a complete picture of business performance. Organizations often require additional visibility into profitability, channel effectiveness, and regional performance to support strategic decision-making.

Key business challenges addressed by this project include:

* Identifying products that generate strong revenue but lower profitability.
* Evaluating dependence on specific telecom operators and distribution channels.
* Detecting regional variations in profit margins and sales performance.
* Providing consolidated portfolio-level insights for commercial decision-making.

---

## 🚀 Objectives

* Analyze smartphone portfolio performance across multiple brands.
* Compare revenue generation and profitability across products and markets.
* Assess distribution patterns across telecom operators.
* Monitor country-level sales performance and margin efficiency.
* Deliver a centralized reporting solution for business stakeholders.

---

## 📊 Dataset Overview

The solution is built using two primary datasets:

| Dataset Component | Type            | Records | Primary Columns                                                                       |
| ----------------- | --------------- | ------- | ------------------------------------------------------------------------------------- |
| Phone Sales       | Fact Table      | 2,998   | Date, Country, Distributor, Brand, Operator, Unit Cost, Amount, Unit Price, Sales     |
| Date_Phones       | Dimension Table | 1,825   | Date, Year, Quarter, Month, Month Name, Month & Year, Week Day, Day Name, Week Number |

---

## 🛠️ Data Architecture

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

## 🧮 Analytical DAX Engine

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

## 🎨 Dashboard Design

The dashboard is organized into three analytical layers designed to guide users from high-level performance indicators to detailed operational insights.

### 1. Executive Summary

KPI cards provide an overview of:

* Total Revenue
* Units Sold
* Total Profit
* Profit Margin %

### 2. Performance Monitoring

Trend-based visualizations enable users to:

* Track sales performance over time.
* Compare regional activity.
* Identify seasonal patterns and fluctuations.

### 3. Portfolio Diagnostics

#### Revenue vs Profit Analysis (Clustered Bar Chart)

A horizontal clustered bar chart compares smartphone brands against their Total Revenue and Total Profit contribution. This visualization highlights the relationship between sales performance and profitability, enabling users to identify brands that generate strong revenue but comparatively lower profit, as well as brands that deliver stronger financial returns relative to their sales volume.

#### Operator Distribution Matrix (100% Stacked Bar Chart)

A 100% stacked bar chart visualizes handset sales volume across major telecom operators, including Movistar, Entel, Claro, Tuenti, and Bitel. By standardizing distribution to a percentage basis, the chart highlights channel allocation patterns and helps identify operator concentration risks within individual brand portfolios.

---

## 📈 Key Insights Generated

### 1. Revenue vs Profitability Analysis

The analysis demonstrated that sales volume alone was not always an accurate indicator of business performance. While several leading smartphone manufacturers generated the highest levels of revenue, certain mid-tier brands, particularly Nokia, achieved significantly stronger profit margins.

With gross margins exceeding 43.8%, these products contributed disproportionately to overall profitability relative to their sales volume, highlighting the importance of evaluating both revenue and margin performance.

### 2. Distribution Channel Dependency Risk

Operator-level analysis revealed instances where specific device portfolios relied heavily on a limited number of telecom distribution partners. Concentration within networks such as Movistar and Entel may increase channel dependency and operational risk.

These findings provide visibility into distribution patterns and support more balanced allocation strategies across operator networks.

### 3. Regional Margin Variations

Country-level analysis identified notable differences in profitability across markets despite similar pricing structures.

Understanding these regional margin variations can support localized pricing decisions, targeted promotional strategies, and more effective inventory allocation across geographic markets.

---

## 🛠️ Tools & Technologies

* **Power BI Desktop** – Data modeling, DAX development, and dashboard design.
* **Power Query** – Data transformation and preparation.
* **DAX** – Business calculations and KPI development.
* **Microsoft Excel** – Source data validation and verification.

---

## 📂 Repository Structure

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

## 📌 Project Highlights

* Dimensional Data Modeling
* DAX-Based KPI Development
* Interactive Power BI Dashboard Design
* Revenue and Profitability Analysis
* Telecom Distribution Analysis
* Executive Reporting and Commercial Insights
