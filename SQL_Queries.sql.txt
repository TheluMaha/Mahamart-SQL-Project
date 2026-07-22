show databases;
use mahamart;
select * from customers;

SELECT * FROM customers;
SELECT customer_name, email
FROM customers;
SELECT *
FROM customers
WHERE city = 'Hyderabad';
SELECT * FROM products;
SELECT product_name, price
FROM products
WHERE price > 1000;
SELECT *
FROM products
ORDER BY price DESC;
SELECT *
FROM products
ORDER BY price ASC;
SELECT COUNT(*) AS total_customers
FROM customers;
SELECT COUNT(*) AS total_products
FROM products;
SELECT AVG(price) AS average_price
FROM products;
SELECT category_id, COUNT(*) AS total_products
FROM products
GROUP BY category_id;
SELECT MAX(price) AS highest_price
FROM products;
SELECT MIN(price) AS lowest_price
FROM products;
SELECT
customers.customer_name,
orders.order_id,
orders.order_date
FROM customers
JOIN orders
ON customers.customer_id = orders.customer_id;
SELECT
orders.order_id,
products.product_name,
order_details.quantity
FROM order_details
JOIN products
ON order_details.product_id = products.product_id
JOIN orders
ON order_details.order_id = orders.order_id;
SELECT
customers.customer_name,
COUNT(orders.order_id) AS total_orders
FROM customers
JOIN orders
ON customers.customer_id = orders.customer_id
GROUP BY customers.customer_name;
SELECT product_name, price
FROM products
WHERE price >
(
SELECT AVG(price)
FROM products
);
UPDATE products
SET price = 2500
WHERE product_id = 1;
DELETE FROM customers
WHERE customer_id = 5;
CREATE VIEW customer_orders AS
SELECT
customers.customer_name,
orders.order_id,
orders.order_date
FROM customers
JOIN orders
ON customers.customer_id = orders.customer_id;
SELECT * FROM customer_orders;
SELECT product_name, price
FROM products
ORDER BY price DESC
LIMIT 5;
SELECT SUM(quantity * price) AS total_sales
FROM order_details
JOIN products
ON order_details.product_id = products.product_id;
SELECT DISTINCT customer_name
FROM customers
JOIN orders
ON customers.customer_id = orders.customer_id;
SELECT product_name
FROM products
WHERE product_id NOT IN
(
SELECT product_id
FROM order_details
);
SELECT
MONTH(order_date) AS month,
COUNT(order_id) AS total_orders
FROM orders
GROUP BY MONTH(order_date);