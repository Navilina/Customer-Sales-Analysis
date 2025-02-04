# Customer-Sales-Analysis


# 📊 Customer Sales Analysis  

## 📌 Project Overview  
This project analyzes customer purchases to identify top-selling products, monthly trends, and high-value customers using SQL.  

## 📂 Dataset  
- `customers.csv` - Customer details (ID, Name, Location)  
- `orders.csv` - Order transactions (Order ID, Customer ID, Product ID, Date, Amount)  
- `products.csv` - Product details (Product ID, Name, Category)  

## 🔍 Key SQL Queries  
1️⃣ **Top 5 Best-Selling Products** - Identifies the highest-selling products  
2️⃣ **Monthly Revenue Analysis** - Tracks revenue trends over time  
3️⃣ **High-Value Customers** - Finds top 10 customers based on spending  

## 🚀 How to Use  
1. Download the dataset from `/data`  
2. Run the SQL scripts in `/queries`  
3. Analyze the insights!  

SELECT 
    p.product_name, 
    SUM(o.quantity) AS total_sold
FROM orders o
JOIN products p ON o.product_id = p.product_id
GROUP BY p.product_name
ORDER BY total_sold DESC
LIMIT 5;


SELECT 
    DATE_TRUNC('month', order_date) AS month, 
    SUM(total_amount) AS revenue
FROM orders
GROUP BY month
ORDER BY month;


SELECT 
    c.customer_name, 
    SUM(o.total_amount) AS total_spent
FROM customers c
JOIN orders o ON c.customer_id = o.customer_id
GROUP BY c.customer_name
ORDER BY total_spent DESC
LIMIT 10;
