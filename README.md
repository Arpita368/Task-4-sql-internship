# Task 4: Aggregate Functions and Grouping

## Objective
Use aggregate functions and grouping to summarize data in SQL.

## Tools
- MySQL Workbench

## Table Used
Table Name: Sales

Columns:
- sale_id (INT, Primary Key) : Unique sale ID
- product_name (VARCHAR(30)) : Name of the product
- category (VARCHAR(20)) : Product category
- quantity (INT) : Quantity sold
- price_per_unit (DECIMAL(10,2)) : Price for one unit
- sale_date (DATE) : Date of sale

## Create Table & Insert Data
CREATE TABLE Sales (
    sale_id INT PRIMARY KEY,
    product_name VARCHAR(30),
    category VARCHAR(20),
    quantity INT,
    price_per_unit DECIMAL(10,2),
    sale_date DATE
);

INSERT INTO Sales VALUES
(1, 'Laptop', 'Electronics', 5, 50000.00, '2025-01-10'),
(2, 'Mouse', 'Electronics', 15, 500.00, '2025-01-12'),
(3, 'Keyboard', 'Electronics', 10, 1500.00, '2025-01-15'),
(4, 'Sofa', 'Furniture', 2, 25000.00, '2025-01-20'),
(5, 'Chair', 'Furniture', 8, 3000.00, '2025-01-22'),
(6, 'Table', 'Furniture', 4, 12000.00, '2025-01-25'),
(7, 'Pen', 'Stationery', 50, 20.00, '2025-01-28'),
(8, 'Notebook', 'Stationery', 30, 50.00, '2025-01-30'),
(9, 'Printer', 'Electronics', 3, 12000.00, '2025-02-02'),
(10, 'Bookshelf', 'Furniture', 1, 8000.00, '2025-02-05');

## Queries with Aggregate Functions & Grouping

-- 1. Total sales revenue by category (SUM)
SELECT category,
       SUM(quantity * price_per_unit) AS total_revenue
FROM Sales
GROUP BY category;

-- 2. Number of products sold in each category (COUNT)
SELECT category,
       COUNT(sale_id) AS total_products_sold
FROM Sales
GROUP BY category;

-- 3. Average price per product in each category (AVG)
SELECT category,
       AVG(price_per_unit) AS avg_price
FROM Sales
GROUP BY category;

-- 4. Highest and lowest price in each category (MAX & MIN)
SELECT category,
       MAX(price_per_unit) AS max_price,
       MIN(price_per_unit) AS min_price
FROM Sales
GROUP BY category;

-- 5. Categories with revenue > 50,000 (HAVING)
SELECT category,
       SUM(quantity * price_per_unit) AS total_revenue
FROM Sales
GROUP BY category
HAVING SUM(quantity * price_per_unit) > 50000;

-- 6. Multiple aggregate functions together
SELECT category,
       COUNT(*) AS items_count,
       SUM(quantity) AS total_units_sold,
       AVG(price_per_unit) AS avg_price,
       MAX(price_per_unit) AS highest_price
FROM Sales
GROUP BY category;

## Notes
- GROUP BY groups rows based on a column.
- Aggregate functions (SUM, COUNT, AVG, MAX, MIN) summarize data.
- HAVING is used to filter grouped data (works after aggregation).
- You can run all these queries in MySQL Workbench or DB Browser for SQLite.

## How to Run
1. Open MySQL Workbench or DB Browser for SQLite.
2. Create a new database (optional in SQLite).
3. Paste and run the CREATE TABLE and INSERT statements.
4. Run each query to see results for different aggregate functions.

## Author
Created by Arpita Jitendra Sonparote

## License
This script is for educational purposes. You can use it or modify it as per your requirement.
