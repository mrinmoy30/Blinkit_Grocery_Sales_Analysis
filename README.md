# 🛒 Blinkit Grocery Sales Analysis

This project aims to conduct a comprehensive analysis of Blinkit's sales performance, customer satisfaction, and inventory distribution. The primary goal is to identify key insights and optimization opportunities by utilizing various Key Performance Indicators (KPIs) and visualizations within Power BI.

---

### [▶️ View the Interactive Report (Link)](https://app.powerbi.com/view?r=eyJrIjoiMTYwZTI5NzktZTQ5ZC00ZmJiLWIyZmItNjM0ODAyM2M3ZGFiIiwidCI6ImEzMjAwOGMwLWRhZjgtNDc5Zi1hOTk1LTI4MTVlYThmMTVjZiJ9)

## Dashboard Preview 🖥️

![Dashboard Preview](https://github.com/mrinmoy30/Blinkit_Grocery_Sales_Analysis/blob/main/Blinkit%20Dashboard.jpg)

---

## 1. Business Requirements 🎯

The primary goal of this dashboard is to answer key business questions and provide actionable insights. The core objectives addressed are:

### KPI Requirements:

- **Total Sales:** The overall revenue generated from all items sold.
- **Average Sales:** The average revenue per sale.
- **Number of Items:** The total count of different items sold.
- **Average Rating:** The average customer rating for items sold.

### Analysis Requirements (Visualizations):

- Analyze the impact of fat content on total sales and other KPIs.
- Identify the sales performance of different item types.
- Compare total sales across different outlets, segmented by fat content.
- Evaluate how outlet establishment age/type influences total sales.
- Analyze the correlation between outlet size and total sales
- Assess the geographic distribution of sales across outlet locations.
- Provide a comprehensive view of all key metrics (Total Sales, Average Sales, Number of Items, Average Rating) broken down by outlet type.

## 2. Data Processing & Transformation (ETL) 🛠️

All data transformations were performed using Excel and PowerBI.

**Data Cleaning and Preparation:**

- **Standardization:** The "Item Fat Content" column was standardized. "LF" was replaced with "Low Fat" (316 replacements) and "reg" was replaced with "Regular" (3006 replacements).
- **Missing Values:** Missing values were identified in the "Item weight" column. These were ignored as the column was not critical for the required analysis.

## 3. Data Modeling 🔗

The project was migrated from Excel Pivot Tables to Power BI for more robust analysis and visualization.

**KPI Measures (DAX):** Four key measures were created using DAX to support the KPI requirements:

- `Total Sales = SUM('Grocery Data'[Sales])`
- `Average Sales = AVERAGE('Grocery Data'[Sales])`
- `Number of items = COUNTROWS('Grocery Data')`
- `Average Rating = AVERAGE('Grocery Data'[Rating])`

Field Parameter: A Field Parameter named "metrics" was created under "Modelling -> New Parameter -> Field". This parameter incorporated the four KPI measures, allowing users to dynamically switch between them in the visualizations.

## 4. Visualizations ✨

The following visualizations were created (on a 16:9 canvas) to address the business requirements:

| Business Question                   | Visualization Used   | Key Fields & Configuration                                                                 |
| :---------------------------------- | :------------------- | :----------------------------------------------------------------------------------------- |
| **Sales by Fat Content**            | Donut Chart          | **Legend:** `Item Fat Content`, **Values:** `Metrics (Field Parameter)`                    |
| **Sales by Item Type**              | Bar Chart            | **Y-axis:** `Item Type`, **X-axis:** `Total Sales`                                         |
| **Fat Content by Outlet for Sales** | Stacked Column Chart | **X-axis:** `Outlet Identifier`, **Y-axis:** `Total Sales`, **Legend:** `Item Fat Content` |
| **Sales by Outlet Establishment**   | Line Chart           | **X-axis:** `Outlet Establishment Year`, **Y-axis:** `Total Sales`                         |
| **Sales by Outlet Size**            | Donut Chart          | **Legend:** `Outlet Size`, **Values:** `Total Sales`                                       |
| **Sales by Outlet Location**        | Funnel Map           | **Location:** `Outlet Location Type`, **Values:** `Total Sales`                            |
| **All Metrics by Outlet Type**      | Matrix Card          | **Rows:** `Outlet Type`, **Values:** `Metrics (Field Parameter)`                           |

## 5. How to Use This Dashboard 🖱️

- **Open the `.pbix` file** in Power BI Desktop.
- **Interact with Visuals:** Click on any element in a chart (e.g., a bar in the "Sales by Item Type" chart) to cross-filter all other visuals on the page for that selection.
- **Use Slicers and Filters:** Use slicers (if added) and the filter pane to drill down into the data by specific criteria.
- **Dynamic KPIs:** Use the "metrics" field parameter slicer to change the measure displayed in the "Sales by Fat Content" and "All Metrics by Outlet Type" visuals.

## 6. Data-Driven Insights 💡

**Overall KPI Summary:**

- The dataset covers **8,523 items**, generating **₹1,201,681.49** in total sales. The average sale per item is **₹140.99**, and the overall average customer rating for all items is **3.97 out of 5**.

**Detailed Pivot Table Analysis:**

**A. Product Insights:**

**a. Sales by Fat Content:** **"Low Fat"** products are the primary sales driver.

- **Low Fat:** **₹776,319.69** in sales (**64.6%** of total) across **5,517 items**.
- **Regular:** **₹425,361.80** in sales (**35.4%** of total) across **3,006 items**.
- The average sales price and average rating are nearly identical for both categories, indicating that the sales dominance is driven by a higher volume and variety of low-fat items, not a higher price or rating.

**b. Sales by Item Type (Category):** **"Fruits and Vegetables"** and **"Snack Foods"** are the clear top-performing categories.

**b1. Top 3 Categories (by Total Sales):**

- **Fruits and Vegetables: ₹178,124.08**
- **Snack Foods: ₹175,433.92**
- **Household: ₹135,976.53**

**b2. Bottom 3 Categories (by Total Sales):**

- **Starchy Foods: ₹21,880.03**
- **Breakfast: ₹15,596.70**
- **Seafood: ₹9,077.87**

**c. Category Price & Rating:**

- **"Household"** items have the highest average sales price (**₹149.42**), suggesting they are higher-ticket items.

- **"Meat"** has the highest average customer rating (**4.02**), though most categories are tightly clustered around the **3.9-4.0** average.

**B. Outlet & Store Insights:**

**a. Sales by Outlet Type:** This is the most significant finding. **"Supermarket Type1"** is the dominant outlet type, accounting for the vast majority of all revenue.

- **Supermarket Type1: ₹787,549.89 (65.5% of all sales)**
- **Grocery Store: ₹151,939.15**
- **Supermarket Type2: ₹131,477.78**
- **Supermarket Type3: ₹130,714.67**

**"Supermarket Type1**" generates more than 5 times the sales of the next closest outlet type.

**b. Sales by Outlet Location:** **"Tier 3"** locations generate the most sales, though all tiers are significant contributors.

- **Tier 3: ₹472,133.03 (39.3% of sales)**
- **Tier 2: ₹393,150.65 (32.7% of sales)**
- **Tier 1: ₹336,397.81 (28.0% of sales)**

**c. Sales by Outlet Size:** **"Medium"** and **"Small"** outlets drive the business, while **"High"** size outlets significantly underperform.

- **Medium: ₹507,895.74**
- **Small: ₹444,794.17**
- **High: ₹248,991.59 (generates roughly half the sales of Medium outlets)**

**d. Sales by Outlet Establishment Year:** There is significant variation by the year the outlet was established.

- The outlet established in **2018** is the top performer by a large margin, with **₹204,522.26** in sales.
- Most other outlets (established **2012-2017, 2020, 2022**) are clustered in the **₹130k-₹133k** range.
- The outlet established in **2011** is the lowest performer, with only **₹78,131.57** in sales.
