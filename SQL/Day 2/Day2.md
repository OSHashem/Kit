# SQL Tutorial: Day 2

## Logical Operators

Logical operators let you combine or negate conditions in the `WHERE` clause.

### 1. AND

Used to filter rows where all conditions must be met.

Example:

```sql
SELECT customer_id, full_name, birth_date, points
FROM customers
WHERE birth_date > '1990-01-01'
  AND points > 1000;
```

This returns only customers born after 1990-01-01 who also have more than 1000 points.

### 2. OR

Used to filter rows where at least one condition must be met.

Example:

```sql
SELECT customer_id, full_name, city, status
FROM customers
WHERE city = 'Cairo'
   OR city = 'Alexandria';
```

This returns customers located in either Cairo or Alexandria.

### 3. NOT

Used to negate a condition (exclude records).

Example:

```sql
SELECT customer_id, full_name, email
FROM customers
WHERE NOT status = 'inactive';
```

This returns customers whose status is not `inactive`.

You can also combine `NOT` with `AND` / `OR`:

```sql
SELECT order_id, order_date, amount
FROM orders
WHERE NOT (amount < 50 OR status = 'cancelled');
```

## The IN Operator (0:51:38 - 0:54:41)

A cleaner alternative to multiple `OR` statements when comparing a column against a list of values.

Example:

```sql
SELECT product_id, product_name, category
FROM products
WHERE category IN ('Beverages', 'Snacks', 'Desserts');
```

Equivalent using `OR`:

```sql
SELECT product_id, product_name, category
FROM products
WHERE category = 'Beverages'
   OR category = 'Snacks'
   OR category = 'Desserts';
```

## The BETWEEN Operator (0:54:41 - 0:56:53)

Use this to select data within a range (inclusive of start and end values). It is more readable than using `>=` and `<=`.

Example with numbers:

```sql
SELECT order_id, order_date, amount
FROM orders
WHERE amount BETWEEN 100 AND 500;
```

This includes rows where `amount` is exactly 100 or 500 (inclusive)

Example with dates:

```sql
SELECT order_id, customer_id, order_date
FROM orders
WHERE order_date BETWEEN '2024-01-01' AND '2024-03-31';
```

This includes rows where `order_date` is on or between the two dates. (inclusive)

## The LIKE Operator (0:56:53 - 1:02:31)

Essential for pattern matching. Note the wildcard characters:

- `%` represents any number of characters.
- `_` represents a single character.

Example: strings that start with `A`:

```sql
SELECT customer_id, full_name
FROM customers
WHERE full_name LIKE 'A%';
```

Example: strings that end with `son`:

```sql
SELECT customer_id, full_name
FROM customers
WHERE full_name LIKE '%son';
```

Example: strings that contain `tech`:

```sql
SELECT product_id, product_name
FROM products
WHERE product_name LIKE '%tech%';
```

Example: exactly 5 characters long and starting with `B`:

```sql
SELECT code
FROM promo_codes
WHERE code LIKE 'B____';
```

## The REGEXP Operator (1:02:31 - 1:11:51)

For advanced pattern matching. Use regular expressions when `LIKE` is not enough.

Common symbols:

- `^` indicates the beginning of a string.
- `$` indicates the end of a string.
- `|` means OR between patterns.
- `[]` defines a set of characters.
- `.` matches any single character.

Example: names starting with `A` or `E`:

```sql
SELECT customer_id, full_name
FROM customers
WHERE full_name REGEXP '^(A|E)';
```

Example: phone numbers with exactly 10 digits:

```sql
SELECT customer_id, phone_number
FROM customers
WHERE phone_number REGEXP '^[0-9]{10}$';
```

Example: email addresses from Gmail or Yahoo:

```sql
SELECT email
FROM customers
WHERE email REGEXP '^[^@]+@(gmail\.com|yahoo\.com)$';
```

## The IS NULL Operator

Use this to identify missing data. Remember that `NULL` is not the same as an empty string or zero; it specifically represents the absence of a value.

Example: find rows where `email` is missing:

```sql
SELECT customer_id, full_name
FROM customers
WHERE email IS NULL;
```

Example: find rows where `email` is not missing:

```sql
SELECT customer_id, full_name
FROM customers
WHERE email IS NOT NULL;
```

Example: combine with other conditions:

```sql
SELECT order_id, customer_id, shipped_date
FROM orders
WHERE shipped_date IS NULL
  AND order_date < '2024-04-01';
```

## Quick Reference

- `AND` = all conditions true
- `OR` = at least one condition true
- `NOT` = reverse the condition
- `IN` = match any item in a list
- `BETWEEN` = range check inclusive
- `LIKE` = simple pattern matching
- `REGEXP` = advanced pattern matching
- `IS NULL` = check missing values
