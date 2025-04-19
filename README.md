**Superstore Sales Analysis using MySQL**

This project demonstrates how to import, structure, and analyze sales data from a retail dataset (Superstore.csv) using MySQL Workbench on Windows.
Dataset
- File: Superstore.csv
- Source: Sample sales data containing order details, customer information, sales, profits, shipping, and product info.

Database Setup

1. Create Database
CREATE DATABASE sales_data;
USE sales_data;

2. CREATE TABLE superstore (
  Row_ID INT,
  Order_ID VARCHAR(20),
  Order_Date VARCHAR(20),
  Ship_Date VARCHAR(20),
  Ship_Mode VARCHAR(50),
  Customer_ID VARCHAR(20),
  Customer_Name VARCHAR(100),
  Segment VARCHAR(50),
  Country VARCHAR(50),
  City VARCHAR(50),
  State VARCHAR(50),
  Postal_Code VARCHAR(20),
  Region VARCHAR(50),
  Product_ID VARCHAR(50),
  Category VARCHAR(50),
  Sub_Category VARCHAR(50),
  Product_Name TEXT,
  Sales FLOAT,
  Quantity INT,
  Discount FLOAT,
  Profit FLOAT
);

3. Importing Data Using MySQL Workbench
Used the "Table Data Import Wizard"
Located the CSV: C:\Users\Vaishnavi\OneDrive\Desktop\Superstore.csv
Selected the target table: superstore

4. View Top Customers
SELECT Customer_Name, SUM(Sales) AS Total_Sales
FROM superstore
GROUP BY Customer_Name
ORDER BY Total_Sales DESC
LIMIT 10;

5. Monthly Sales Trend
SELECT 
  MONTH(STR_TO_DATE(Order_Date, '%m/%d/%Y')) AS OrderMonth,
  SUM(Sales) AS TotalSales
FROM superstore
GROUP BY OrderMonth
ORDER BY OrderMonth;

6. Sales by Category
SELECT Category, SUM(Sales) AS Total_Sales
FROM superstore
GROUP BY Category;

