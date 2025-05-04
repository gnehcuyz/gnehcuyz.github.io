---
title: SQL Essentials - Aggregate Functions & Grouping
date: 2025-05-04
draft: false
summary: Deep dive into GROUP BY, HAVING, COUNT, and DISTINCT in SQL
math: true
tags: [SQL]
---

## Aggregate Functions & Grouping

### Background
In the examples below, assume we have a table called `users` with the following columns:

- `name` – the user's name  
- `age` – the user's age  
- `city` – the city where the user lives  
- `signup_date` – the date the user signed up  
- `email` – the user's email address  

---
### `COUNT()`
- Returns the number of rows that match a specified condition.
- `COUNT(*)` counts all rows, **including those with NULLs**. So does `COUNT(1)`.
- `COUNT(column_name)` only counts non-null values.
```sql
SELECT COUNT(*) FROM users
```
```sql
SELECT COUNT(city) FROM users
```

### `SUM()`
- Adds all the **non-null** values in a numeric column. Treat null values as 0.
```sql
SELECT SUM(age) FROM users
```

### `MIN()` / `MAX()`
- Finds the smallest or largest value in a column.
```sql
SELECT MIN(age), MAX(age) FROM users
```

### `AVG()`
- Calculates the average of non-null numeric values in a column.
```sql
SELECT AVG(age) FROM users
```

---

### `GROUP BY`
- Groups rows that share the same value in a column so aggregate functions can be applied to each group.
```sql
SELECT city, COUNT(*) FROM users 
GROUP BY city
```
This returns a table like the following:

| city      | count |
|-----------|-------|
| New York  | 10    |
| Boston    | 7     |
| San Diego | 5     |

---

### `HAVING`
- Filters grouped records (unlike `WHERE`, which filters rows before aggregating).
```sql
SELECT city, COUNT(*) 
FROM users 
GROUP BY city 
HAVING COUNT(*) > 5
```
This returns a table like the following:
| city      | count |
|-----------|-------|
| New York  | 10    |
| Boston    | 7     |

---

### `DISTINCT`
### To view unique values
#### Examples
1. Get all the unique cities users come from:
    ```sql
    SELECT DISTINCT city FROM users
    ```
    | city        |
    |-------------|
    | New York    |
    | Boston      |
    | San Diego   |
    | Seattle     |
2. Get unique (city, age) pairs:
    ```sql
    SELECT DISTINCT city, age FROM users
    ```
    | city        | age |
    |-------------|-----|
    | New York    | 25  |
    | Boston      | 30  |
    | San Diego   | 25  |
    | New York    | 30  |
    | Seattle     | 40  |
    - This shows the **unique pairs** of city and age — meaning the same city can appear more than once, but only if it's paired with a different age. 

### Using `DISTINCT` in aggregations
```sql
SELECT COUNT(DISTINCT city) AS unique_cities
FROM users
```
| unique_cities |
|---------------|
| 4             |
- `DISTINCT` goes inside the aggregate function rather than at the beginning of the `SELECT` clause.

---

## Query Clause Order

The order in which we write SQL clauses matters. Here's the standard order for everything we've learned so far:

1. `SELECT`
2. `FROM`
3. `WHERE`
4. `GROUP BY`
5. `HAVING`
6. `ORDER BY`

## Reference
These notes are based on the [Mode Intermediate SQL Tutorial](https://mode.com/sql-tutorial/intro-to-intermediate-sql). I've written them to help myself quickly recall aggregation and grouping tools in SQL.
