# Retail Sales Performance Dashboard — Power BI

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-37%20Measures-blue?style=for-the-badge)
![Excel](https://img.shields.io/badge/Dataset-Excel-217346?style=for-the-badge&logo=microsoftexcel&logoColor=white)

> End-to-end retail analytics dashboard built in Power BI for a fictional retail chain operating across Azerbaijan. Features star/snowflake schema data modeling, 37 DAX measures, RFM segmentation, Pareto/ABC analysis, What-if discount simulation, and drillthrough store-level analytics.

---

## 📸 Dashboard Preview

| Executive Overview | Sales Performance |
|---|---|
| ![Executive Overview](01_executive_overview.png) | ![Sales Performance](02_sales_performance.png) |

| Product Analysis | Customer Insights |
|---|---|
| ![Product Analysis](03_product_analysis.png) | ![Customer Insights](04_customer_insights.png) |

| Profitability & Simulation | Store Deep-Dive |
|---|---|
| ![Profitability](05_profitability_simulation.png) | ![Store Deep-Dive](06_store_deep_dive.png) |

---

## 📌 Project Overview

A fictional retail chain operating across Azerbaijan with 12 stores in 5 regions was used as the business scenario. The dashboard was built to simulate a real-world BI solution that enables management to monitor sales performance, customer behavior, and profitability in one place.

| | |
|---|---|
| **Tool** | Power BI Desktop |
| **Dataset** | Synthetic data generated with Python |
| **Time Period** | 2023 – 2025 (3 years) |
| **Transactions** | 31,000+ sales records |
| **Customers** | 2,600 |
| **Products** | 55 across 5 categories |
| **Stores** | 12 stores across 5 regions |

> The dataset was generated with realistic seasonal patterns including Novruz holiday spikes, Black Friday peaks, New Year surges, and year-over-year growth trends. Stores were deliberately assigned different performance tiers (Star / Solid / Underperformer) to enable meaningful storytelling.

---

🗂️ Data Model

Star + Snowflake Schema — 7 tables

Dim_Date ──────────────→ Fact_Sales ←──────── Dim_Product ←─── Dim_Category
                              ↑                                       ↑
Dim_Store ────────────────────┤                                       │
Dim_Customer ─────────────────┘                                       │
                                                                       │
                          Fact_Targets ←── Dim_Store                  │
                               ↑                                       │
                          Dim_Date          Dim_Category ──────────────┘

TableTypeRowsDim_DateDimension1,096Dim_StoreDimension12Dim_ProductDimension55Dim_CategorySnowflake Dimension5Dim_CustomerDimension2,600Fact_SalesFact31,252Fact_TargetsFact (Monthly Plan)2,132


Why a separate Dim_Category? Fact_Targets is at category granularity (not product level), while Dim_Product[Category] is not unique. A dedicated Dim_Category table resolves this as a snowflake element, enabling clean relationships with both fact tables — a deliberate modeling decision to handle different granularity levels.

---
