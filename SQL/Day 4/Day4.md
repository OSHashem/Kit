# SQL Tutorial: Day 4

## Joining Across Databases

Concept: Combining tables from different databases on the same server.

Syntax: Use the database_name.table_name prefixing method.

Example:
```sql
SELECT *
FROM order_items oi
JOIN sql_inventory.products p
ON oi.product_id = p.product_id;
```

## Self Joins 

Use Case: Ideal for hierarchical or organizational data where a record refers to another record in the same table (e.g., an employee pointing to their manager).

Note: You must use table aliases (e.g., e and m) to treat the single table as two separate entities during the join.

Example:
```sql
SELECT e.employee_name AS employee, m.employee_name AS manager
FROM employees e
LEFT JOIN employees m ON e.manager_id = m.employee_id;
```
This query retrieves each employee's name along with their manager's name by joining the employees table to itself.

## Joining Multiple Tables

Best Practice: Always give each table a distinct alias to keep the query clean and prevent ambiguity. Chain the JOIN statements logically.

Example:
```sql
SELECT c.customer_name, o.order_date, p.product_name, oi.quantity
FROM customers c
JOIN orders o ON c.customer_id = o.customer_id
JOIN order_items oi ON o.order_id = oi.order_id
JOIN products p ON oi.product_id = p.product_id;
```
This query joins four tables to get customer names, order dates, product names, and quantities for each order item.


## Compound Join Conditions

Scenario: When a table uses a composite primary key (multiple columns defining a unique row).
Syntax: Include all relevant columns in the ON clause using the AND operator (e.g., ON t1.col1 = t2.col1 AND t1.col2 = t2.col2).

Example:
```sql
SELECT *
FROM enrollments e
JOIN courses c ON e.student_id = c.student_id AND e.course_id = c.course_id;
```
Assuming enrollments has a composite key of student_id and course_id, this joins on both columns.

## Join Syntax Standards

Explicit vs. Implicit: Distinguish between the Implicit Syntax (using commas in the FROM clause—now considered outdated/prone to error) and the Explicit Syntax (using the JOIN keyword—the modern, recommended standard).

Implicit Syntax Example:
```sql
SELECT *
FROM table1, table2
WHERE table1.id = table2.id;
```

Explicit Syntax Example:
```sql
SELECT *
FROM table1
JOIN table2 ON table1.id = table2.id;
```
The explicit syntax is clearer and less error-prone, especially with complex joins.

## Outer Joins

Logic: LEFT JOIN includes all records from the left table, even if there is no match in the right table (missing data appears as NULL).

Best Practice: LEFT JOIN over RIGHT JOIN for better readability.

Advanced: Understand how to apply LEFT JOIN across multiple tables and how to perform Self Outer Joins to maintain all parent records even without children.

Types of Outer Joins:
- LEFT JOIN (or LEFT OUTER JOIN): Includes all from left table.
- RIGHT JOIN (or RIGHT OUTER JOIN): Includes all from right table.
- FULL OUTER JOIN: Includes all from both tables.

LEFT JOIN Example:
```sql
SELECT c.customer_name, o.order_date
FROM customers c
LEFT JOIN orders o ON c.customer_id = o.customer_id;
```
This shows all customers, even those without orders (order_date will be NULL).

RIGHT JOIN Example:
```sql
SELECT c.customer_name, o.order_date
FROM customers c
RIGHT JOIN orders o ON c.customer_id = o.customer_id;
```
This shows all orders, even if customer is missing.

Self Outer Join Example:
```sql
SELECT e.employee_name, m.employee_name AS manager
FROM employees e
LEFT JOIN employees m ON e.manager_id = m.employee_id;
```
This ensures all employees are listed, even if they have no manager.

## Summary

- **Joining Across Databases**: Use fully qualified table names (database.table) to join tables from different databases.
- **Self Joins**: Use aliases to join a table to itself for hierarchical data.
- **Multiple Tables**: Chain JOINs with aliases for clarity.
- **Compound Conditions**: Use AND in ON clause for composite keys.
- **Syntax**: Prefer explicit JOIN syntax over implicit.
- **Outer Joins**: LEFT JOIN is most common; includes all from left table.

