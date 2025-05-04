---
title: Basic SQL
date: 2025-05-03
draft: false
summary: A beginner-friendly note covering basic SQL syntax and logic
math: true
tags: [SQL]
---

## Basic SQL – Key Concepts & Syntax

### Background
In the examples below, assume we have a table called `users` with the following columns:

- `name` – the user's name  
- `age` – the user's age  
- `city` – the city where the user lives  
- `signup_date` – the date the user signed up  
- `email` – the user's email address  

---

### `SELECT`
- Retrieves data from a table.
- To select specific columns:  
  ```sql
  SELECT name, age FROM users
  ```
- To select **all columns**: 
  ```sql
  SELECT * FROM users
  ```

### `WHERE`
- Filters rows that meet a condition.  
  ```sql
  SELECT * FROM users WHERE age > 30
  ```

### `LIMIT`
- Limits the number of results returned.  
  ```sql
  SELECT * FROM users LIMIT 5
  ```

### `ORDER BY`
- Sorts the results by one or more columns.  
- Default is ascending (`ASC`). Use `DESC` for descending.  
  ```sql
  SELECT * FROM users ORDER BY signup_date DESC
  ```

---

## Logical Operators

### `LIKE`
- `LIKE` is a logical operator that allows us to match on similar values or patterns.
- It is **case-sensitive** in Mode SQL.

    #### Wildcards:
    - `%` matches **any number of characters**.  
        Example:  
        ```sql
        SELECT *
        FROM users
        WHERE name LIKE 'Alex%'
        ```
        This will return rows where the `name` starts with "Alex" (e.g., "Alex", "Alexander", "Alexis").

    - `_` (underscore) matches **a single character**.  
        Example:  
        ```sql
        SELECT *
        FROM users
        WHERE email LIKE 'a_b@example.com'
        ```
        This matches emails where the second character can be anything (e.g., `a1b@example.com`, `acb@example.com`).

    #### Case-insensitive matching:
    - Use `ILIKE` instead of `LIKE` if you want the match to be **case-insensitive**.  
        Example:  
        ```sql
        SELECT *
        FROM users
        WHERE name ILIKE 'alex%'
        ```
        This matches names like "alex", "Alex", or "ALEXANDRA".

### `IN`
- Checks if a value is in a specific list.  
  ```sql
  SELECT * FROM users WHERE city IN ('NY', 'LA')
  ```

### `BETWEEN`
- Selects values within a range (inclusive).  
  ```sql
  SELECT * FROM users WHERE age BETWEEN 20 AND 30
  ```
    - This is equivalent to 
        ```sql
        SELECT * FROM users 
        WHERE age >= 20 AND age <= 30
        ```

### `IS NULL`
- Finds rows where a column has no value. We can use this to  exclude rows with missing data from our results. 
  ```sql
  SELECT * FROM users WHERE email IS NULL
  ```
- ``` WHERE email = NULL ``` will not work because we can't perform arithmetic on null values.

### `AND`
- Combines conditions where **both must be true**.  
  ```sql
  SELECT * FROM users WHERE age > 18 AND city = 'Boston'
  ```

### `OR`
- Combines conditions where **at least one must be true**.  
  ```sql
  SELECT * FROM users WHERE age < 18 OR city = 'Boston'
  ```

### `NOT`
- `NOT` is a logical operator that reverses a condition—only rows where the condition is false will be included.

    #### Example 1: `NOT BETWEEN`
    ```sql
    SELECT *
    FROM users
    WHERE age NOT BETWEEN 20 AND 30
    ```
    This will return users whose age is **not** between 20 and 30.


    #### Example 2: `NOT LIKE`
    `NOT` is often used with `LIKE` to exclude matching patterns.
    ```sql
    SELECT *
    FROM users
    WHERE name NOT LIKE '%alex%'
    ```
    This excludes any name that contains "alex".

    #### Example 3: `IS NOT NULL`
    You can also use `NOT` to check for non-null values (must use `IS NOT NULL`):
    ```sql
    SELECT *
    FROM users
    WHERE email IS NOT NULL
    ```
    This returns all users who have an email address.


## Reference
These are my study notes based on the [Mode SQL Tutorial](https://mode.com/sql-tutorial/introduction-to-sql). I’ve organized them as a personal cheat sheet for quick reference.
