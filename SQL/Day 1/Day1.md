# SQL Tutorial

## The SELECT Statement:

The primary command for data retrieval.

Example:

```sql
Select *
From Customers
```

## Clause Order

The order of clauses is mandatory in SQL:

```sql
SELECT
FROM
WHERE
ORDER BY
```

## Refining the SELECT Clause

You can select specific columns rather than \* (all columns).

### Arithmetic

You can perform math (e.g., unit_price \* 1.1) directly in the SELECT clause.

Example:

```sql
SELECT unit_price * 1.1
FROM Products
```

### Aliases

Use the AS keyword to rename columns in your output for better readability.

Example:

```sql
SELECT
    unit price,
    unit_price * 1.1 as "price after tax"
FROM Products
```

### DISTINCT

Use this to remove duplicate values from your result set.

Example:

```sql
SELECT DISTINCT first_name
FROM Users
```

## Filtering with WHERE

The WHERE clause allows you to filter data based on specific criteria.

You can use standard comparison operators (e.g., >, <, >=, <=, =, != or <>).

Example:

```sql
SELECT *
FROM Products
Where unit_price < 100
```
