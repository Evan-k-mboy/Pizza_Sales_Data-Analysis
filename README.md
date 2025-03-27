# Pizza_Sales_Data-Analysis
### Project Overview
- This project analyzes pizza sales data using SQL queries to extract key business insights. The dataset includes order details, revenue, customer purchases, and sales trends. The goal is to demonstrate intermediate SQL skills with queries focusing on aggregations, time-series analysis, and business KPIs.
  ### Key Business Questions Answered
1. What is the total revenue, total orders, and average order value (AOV)?
2. What are the daily and monthly sales trends?
3.  Which are the best-selling pizzas?
4.  Which pizza size is the most ordered?
5.  What are the peak sales hours?
   6. What percentage of revenue does each pizza category contribute?
7. Who are the most frequent customers?
   ### SQL Queries & Insights
   ## 1. Total Revenue, Orders & Average Order Value
  ```sql SELECT 
    SUM(total_price) AS total_revenue,
    COUNT(DISTINCT order_id) AS total_orders,
    ROUND(AVG(total_price), 2) AS average_order_value
FROM pizza_sales;
**2.Daily Revenue Trend**
```sql SELECT 
    order_date, 
    SUM(total_price) AS daily_revenue
FROM pizza_sales
GROUP BY order_date
ORDER BY order_date;
**3. Best-Selling Pizzas by Quantity Sold**
``` sql SELECT 
    pizza_name, 
    SUM(quantity) AS total_sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY total_sold DESC
LIMIT 10;
**4.Peak Sales Hours**
``` sql SELECT 
    EXTRACT(hour FROM order_time) AS sales_hour,
    COUNT(order_id) AS order_count
FROM pizza_sales
GROUP BY sales_hour
ORDER BY order_count DESC;
**5.Peak Sales Hours**
```sql SELECT 
    EXTRACT(hour FROM order_time) AS sales_hour,
    COUNT(order_id) AS order_count
FROM pizza_sales
GROUP BY sales_hour
ORDER BY order_count DESC;
**6.percentage of revenue  each pizza category contribute**
```sql SELECT 
    category,
    SUM(total_price) AS category_revenue,
    ROUND(SUM(total_price) * 100 / (SELECT SUM(total_price) FROM pizza_sales), 2) AS revenue_percentage
FROM pizza_sales
GROUP BY category
ORDER BY revenue_percentage DESC;
**7. Most frequent customers**
```sql SELECT 
    customer_id, 
    COUNT(order_id) AS total_orders
FROM pizza_sales
GROUP BY customer_id
ORDER BY total_orders DESC
LIMIT 10;
 **Tools Used**
1. SQL-for data analysis
2. Excel- Data Cleaning

**Key Insights & Findings
**
1. The best-selling pizza is Pepperoni Pizza, followed by BBQ Chicken Pizza.
2. Most orders happen between 6 PM - 8 PM, making it the peak sales window.
3.Large-sized pizzas are the most popular among customers
4. Discounts increase order volume but lower overall revenue per order

**How to Use This Project**
- Download the dataset (pizza_sales.csv) and import it into MySQL.
- Run the SQL queries in the pizza_sales_analysis.sql file.
-Analyze and visualize results.

