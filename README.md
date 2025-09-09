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

<img width="1318" height="670" alt="Ecommerce_DataModeling" src="https://github.com/user-attachments/assets/15c9c91c-8a24-4902-bd4e-cc533f4bdbb2" />

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

## ✨ Key Features  

- 📊 **KPI Cards** → YTD Sales, YTD Profit, YTD Quantity, Profit Margin %  
- 📈 **YoY Growth Indicators** → Show positive/negative sales & profit growth  
- 🏆 **Top & Bottom Products** → Top 5 and Bottom 5 items by sales revenue  
- 🛍️ **Sales by Category/Sub-category** → Breakdown of Furniture, Office Supplies, Technology  
- 🌍 **Regional Sales Map** → Sales contribution by State & Region (West, East, Central, South)  
- 🚚 **Shipping Mode Analysis** → Standard, Second Class, First Class, Same Day  

---

## 📸 Dashboard Screenshot  

### E-commerce Dashboard  
<img width="1195" height="671" alt="Ecommerce_Dashoard_screenshot" src="https://github.com/user-attachments/assets/547aa68b-c779-493a-a0b8-0e96a995e634" />

---

## 📌 Business Impact  

- Helped identify **underperforming products and categories** for corrective action  
- Highlighted **regional opportunities** to target marketing campaigns  
- Improved decision-making on **shipping methods** to increase profitability  
- Delivered a **single source of truth** for executives to track sales performance  

---

## 🚀 Skills Used  

- **MySQL** – Data connection & source integration  
- **Power BI** – Data modeling, DAX measures, dashboard design  
- **Excel** – Minor cleaning & validation  
- **Data Storytelling** – Translating data into actionable business insights


