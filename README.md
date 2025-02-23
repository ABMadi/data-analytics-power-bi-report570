# **Power BI Quarterly Sales Report for an International Retailer**
### **📊 Transforming Retail Data into Actionable Insights**
A **medium-sized international retailer** has approached us to enhance their **business intelligence** capabilities. With **operations spanning multiple regions**, they have amassed a significant volume of sales data from **various disparate sources** over the years. Recognizing the **value of data-driven decision-making**, they have decided to implement **Microsoft Power BI** to generate a **Quarterly Sales Report**.

## **🎯 Project Objective**
The primary objective of this project is to design a **comprehensive Power BI report** that provides **high-level insights for C-suite executives**, along with detailed analytics on **customer value, product performance, and store efficiency**. To achieve this, we have:
- Extracted and transformed **data from multiple sources**.
- Designed a **robust data model** using a **star-based schema**.
- Developed a **multi-page Power BI report** with interactive visualizations.

The report delivers:
- 📈 **A high-level business summary** for executives.
- 🏆 **Insights into highest-value customers**, segmented by **sales region**.
- 🔍 **Analysis of top-performing products**, categorized by **type vs. sales targets**.
- 🗺️ **A geographical map visualization**, showcasing the **performance metrics of retail stores** across various territories.

---

## **📢 Milestone Achievements**
In this milestone, we focused on data extraction, transformation, and model optimization.

### **1️⃣ Orders Table (Fact Table)**
The **Orders** table contains transactional order data and serves as the primary **fact table** in the model.
- **Data Source**: Connected to an **Azure SQL Database** and imported the `orders_powerbi` table using **Import mode**.
- **Data Cleaning & Transformations**:
  - Deleted the `[Card Number]` column for **data privacy**.
  - Split `[Order Date]` and `[Shipping Date]` into **separate Date & Time** columns.
  - Removed **rows with missing Order Dates** to ensure data integrity.
  - Renamed columns to follow **Power BI naming conventions**.

---

### **2️⃣ Products Table (Dimension Table)**
The **Products** table provides details about the products, including category, pricing, and weight.
- **Data Source**: Imported from **Products.csv** using **Get Data** in Power BI.
- **Data Cleaning & Transformations**:
  - Removed **duplicate records** based on `[Product Code]` to maintain **data uniqueness**.
  - Renamed columns for **clarity and consistency**.

---

### **3️⃣ Stores Table (Dimension Table)**
The **Stores** table contains retail store information, including location and store type.
- **Data Source**: Connected to **Azure Blob Storage** and imported the `Stores` table.
- **Data Cleaning & Transformations**:
  - Standardized the `[Region]` column to maintain **consistent spelling**.
  - Renamed columns to follow **Power BI best practices**.

---

### **4️⃣ Customers Table (Dimension Table)**
The **Customers** table contains customer records from different regions.
- **Data Source**: Downloaded and extracted `Customers.zip`, which contained multiple CSV files.
- **Data Import Method**:
  - Used the **Folder** data connector in Power BI.
  - Applied the **Combine & Transform** option to **merge all CSV files** into a **single dataset**.
- **Data Cleaning & Transformations**:
  - Created a `[Full Name]` column by **combining `[First Name]` and `[Last Name]`**.
  - Removed **unnecessary index columns**.
  - Renamed columns for **clarity and consistency**.

---

## **🛠️ Power BI Data Model & Schema**
The data model is structured using a **star schema**, with the **Orders table** as the central fact table and **dimension tables** for products, stores, and customers. This schema optimizes **query performance** and ensures efficient data relationships.

### **🔗 Relationships**
- `Orders[Product ID]` → `Products[Product ID]`
- `Orders[Customer ID]` → `Customers[Customer ID]`
- `Orders[Store ID]` → `Stores[Store ID]`

