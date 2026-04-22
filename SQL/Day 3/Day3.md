# SQL Tutorial: Day 3

## Data Sorting and Limiting

### ORDER BY Clause 

Used to sort results by one or more columns.

Best Practice: Always specify column names rather than column positions (e.g., ORDER BY 1) to ensure your code doesn't break if table structures change.

You can use aliases defined in your SELECT clause for sorting.

```sql
SELECT employee_id, salary
FROM employees
ORDER BY salary DESC;
```

You can sort by multiple columns too:

```sql
SELECT employee_id, department_id, salary
FROM employees
ORDER BY department_id ASC, salary DESC;
```

### LIMIT Clause

Use this to restrict the number of rows returned, which is essential for performance and managing large datasets (like pagination).

```sql
SELECT employee_id, first_name, last_name
FROM employees
ORDER BY hire_date DESC
LIMIT 10;
```

In some SQL dialects, `LIMIT` can be combined with `OFFSET`:

```sql
SELECT employee_id, first_name, last_name
FROM employees
ORDER BY hire_date DESC
LIMIT 10 OFFSET 20;
```

> Tip: `LIMIT` is especially useful when you only need the top rows, such as top earners or most recent records.

## Introduction to Joins

Why joins? Data is normalized across related tables to avoid redundancy, so joins bring that related information back together into meaningful reports.

### INNER JOIN

Returns rows when there is a matching value in both tables.

```sql
SELECT e.employee_id,
       e.first_name,
       e.last_name,
       d.department_name
FROM employees e
INNER JOIN departments d
    ON e.department_id = d.department_id;
```

This query returns only employees assigned to a department.

<!-- ### LEFT JOIN (LEFT OUTER JOIN)

Returns all rows from the left table, and matching rows from the right table. When there is no match, the right-side columns return `NULL`.

```sql
SELECT c.customer_id,
       c.customer_name,
       o.order_id,
       o.order_date
FROM customers c
LEFT JOIN orders o
    ON c.customer_id = o.customer_id;
```

This is useful to find customers who may not have placed any orders yet.

### RIGHT JOIN (RIGHT OUTER JOIN)

Returns all rows from the right table, and matching rows from the left table.

```sql
SELECT p.product_id,
       p.product_name,
       s.supplier_name
FROM suppliers s
RIGHT JOIN products p
    ON s.supplier_id = p.supplier_id;
```

This query returns all products, even if a corresponding supplier record does not exist.

### FULL OUTER JOIN

Returns rows when there is a match in one of the tables.

```sql
SELECT a.id,
       a.value AS value_a,
       b.value AS value_b
FROM table_a a
FULL OUTER JOIN table_b b
    ON a.id = b.id;
```

This query returns rows from both tables, with `NULL` for any missing matches.

### CROSS JOIN

Returns the Cartesian product of both tables. Every row in the first table is combined with every row in the second table.

```sql
SELECT p.product_name,
       c.country_name
FROM products p
CROSS JOIN countries c;
```

Use this join only when you intentionally need every combination of rows.

### SELF JOIN

A self join joins a table to itself. This is useful for hierarchical or related records in the same table.

```sql
SELECT m.employee_id,
       m.first_name AS manager_name,
       e.employee_id AS employee_id,
       e.first_name AS employee_name
FROM employees e
LEFT JOIN employees m
    ON e.manager_id = m.employee_id;
``` -->

### Join Best Practices

- Use table aliases for readability: `FROM customers c JOIN orders o`
- Always include the join condition in the `ON` clause.
<!-- - Prefer explicit join syntax (`JOIN ... ON`) over comma-separated joins.
- Use `LEFT JOIN` only when you need unmatched left-side rows.
- Avoid `CROSS JOIN` unless a full Cartesian product is required. -->

## Practical Examples

### Example: Top Salaries by Department

```sql
SELECT d.department_name,
       e.employee_id,
       e.first_name,
       e.salary
FROM employees e
JOIN departments d
    ON e.department_id = d.department_id
ORDER BY d.department_name ASC,
         e.salary DESC
LIMIT 5;
```

### Example: Recent Orders with Customer Names

```sql
SELECT o.order_id,
       o.order_date,
       c.customer_name
FROM orders o
JOIN customers c
    ON o.customer_id = c.customer_id
ORDER BY o.order_date DESC
LIMIT 20;
```

<!-- ### Example: Employees Without Orders

```sql
SELECT e.employee_id,
       e.first_name,
       e.last_name
FROM employees e
LEFT JOIN orders o
    ON e.employee_id = o.sales_person_id
WHERE o.order_id IS NULL;
``` -->

<!-- This query identifies employees who are not linked to any sales order. -->

## Summary

- `ORDER BY` sorts result sets by one or more columns.
- `LIMIT` reduces the number of returned rows and improves query performance.
- `JOIN` allows combining related data from multiple tables.
<!-- - Use the correct join type for your business question: `INNER JOIN` for matching rows, `LEFT JOIN` for all left-side rows, `RIGHT JOIN` for all right-side rows, and `FULL OUTER JOIN` for all rows from both sides. -->
- Table aliases help keep joins readable and maintainable.
