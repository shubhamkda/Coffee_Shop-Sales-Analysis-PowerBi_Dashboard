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
Average Sales = AVERAGEX( ALLSELECTED(Transactions[transaction_date]), 'Date Table'[Total Sales] )
```















