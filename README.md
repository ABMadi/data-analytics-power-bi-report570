# Power BI Quarterly Sales Report for an International Retailer

📊 **Transforming Retail Data into Actionable Insights**  
This project aims to develop a Quarterly Sales Report for a medium-sized international retailer, enhancing their business intelligence capabilities. With operations across multiple regions, they have accumulated sales data from various sources over the years. The goal of this project is to transform that data into actionable insights for better decision-making using Microsoft Power BI.

---

## 🎯 Project Objective

The objective is to design a multi-page Power BI report that:

- Provides a high-level executive summary.
- Highlights top customers segmented by sales region.
- Analyzes top-performing products by category and performance against targets.
- Displays store performance across regions using a geographical map visualization.

---

## 📢 Milestone Achievements

### ✅ Previous Milestones
Focused on the **Customer Detail page**, including creation of visuals, measures, and slicers for analyzing customer data.

### 🆕 New Milestone: KPI Visuals for Executive Summary

This milestone focused on creating robust KPI visuals for **Quarterly Revenue, Profit, and Orders**. It involved implementing dynamic, context-aware DAX logic and resolving issues related to data misalignment, resulting in fully functional, data-driven KPI reporting.

---

## 📊 Executive Summary Page Overview

This page delivers high-level business metrics through three custom KPI visuals, highlighting how actual performance compares to quarterly growth targets.

---

### 🔖 Visuals Created

1️⃣ **KPI Cards (Custom Build)**
Each metric is represented by:
- A **Card Visual** for current quarter value
- A **Line Chart** comparing actuals to targets over time
- Metrics:
  - **Total Revenue vs Target Revenue**
  - **Total Profit vs Target Profit**
  - **Total Orders vs Target Orders**

📸 Insert Screenshot of KPI Cards and Line Charts here

2️⃣ **Target Logic**
Quarterly targets were set at **5% growth** over the previous quarter, using measures that respect the actual data range of the `Sales[Order Date]` column. This resolved issues with KPI visuals failing to evaluate targets.

---

## 🧮 Key DAX Measures Created for This Page

| Measure Name               | Description                                                                 |
|---------------------------|-----------------------------------------------------------------------------|
| Previous Quarter Revenue  | Revenue in the quarter prior to the current one                            |
| Previous Quarter Profit   | Profit in the previous quarter                                              |
| Previous Quarter Orders   | Number of orders in the previous quarter                                    |
| Target Revenue            | 5% growth over previous quarter revenue                                     |
| Target Profit             | 5% growth over previous quarter profit                                      |
| Target Orders             | 5% growth over previous quarter orders                                      |

---

## 🗂️ Star Schema Data Model

The Executive Summary page leverages the existing star schema from previous milestones:

| Dimension Table           | Fact Table (Sales)   | Type         | Active |
|---------------------------|----------------------|--------------|--------|
| Products[product_code]    | Sales[product_code]  | One-to-Many  | ✅      |
| Data_Analytics[store code]| Sales[Store Code]    | One-to-Many  | ✅      |
| Customers[User UUID]      | Sales[User ID]       | One-to-Many  | ✅      |
| DateTable[date]           | Sales[Order Date]    | One-to-Many  | ✅      |
| DateTable[date]           | Sales[Shipping Date] | One-to-Many  | ❌      |

---
