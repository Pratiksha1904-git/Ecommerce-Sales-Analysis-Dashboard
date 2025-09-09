# 🛒 E-Commerce Sales Analysis Dashboard  

## 📌 Project Overview  
This project analyzes E-commerce sales data to provide insights into **YTD performance, sales trends, product performance, and customer behavior**.  
The dashboard helps business leaders monitor **sales, profit, quantity, profit margins, top/bottom products, and regional trends** for better decision-making.  

---

## 🎯 Business Problem  
The company faced challenges in tracking **real-time sales across categories, regions, and products**.  
Leadership needed an **interactive dashboard** to identify:  
- Top & bottom performing products  
- Regional strengths & weaknesses  
- Sales growth over time  
- Impact of shipping methods on profitability  

---

## 🏆 Project Goals  
- Build KPI cards for **YTD Sales, Profit, Quantity, and Profit Margin** with YoY Growth  
- Identify **Top 5 and Bottom 5 Products** by sales  
- Analyze **Sales by Category and Sub-category**  
- Map **Regional Sales by State** using geographic data  
- Track **Sales by Shipping Mode** for operational optimization  

---

## 🛠️ Tech Stack  
- **MySQL** → Data source connection for importing transactional sales data  
- **Power BI** → Data modeling, DAX measures, interactive dashboards  
- **Excel** → Minor pre-cleaning and validation  

---

## 📂 Data Sources  
- `ecommerce_data.csv` → Transaction-level dataset (orders, sales, profit, categories, shipping, state)  
- `us_state_long_lat_codes.csv` → Reference table with US states and coordinates for mapping  
- **Calendar Table** → Created in Power BI using DAX  

---

## 🗂️ Data Model (Star Schema)  

**Fact Table:**  
- `ecommerce_data` (orders, sales, profit, quantity, category, state, shipping type)  

**Dimension Tables:**  
- `Calendar` (custom date table for time intelligence)  
- `us_state_long_lat_codes` (geographic info for mapping)  

**Relationships:**  
- `Calendar[Date]` (1) ──▶ (*) `ecommerce_data[Order_Date]`  
- `us_state_long_lat_codes[State]` (1) ──▶ (*) `ecommerce_data[State]`  

![Data Model](modeling/data_model.png)  

---

## 🧮 Calendar Table (DAX)  
```DAX
Calendar =
ADDCOLUMNS (
    CALENDAR ( DATE(2019,1,1), DATE(2023,12,31) ),
    "Year", YEAR([Date]),
    "Month", FORMAT([Date], "MMMM"),
    "Month Number", MONTH([Date])
)

