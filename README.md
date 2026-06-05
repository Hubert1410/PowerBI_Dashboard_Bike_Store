# PowerBI - End-to-End Dashboard for Global Sales Strategy

![Dashboard](/Images/Dashboard.gif)

## Introduction
**AdventureWorks** is a global manufacturing company that produces and sells bicycles, bike parts, and cycling accessories. As a Data Analyst, before diving into development, I defined the core project goals and answered key strategic questions to ensure the dashboard delivers maximum business value.

### Project Goals:
* **Track KPIs:** Monitor high-level metrics to define whether the organization is meeting its predefined goals.
* **Compare Regional Performance:** Identify growth opportunities and underperforming territories.
* **Analyze Product-Level Trends:** Drill down into specific categories and subcategories to see what drives revenue.
* **Identify High-Value Customers:** Understand customer demographics and purchasing behavior.

---

## 🧭 Dashboard Planning & Preparations

To build an effective reporting tool, I addressed **three fundamental data storytelling questions**:

### Q1: What type of data will be used? 
> *The data type dictates the choice of visualizations to ensure clarity and avoid clutter.*
* **Time Series:** Profit, revenue, and orders tracked over time (best for line/area charts).
* **Categorical:** Product categories, subcategories, and customer segments (best for bar/column charts).
* **Geospatial:** Regional data from the Territory Lookup table (best for map visualizations).
* **Hierarchical:** Structural data like Product Category $\rightarrow$ Subcategory $\rightarrow$ Product Name (best for matrix visuals and drill-downs).

### Q2: What story should the report tell?
* **Comparisons over time & categories:** Monthly Revenue, Total Customers, Orders by Country, and Orders by Category.
* **Composition (Breakdown):** Splitting wholes into parts, such as Orders by Customer Occupation and Orders by Customer Income Level.

### Q3: Who is the target audience and what do they need?
* **Audience:** Executive Managers.
* **Needs:** High-level summaries, quick insights to support data-driven decision-making, and intuitive, widely recognized visuals (avoiding overly complex charts).

---

## 🗂️ Dashboard Structure
Based on the planning phase, the report was structured into **4 dedicated pages** to separate high-level overviews from deep-dive analyses:
1.  **Main Executive Dashboard:** High-level overview of KPIs, revenue, and order trends.
2.  **Map View:** Geospatial analysis of performance across global territories.
3.  **Product Detail:** Deep dive into specific product performance, pricing, and returns.
4.  **Customer Detail:** Demographics, behavior, and top customer tracking.

![DashboardPages](/Images/Dashboard_Pages.png)

---

## ❄️ Data Model

![DataModel](/Images/Data_Model.gif)

The project utilizes a **Snowflake Schema** data model designed for structured data organization and efficient analytical querying.

### What is a Snowflake Schema?
A Snowflake Schema is an extension of a Star Schema where **dimension tables are normalized**, meaning they split into further sub-tables. In this project, instead of a single flattened product table, the model branches out structurally: 
`Product Category` ➔ `Product Subcategory` ➔ `Product Lookup` ➔ `Sales/Returns (Fact Tables)`.

### Model Components:
* **2 Fact Tables:** `Sales Data` and `Returns Data` — containing granular transactional records (dates, quantities, prices).
* **6 Dimension Tables:** Providing context across the model (`Calendar Lookup`, `Customer Lookup`, `Territory Lookup`, and the normalized Product tables).
* **The Downstream Principle:** Filters always flow "downstream" — from the 1-side (Dimension tables) to the many-side (Fact tables). For example, filtering by a *Product Category* automatically propagates down to filter the *Subcategories*, which filters the *Products*, and ultimately filters the rows in the *Sales* table.
