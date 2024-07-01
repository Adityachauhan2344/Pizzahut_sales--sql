Pizza Hut Sales Analysis 2015

Overview
This project presents a comprehensive analysis of Pizza Hut's sales performance for the year 2015. Utilizing MySQL for data retrieval and analysis, we have explored various facets of the sales data, from basic metrics to advanced insights. This README provides an overview of the SQL queries used and the key findings from the analysis.

Basic Analysis
Total Number of Orders Placed:

Query: SELECT COUNT(*) AS total_orders FROM orders;
Total Revenue Generated from Pizza Sales:

Query: SELECT SUM(total_amount) AS total_revenue FROM orders;
Highest-Priced Pizza:

Query: SELECT name, MAX(price) AS highest_price FROM pizzas;
Most Common Pizza Size Ordered:

Query: SELECT size, COUNT(*) AS frequency FROM orders GROUP BY size ORDER BY frequency DESC LIMIT 1;
Top 5 Most Ordered Pizza Types:

Query: SELECT name, COUNT(*) AS quantity FROM orders GROUP BY name ORDER BY quantity DESC LIMIT 5;
Intermediate Analysis
Total Quantity of Each Pizza Category Ordered:

Query: SELECT category, SUM(quantity) AS total_quantity FROM orders INNER JOIN pizzas ON orders.pizza_id = pizzas.id GROUP BY category;
Distribution of Orders by Hour of the Day:

Query: SELECT HOUR(order_time) AS hour, COUNT(*) AS order_count FROM orders GROUP BY hour;
Category-Wise Distribution of Pizzas:

Query: SELECT category, COUNT(*) AS quantity FROM orders INNER JOIN pizzas ON orders.pizza_id = pizzas.id GROUP BY category;
Average Number of Pizzas Ordered per Day:

Query: SELECT order_date, AVG(quantity) AS average_pizzas FROM orders GROUP BY order_date;
Top 3 Most Ordered Pizza Types Based on Revenue:

Query: SELECT name, SUM(total_amount) AS total_revenue FROM orders GROUP BY name ORDER BY total_revenue DESC LIMIT 3;
Advanced Analysis
Percentage Contribution of Each Pizza Type to Total Revenue:

Query: SELECT name, (SUM(total_amount) / (SELECT SUM(total_amount) FROM orders) * 100) AS revenue_percentage FROM orders GROUP BY name;
Cumulative Revenue Generated Over Time:

Query: SELECT order_date, SUM(total_amount) OVER (ORDER BY order_date) AS cumulative_revenue FROM orders;
Top 3 Most Ordered Pizza Types by Revenue for Each Pizza Category:

Query: SELECT category, name, SUM(total_amount) AS total_revenue FROM orders INNER JOIN pizzas ON orders.pizza_id = pizzas.id GROUP BY category, name ORDER BY category, total_revenue DESC LIMIT 3;
Conclusion
This analysis provides valuable insights into Pizza Hut's sales performance in 2015. By leveraging MySQL and SQL queries, we have identified key trends and metrics that can inform strategic decisions and drive future success.

How to Use
Clone the repository.
Import the dataset into your MySQL server.
Run the provided SQL queries to replicate the analysis.
Feel free to contribute by suggesting improvements or adding more analyses.
