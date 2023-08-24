# Advanced SQL Skills Showcase

## Table of Contents

1. [Introduction](#introduction)
2. [SQL Queries](#sql-queries)
3. [Conclusion](#conclusion)

## Introduction

Welcome to my Advanced SQL Skills Showcase! In this document, I will demonstrate my proficiency in SQL through a series of carefully crafted queries and accompanying outputs. SQL (Structured Query Language) is a powerful tool for managing, querying, and analyzing data, and throughout this showcase, I will illustrate how I leverage this skill to extract valuable insights from databases. Please bear in mind that the data used for the queries has been subsetted to ensure uploading to the repo.

## SQL Queries

### Query 1: Monthly Revenue Trend

This query takes data from the "sales" table, groups it by year and month, calculates the total monthly revenue for each group, and presents the results in chronological order. It's a useful query for analyzing and visualizing revenue trends over time, helping you see how revenue varies from month to month and year to year.

#### SQL Code

```sql
-- SQL Query 1
    SELECT
      YEAR(date) AS year,
      MONTH(date) AS month,
      SUM(revenue) AS monthly_revenue
    FROM sales
    GROUP BY year, month
    ORDER BY year, month;
```
Output

![image](https://github.com/hadiabdul9999/sql_db_projects/assets/31616567/77a0eb50-6ec3-4c48-9903-bc78eacfa718)

### Query 2: Revenue by Product Hierarchy

This query retrieves data from the "sales" and "product_hierarchy" tables, joins them based on the "product_id," groups the results by different levels of the product hierarchy, calculates the total revenue for each product hierarchy, and presents the results in descending order of total revenue. It's useful for analyzing which product hierarchies generate the most revenue in your dataset.

#### SQL Code

```sql
-- SQL Query 2
    SELECT
      ph.hierarchy1_id,
      ph.hierarchy2_id,
      ph.hierarchy3_id,
      SUM(sa.revenue) AS total_revenue
    FROM sales sa
    JOIN product_hierarchy ph ON sa.product_id = ph.product_id
    GROUP BY hierarchy1_id, hierarchy2_id, hierarchy3_id
    ORDER BY total_revenue DESC;
```
Output

![image](https://github.com/hadiabdul9999/sql_db_projects/assets/31616567/862d0d5e-1cd2-473a-af9e-298dd5270f39)

### Query 3: Promotion Impact on Revenue

This query retrieves data from the "sales" table, groups it by the "promo_type_1" column, calculates the total revenue for each distinct promotional type and presents the results in descending order of total revenue. It's useful for analyzing which promotional types generate the most revenue in your dataset, helping you identify the most successful marketing strategies or promotions.

#### SQL Code

```sql
-- SQL Query 3
    SELECT
      promo_type_1,
      SUM(revenue) AS total_revenue
    FROM sales
    GROUP BY promo_type_1
    ORDER BY total_revenue DESC;
```
Output

![image](https://github.com/hadiabdul9999/sql_db_projects/assets/31616567/232c5a4e-2656-497c-8d17-de8a6841702e)

### Query 4: Sales and Stock Correlation

This query retrieves data from the "sales" table, groups it by the "product_id" column, calculate the average daily sales and average stock quantity for each distinct product, and presents the results in descending order of average daily sales. It can be used to identify which products have the highest average daily sales and compare them in terms of stock quantities.

#### SQL Code

```sql
-- SQL Query 4
    SELECT
      product_id,
      AVG(sales) AS avg_daily_sales,
      AVG(stock) AS avg_stock_quantity
    FROM sales
    GROUP BY product_id
    ORDER BY avg_daily_sales DESC;
```
Output

![image](https://github.com/hadiabdul9999/sql_db_projects/assets/31616567/cba6883b-264a-466b-a2a4-94ed09219230)

### Query 5: Profit Margin by Store Type and Promotion

This SQL query summarizes the total revenue and profit margin for each combination of "storetype_id" and "promo_type_1" by joining data from the "sales" and "store_cities" tables. It calculates the total revenue and profit margin percentages and groups the results by these two columns.

#### SQL Code

```sql
-- SQL Query 5
    SELECT
      s.store_type,
      sa.promo_type_1,
      SUM(revenue) AS total_revenue,
      SUM(revenue - (stock * price)) / SUM(revenue) * 100 AS profit_margin
    FROM sales sa
    JOIN store_cities s ON sa.store_id = s.store_id
    GROUP BY s.store_type, sa.promo_type_1;
```
Output

![image](https://github.com/hadiabdul9999/sql_db_projects/assets/31616567/19832c7b-c2a8-484c-8127-5d716d49ba05)

### Query 6: Sales Variation by City

This SQL query calculates the sales variation (the difference between the maximum and minimum sales) for each city where stores are located. It accomplishes this by joining data from the "sales" and "store_cities" tables, grouping the results by city, and then ordering the cities in descending order of their sales variation.

#### SQL Code

```sql
-- SQL Query 6
    SELECT
      c.city,
      MAX(sales) - MIN(sales) AS sales_variation
    FROM sales sa
    JOIN store_cities c ON sa.store_id = c.store_id
    GROUP BY c.city
    ORDER BY sales_variation DESC;
```
Output

![image](https://github.com/hadiabdul9999/sql_db_projects/assets/31616567/ae7897c3-2f29-4470-87d2-a6566cef4a8b)

### Query 7: Product Size Analysis

This SQL query calculates several average metrics related to product dimensions, daily sales, and daily revenue using data from the "sales" table. Here's a summary of what it does:

* AVG(sales) AS avg_daily_sales: Calculates the average daily sales.
* AVG(revenue) AS avg_daily_revenue: Calculates the average daily revenue.
In essence, this query provides an overview of sales/revenue metrics, giving you a sense of the sales performance across all data in the "sales" table.

#### SQL Code

```sql
-- SQL Query 7
    SELECT
      ROUND(AVG(product_length), 2) AS avg_length,
      ROUND(AVG(product_depth), 2) AS avg_depth,
      ROUND(AVG(product_width), 2) AS avg_width,
      AVG(sales) AS avg_daily_sales,
      AVG(revenue) AS avg_daily_revenue
    FROM sales;
```
Output

![image](https://github.com/hadiabdul9999/sql_db_projects/assets/31616567/fe35b6a3-125f-4188-977a-bcd909e2a5fb)


## Conclusion
In this comprehensive README document, we've explored a series of SQL queries and their associated outputs, showcasing a range of data analysis and manipulation techniques. This collection of SQL queries reflects my proficiency in working with databases and extracting valuable insights from data.

Throughout this README, we've covered various aspects of SQL, including:

* Data Retrieval: We've demonstrated how to extract specific information from our dataset efficiently.
* Data Transformation: You've seen how SQL can be used to clean and reshape data to suit our analytical needs.
* Data Aggregation: We've summarized and aggregated data to gain meaningful insights.
* Complex Queries: We've delved into more complex SQL operations like subqueries, joins, and window functions to solve real-world data challenges.
* Performance Optimization: We've discussed techniques for optimizing SQL queries to ensure they run efficiently, even with large datasets.
* These SQL queries and examples not only highlight my SQL skills but also offer practical insights into how SQL can be used to analyze and understand data effectively.





