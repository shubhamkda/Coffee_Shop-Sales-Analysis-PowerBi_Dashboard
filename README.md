# Coffee Shop Sales Analysis Dashboard | Power BI
## Project Overview

The **Coffee Shop Sales Analysis Dashboard** is an interactive Power BI solution developed to analyze and monitor sales performance across a coffee shop business.

The dashboard brings together important business metrics such as **revenue, order volume, and quantity sold**, while allowing users to drill down into performance by product category, product type, store location, and time period.

The primary objective of this project is to convert raw transaction data into meaningful business insights that can help stakeholders:

* Monitor overall sales performance  
* Identify high-performing products and categories  
* Compare sales across store locations  
* Understand daily and weekly sales patterns  
* Analyze customer purchasing trends by time  
* Track month-over-month performance  
* Support data-driven operational decisions  

## **📊 Dataset**
The dashboard is built using transaction-level coffee shop sales data.  

The dataset contains the following fields:

Field        | Description
------------- | -------------
**transaction_id**  | Unique reference number assigned to each transaction
**transaction_date** | Date on which the transaction was completed
**transaction_time**  | Time at which the transaction occurred
**transaction_qty**  | Number of products purchased in a transaction
**store_id**  | Unique identifier of the store
**store_location**  | Location of the respective store
**product_id**  | Unique identifier assigned to each product
**unit_price**  | Selling price of one unit
**product_category**  | Broad category of the product
**product_type**  | Specific product type under a category
**product_detail**  | Detailed description/name of the product


## 🧮 DAX Measures
Several DAX measures were created to calculate the dashboard's core performance indicators and time-based comparisons.
### Key Performance Metrics
**Total Sales**
Calculates the total sales revenue for the selected filter context.  
```text
Total Sales = SUM(Transactions[Sales])
```
**Total Orders**
Counts the number of unique transactions.  
```text
Total Orders = DISTINCTCOUNT(Transactions[transaction_id])
```
**Total Quantity Sold**
Calculates the total number of products sold.  
```text
Total Quantity Sold = SUM(Transactions[Transaction_Qty])
```
**Average Sales**
Calculates the average daily sales value based on the selected date context.  
```text
Average Sales = AVERAGEX(ALLSELECTED(Transactions[transaction_date]), 'Date Table'[Total Sales])
```

### Month-over-Month Analysis
**Previous Month Sales**
Retrieves the sales value from the preceding month.  
```text
Previous Month Sales = CALCULATE('Transactions'[CM],DATEADD('Date Table'[Date], -1, MONTH))
```
**Previous Month Orders**
Returns the order count for the previous month.  
```text
CALCULATE('Transactions'[CM Orders],DATEADD('Date Table'[Date], -1, MONTH))
```
**Previous Month Quantity**
Calculates the quantity sold during the previous month.  
```text
Previous Month Quantity = CALCULATE('Transactions'[CM Qty],DATEADD('Date Table'[Date], -1,MONTH))
```

### Current Month Sales
The following calculation dynamically identifies the selected month and calculates the month-to-date sales.
```text
Current Month Sales = VAR selected_month = SELECTEDVALUE('Date Table'[Month]) RETURN TOTALMTD( CALCULATE(SUM(Transactions[Sales]),'Date Table'[Month] = selected_month),'Date Table'[Date])
```

## 🛠️ Prerequisites
Before using or modifying this project, make sure you have:
### Power BI Desktop
Install the latest version of Power BI Desktop to open and work with the ```text .pbix ``` file.
### Sales Dataset
A CSV or Excel dataset containing coffee shop transaction information with fields comparable to those described in the **Dataset** section.
### Basic Power BI Knowledge
* A basic understanding of the following is recommended:  
* Data import and transformation  
* Power Query  
* Data modeling  
* DAX measures  
* Creating and formatting Power BI visuals  
* Using filters and slicers  

## 📈 How to Use the Dashboard

### Select the Analysis Period
Use the **Month** slicer/dropdown to select the month you want to analyze.  
The dashboard can be used to examine a particular month, with the default view configured for **May 2023**.  

### Analyze Business Performance
Use the dashboard visuals to explore:
* Overall sales performance  
* Number of orders  
* Product quantity sold  
* Daily sales movement  
* Product category performance  
* Product type performance  
* Store-level sales  
* Weekday vs. weekend sales  
* Sales distribution by day and hour  

### Interactive Analysis
Power BI's interactive features allow users to:
* Apply filters  
* Drill into visual data  
* Hover over charts for additional information  
* Compare different business dimensions  
* Analyze performance across different time periods  

## 📊 Dashboard Components
The report consists of multiple interactive visuals designed to provide a comprehensive view of coffee shop sales performance.
### 🔹 Month Filter
A month-based slicer allows users to select the period they want to analyze.
### 🔹 KPI Cards
The KPI section displays major business metrics including:
* Total Sales  
* Total Orders  
* Total Quantity Sold
The KPIs also provide **month over month comparisons** to help identify changes in performance.
### 🔹 Sales Trend by Date
A line chart displays sales movement across individual dates.  
An average sales reference line is included to provide context for identifying days with relatively higher or lower sales.
### 🔹 Weekday vs. Weekend Sales
A donut chart illustrates the proportion of sales generated during:
* Weekdays  
* Weekends  
This helps identify differences in customer purchasing behavior throughout the week.
### 🔹 Sales by Product Category
A bar chart compares revenue across major product categories such as:
* Coffee  
* Tea  
* Bakery  
* Other available categories  
This view helps identify categories contributing significantly to overall revenue.
### 🔹 Sales by Product Type
A more detailed product-level analysis breaks down sales by individual product types within each category.  
This enables users to identify products that generate higher sales volumes or revenue.  
### 🔹 Sales by Store Location
Sales performance is compared across different store locations.  
The visualization also incorporates month-over-month changes, making it easier to understand how individual locations are performing over time.  
### 🔹 Sales by Day & Hour
A heatmap visualizes sales activity across different days of the week and hours of the day.  
* This helps identify:  
* Peak sales hours  
* High-performing days  
* Low-activity periods  
* Potential opportunities for operational optimization  

## 🎯 Business Insights
The dashboard can be used by business and operations teams to answer questions such as:

* Which products generate the highest sales?  
* Which product categories contribute most to revenue?  
* Which store locations are performing strongly?  
* How does sales performance change month over month?  
* Are weekends generating more sales than weekdays?  
* What are the busiest hours of the day?  
* Which periods experience comparatively lower sales?  
* Where could staffing or operational resources be optimized?  

## 🧰 Tools & Technologies
* ower BI Desktop  
* Power Query  
* DAX  
* Data Modeling  
* CSV / Excel  
* Data Visualization  
* Business Intelligence & Analytics  

## 📁 Project Structure

Coffee-Shop-Sales-Dashboard/  
│  
├── CoffeeShopSalesDashboard.pbix  
├── Dataset/  
│   └── coffee_shop_sales.csv  
├── Screenshots/  
│   └── dashboard.png  
└── README.md  













