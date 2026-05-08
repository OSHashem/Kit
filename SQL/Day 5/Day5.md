# SQL Course - Day 5

## The USING Clause:

A cleaner alternative to the ON clause, used to simplify join conditions when tables share identical column names. Instead of ON table1.column = table2.column, you can simply use USING (column).

EXAMPLE:

```sql
SELECT
    o.order_id,
    c.customer_name,
    sh.name as shipper_name
FROM orders o
JOIN customers c
USING (customer_id)
join shippers sh
using (shipper_id)
```

## Natural Joins

This command automatically joins tables based on columns with the same name. While convenient, it is often discouraged for production code because it lacks explicit join logic, which can lead to unexpected results if the table schema changes.

EXAMPLE:

```sql
SELECT
    order_id,
    customer_name,
    product_name
FROM orders
NATURAL JOIN customers
NATURAL JOIN products
```

**Note:** The NATURAL JOIN assumes that any columns with matching names in both tables are join keys. This can be risky if column names don't align with your intended join logic.

## Cross Joins

Combines every single row from the first table with every single row from the second table, creating a Cartesian product. It can be written using either implicit syntax (using a comma) or explicit syntax (CROSS JOIN).

EXAMPLE:

```sql
-- Explicit syntax
SELECT
    c.customer_name,
    p.product_name
FROM customers c
CROSS JOIN products p;

-- Implicit syntax
SELECT
    c.customer_name,
    p.product_name
FROM customers c, products p;
```

**Use Case:** Cross joins are useful for generating combinations, such as creating a list of all possible customer-product pairs or generating date ranges with categories. Use with caution as they can result in very large result sets (rows in table1 × rows in table2).

## Unions

Used to combine rows from multiple SELECT statements into a single result set. This is particularly useful for labeling data from different queries (e.g., categorizing orders as 'active' or 'archived') and merging them into a comprehensive report.

### UNION vs UNION ALL

- **UNION**: Removes duplicate rows from the result set
- **UNION ALL**: Keeps all rows, including duplicates (faster performance)

EXAMPLE:

```sql
-- UNION (removes duplicates)
SELECT 
    customer_name,
    'Active' as status
FROM customers
WHERE active = 1

UNION

SELECT 
    customer_name,
    'Inactive' as status
FROM customers
WHERE active = 0;

-- UNION ALL (keeps duplicates)
SELECT employee_name FROM current_employees
UNION ALL
SELECT employee_name FROM former_employees;
```

**Important Rules for UNION:**
- All SELECT statements must have the same number of columns
- Columns must have compatible data types
- Column names from the first SELECT determine the result set column names
- ORDER BY must be at the end of the entire UNION statement

## Key Takeaways

| Concept | Purpose | Use Case |
|---------|---------|----------|
| USING Clause | Simplify joins with identical column names | When tables share common column names |
| Natural Join | Automatic join based on matching column names | Quick queries (not recommended for production) |
| Cross Join | Cartesian product of all rows | Generate combinations, all possible pairs |
| UNION | Combine rows from multiple queries | Merge different result sets, categorize data |
