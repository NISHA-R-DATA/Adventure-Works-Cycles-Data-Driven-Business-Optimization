# 🚴‍♂️ Adventure Works Cycles – Business Intelligence Dashboard

## 📌 Table of Contents
1. [Project Overview](#project-overview)  
2. [Business Problem](#business-problem)  
3. [Data Overview](#data-overview)  
4. [Tools & Technologies Used](#tools--technologies)  
5. [Approach](#approach)  
   - [Data Preprocessing & Transformation](#data-preprocessing--transformation)  
   - [Data Modelling](#data-modelling)  
   - [Visualization & Dashboard Design](#visualization--dashboard-design)  
6. [Key Business Insights](#key-business-insights-2010–2014)  
7. [Recommendations](#recommendations)  
8. [Conclusion](#conclusion)  

---

## 🧭 Project Overview
This Power BI project addresses key operational and strategic challenges faced by Adventure Works Cycles, a global manufacturer of bicycles and related accessories. The objective is to:  
• Optimize inventory management  
• Reduce production costs  
• Identify high-value customers  
• Expand market reach  

Through detailed data analysis and dynamic dashboards, the project uncovers insights into regional sales trends, customer behavior, and product profitability. These insights empower business stakeholders to streamline production planning, target the right customer segments, and improve overall operational efficiency.  

By transforming complex datasets into clear, actionable recommendations, this solution supports smarter decision-making and helps strengthen the company’s position through improved acquisition, retention, and resource allocation strategies.  

*A snapshot of the Power BI dashboard built for Adventure Works Cycles, offering a visual summary of key business metrics.*

![Dashboard_AWC](https://github.com/user-attachments/assets/419824ff-c90e-4741-a38f-bba643fdaaa7)

---

## ❗ Business Problem
Adventure Works Cycles faces the following challenges:  
1. Targeting the Right Customers: Identifying the most profitable customer segments and engaging them with targeted offerings to increase lifetime value.  
2. Expanding Product Availability: Understanding regional and category-wise sales performance to optimize inventory and extend market reach.  
3. Reducing Production Costs: Minimizing inefficiencies in manufacturing, especially for high-cost product lines.  

The company’s strategic goal is to grow its market share by focusing on the right customers, improving inventory flow, and managing costs effectively.

---
## 📂 Data Overview
Historical data from 2010 to 2014 was provided, covering sales transactions, customer profiles, regional information, and product details. The dataset was organized across the following tables:
- **FactInternetSales**, **FactInternetSalesNew** – Internet sales transactions  
- **DimCustomer**, **DimSalesTerritory** – Customer and territory data  
- **DimProduct**, **DimProductSubcategory**, **DimProductCategory** – Product hierarchy

---

## 🧰 Tools & Technologies Used

| Tool / Technique         | Purpose                                                  |
|--------------------------|----------------------------------------------------------|
| Microsoft Excel          | Initial data review and validation                       |
| Power Query Editor       | Data cleaning, transformation, and shaping              |
| DAX (Data Analysis Expressions) | Creation of custom measures, KPIs, and calculated columns |
| Power BI Desktop         | Data modeling, interactive visualizations, and dashboard creation |

---
# 📊 Approach

## 1️⃣ Data Preprocessing & Transformation

• Imported and consolidated raw Excel files within Power BI.  
• Cleaned data using Power Query Editor:  
&nbsp;&nbsp;&nbsp;&nbsp;o Removed irrelevant columns (e.g., Carrier Tracking Number, Customer Phone Number).  
&nbsp;&nbsp;&nbsp;&nbsp;o Standardized data types and formatting.  
• Appended FactInternetSales and FactInternetSalesNew into a unified Sales table for consistency across all years.  
• Created new calculated columns:  
&nbsp;&nbsp;&nbsp;&nbsp;o Sales, ProductionCost, and Gross Profit for financial analysis.  
• Simplified the snowflake schema:  
&nbsp;&nbsp;&nbsp;&nbsp;o Merged DimProduct, DimProductSubcategory, and DimProductCategory into a single product dimension.  
• Created a DimDate table:  
&nbsp;&nbsp;&nbsp;&nbsp;o Generated continuous date range, with derived columns for Year, Quarter, and Financial Month (starting in April).  
• Constructed CustomerFullName column in DimCustomer by combining first, middle, and last names.  
• Customer Segmentation Logic:
A segmentation table was created using customer transaction frequency:

| Category         | Criteria         |
|------------------|------------------|
| Top-Tier         | 10+ orders        |
| Steady Shoppers  | 5–9 orders        |
| Occasional Buyers| Fewer than 5 orders |

This categorization aids in profiling customer engagement and supporting loyalty campaigns.

---

## 2️⃣ Data Modeling

• Developed a Star Schema with the unified Sales table as the fact table.  
• Established many-to-one relationships with all relevant dimension tables.  
• Ensured referential integrity and enabled effective cross-filtering.  

*Visual representation of the star schema designed to structure and streamline data for effective reporting and analysis.*

![Screenshot 2025-05-08 135149](https://github.com/user-attachments/assets/85655752-6298-4ec9-9815-41198a7fa5ec)

---
# 📊 3️⃣ Visualization & Dashboard Design

## 🔍 Key Performance Indicators (KPIs) Tracked:
- Total Orders  
- Total Sales  
- Total Production Cost  
- Gross Profit Margin  
- Net Profit Margin  
- Total Customers  

## 📈 Key Visuals:

### Sales by Product Category
- A hierarchical visual allows drill-down from Product Category to Subcategory.  
- A drill-through page shows detailed product-level data including Gross Profit and Stock Status.  
- Applied conditional formatting with arrows to indicate profit trends.
- Color-coded Stock Status: Red-Oversized, Green-Within Range, Yellow-Undersized. This supports proactive inventory decisions.  

🧮 **Custom Stock Status Classification (DAX):**

```DAX
StockStatus = 
VAR QuantityOrdered = SUM(Sales[OrderQuantity])
VAR SafetyStockLevel = AVERAGE(Sales[SafetyStockLevel])
VAR ReorderPoint = AVERAGE(Sales[ReorderPoint])
RETURN
IF(QuantityOrdered > ReorderPoint, "Oversized",
    IF(QuantityOrdered < SafetyStockLevel, "Undersized", "Within Range"))
```
	
*View of the tailored product table designed for profitability tracking and efficient inventory management.*

![Product Table](https://github.com/user-attachments/assets/5643ceb8-d8d7-4bea-98ad-6ad8bfaca11c)

---

## Sales Trends by Product Color

•	A bar chart highlights best-selling and underperforming colors.  
•	Included a Key Influencer visual to analyze the impact of color on production costs. 

*Snapshot of Key influencer Visual*

![Keyinfluencer](https://github.com/user-attachments/assets/3695d311-f67e-459e-bff7-61f6dd7336b2)

---

## Regional Sales Funnel

A funnel chart with tooltips offers insights into sales performance by Sales Territory and Country.

---

## Customer Insights & Behavioral Analysis

•	Users can interactively explore how factors like Occupation, Commute Distance, and Car Ownership influence purchasing behavior.  
•	Bookmark navigation enables seamless switching between behavioral analysis views. 

*Customer insights and behavioral analysis view*

![customer_insights](https://github.com/user-attachments/assets/50360b54-a9d9-49cb-82c7-d5b3469debeb)

---

## Order Distribution by Customer Tier

•	A Decomposition Tree visual displays order volume by customer category.  
•	Enables deep-dive into Top-Tier buyer profiles and supports targeted retention strategies.

*Views of tailored tables capturing insights on top-tier, steady, and occasional customers.*

![Customer_Table](https://github.com/user-attachments/assets/2d4afd27-fe06-4db3-91ec-214c5b20ec03)

---

## 📌 Key Business Insights 

### 📈 Sales Trends
• Orders increased steadily year-over-year.  
• A notable sales spike in 2013, attributed to diversification into Accessories and Clothing.

### 🚲 Product Profitability
• Bikes, especially Road and Mountain Bikes, led in sales.  
• Accessories and Clothing gained traction from 2012 onward.  
• Top 20 products generated 63% of total sales.  
• Mountain-200 Black (46) was the top-performing product in terms of profit.  
• Red and Silver bikes incurred high production costs.  
• Overstocked high-margin products indicated potential inventory inefficiencies.

### 🌍 Regional Sales
• North America, led by the Southwest U.S., dominated revenue.  
• Australia and UK showed consistent growth.  
• Canada underperformed, suggesting a need for localized strategies.

### 👥 Customer Segmentation
• A small group of Top-Tier Customers (246) accounted for a large revenue share.  
• Occasional Buyers represented an underleveraged growth segment.  
• Multi-car owners showed preference for premium offerings.  
• Female professionals with mid-income levels displayed stable, high-value buying behavior.

---

## ✅ Recommendations

### 1. Sales & Marketing
• Launch exclusive loyalty programs for top-tier customers.  
• Expand focus on premium products (Mountain, Touring bikes) tailored for affluent, multi-car households.  
• Continue investment in Accessories & Clothing as high-growth segments.

### 2. Inventory Optimization
• Reduce overstocking of large-volume, high-margin items.  
• Align production with real-time demand trends and reorder points.

### 3. Cost Control
• Revisit procurement strategies for Red and Silver paint/materials.  
• Explore lean manufacturing techniques to minimize wastage and cut costs.

### 4. Regional Expansion
• Strengthen marketing efforts in Canada and France to boost market penetration.  
• Evaluate localized promotions and bundled offers to engage new customers.

---

## 🏁 Conclusion

This Power BI project effectively transformed fragmented raw data into a unified, insightful, and action-oriented analytical solution. By identifying key product trends, regional opportunities, and customer behavior patterns, it enables Adventure Works Cycles to make smarter, data-driven decisions. The dashboards serve not only as performance tracking tools but also as strategic assets for enhancing customer engagement, managing costs, and driving market expansion.

Armed with these insights, Adventure Works Cycles is well-positioned to strengthen its competitive edge, streamline operations, and unlock untapped customer value across global markets.

