# Power BI Quarterly Sales Report for an International Retailer

## 📊 Transforming Retail Data into Actionable Insights
A medium-sized international retailer has approached us to enhance their business intelligence capabilities. With operations spanning multiple regions, they have amassed a significant volume of sales data from various disparate sources over the years. Recognizing the value of data-driven decision-making, they have decided to implement Microsoft Power BI to generate a Quarterly Sales Report.

---

## 🎯 Project Objective
The primary objective of this project is to design a comprehensive Power BI report that provides high-level insights for C-suite executives, along with detailed analytics on customer value, product performance, and store efficiency. To achieve this, we have:

- Extracted and transformed data from multiple sources.
- Designed a robust data model using a star-based schema.
- Developed a multi-page Power BI report with interactive visualizations.

### The report delivers:
- 📈 A high-level business summary for executives.
- 🏆 Insights into highest-value customers, segmented by sales region.
- 🔍 Analysis of top-performing products, categorized by type vs. sales targets.
- 🗺️ A geographical map visualization, showcasing the performance metrics of retail stores across various territories.

---

## 📢 Milestone Achievements
In this milestone, we focused on data extraction, transformation, and model optimization.

### 1️⃣ Sales Table (Fact Table)
The Sales table contains transactional order data and serves as the primary fact table in the model.

- **Data Source:** Connected to an Azure SQL Database and imported the Sales table using Import mode.
- **Data Cleaning & Transformations:**
    - Deleted the `[Card Number]` column for data privacy.
    - Split `[Order Date]` and `[Shipping Date]` into separate Date & Time columns.
    - Removed rows with missing Order Dates to ensure data integrity.
    - Renamed columns to follow Power BI naming conventions.

### 2️⃣ Products Table (Dimension Table)
The Products table provides details about the products, including category, pricing, and weight.

- **Data Source:** Imported from Products.csv using Get Data in Power BI.
- **Data Cleaning & Transformations:**
    - Removed duplicate records based on `[Product Code]` to maintain data uniqueness.
    - Renamed columns for clarity and consistency.

### 3️⃣ Stores Table (Dimension Table)
The Stores information is contained within the `data_analytics` table.

- **Data Source:** Connected to Azure Blob Storage.
- **Key Transformations:**
    - Standardized the `[Region]` column for consistent spelling.
    - Created a **Country** column based on **Country Code** (GB, US, DE → Full Country Name).
    - Created a **Geography** column combining **Region and Country** (e.g., "California, United States").
    - Renamed columns to follow Power BI best practices.

### 4️⃣ Customers Table (Dimension Table)
The Customers table contains customer records from different regions.

- **Data Source:** Downloaded and extracted `Customers.zip`, which contained multiple CSV files.
- **Data Import Method:**
    - Used the **Folder data connector** in Power BI.
    - Applied the **Combine & Transform** option to merge all CSV files into a single dataset.
- **Data Cleaning & Transformations:**
    - Created a `[Full Name]` column by combining `[First Name]` and `[Last Name]`.
    - Removed unnecessary index columns.
    - Renamed columns for clarity and consistency.

---

## 🛠️ Power BI Data Model & Schema
The data model is structured using a **star schema**, with the **Sales** table as the central fact table and dimension tables for **Products**, **Stores**, and **Customers**. This schema optimizes query performance and ensures efficient data relationships.

### 🔗 Relationships
| Dimension Table | Fact Table (Sales) | Type | Active |
|-----------------|--------------------|-----|-------|
| Products[product_code] | Sales[product_code] | One-to-Many | ✅ |
| Data_Analytics[store code] | Sales[Store Code] | One-to-Many | ✅ |
| Customers[User UUID] | Sales[User ID] | One-to-Many | ✅ |
| DateTable[date] | Sales[Order Date] | One-to-Many | ✅ (Active) |
| DateTable[date] | Sales[Shipping Date] | One-to-Many | ❌ (Inactive) |

---

## 📊 Key DAX Measures
| Measure Name | Description |
|--------------|-------------|
| Total Orders | Counts total orders (`COUNTROWS(Sales)`) |
| Total Revenue | Calculates revenue by multiplying quantity and sale price |
| Total Profit | Computes total profit per product |
| Total Customers | Counts unique customers dynamically |
| Total Quantity | Sums total quantity of items sold |
| Profit YTD | Calculates **Year-to-Date (YTD) profit** |
| Revenue YTD | Calculates **Year-to-Date (YTD) revenue** |

---

## 📂 Hierarchies for Drill-Down Analysis
Hierarchies allow for granular analysis and drill-downs in reports.

### 📅 Date Hierarchy
| Level | Column |
|------|-------|
| Start of Year | StartOfYear |
| Start of Quarter | StartOfQuarter |
| Start of Month | StartOfMonth |
| Start of Week | StartOfWeek |
| Date | Date |

### 🌍 Geography Hierarchy
| Level | Column |
|------|-------|
| World Region | Region |
| Country | Country |
| Country Region | Country Region |

---

## 📊 Customer Detail Page Features
The **Customer Detail page** contains:

### Headline Cards
- **Unique Customers**: Total unique customers filtered dynamically.
- **Revenue per Customer**: Average revenue per customer.

### Donut Charts
- **Customers by Country**: Displays the distribution of customers across different countries.
- **Customers by Product Category**: Shows how many customers purchased from each product category.

### Line Chart
- Displays **Total Customers over time**.
- Supports drill-down to **Year, Quarter, and Month levels**.
- Includes:
    - **Trend line** showing overall customer growth.
    - **Forecast** for the next 10 periods with a 95% confidence interval.

### Top 20 Customers Table
- Displays the **Top 20 customers** by total revenue.
- Includes:
    - **Customer Full Name**
    - **Total Revenue per Customer**
    - **Total Orders per Customer**
- Includes **data bars** for easy comparison of customer revenue.

### Top Customer Insights Cards
- A set of 3 **card visuals** displaying insights for the **top customer by revenue**:
    - **Top Customer Name**
    - **Top Customer Total Revenue**
    - **Top Customer Number of Orders**

### Date Slicer
- Allows users to **filter the page by year** using a **Between-style slicer**, providing flexibility for viewing data within a specific time range.


