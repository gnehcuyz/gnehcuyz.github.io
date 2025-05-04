---
title: SQL Essentials - CASE
date: 2025-05-04
draft: false
summary: A beginner's guide to using the CASE statement for conditional queries
math: true
tags: [SQL]
---

# `CASE` in SQL

The SQL `CASE` statement enables conditional logic within queries, working like an `if/then` structure in programming. It checks conditions and returns values based on which condition is met.

---

## Basic Syntax

```sql
CASE
  WHEN condition1 THEN result1
  WHEN condition2 THEN result2
  ...
  ELSE resultN
END
```

- `WHEN`: The condition to check.
- `THEN`: The result if the condition is true.
- `ELSE`: (Optional) Fallback result if none of the conditions match.
- `END`: Marks the end of the CASE block.

### Example

```sql
SELECT name,
       CASE
         WHEN age >= 60 THEN 'Senior'
         WHEN age >= 30 THEN 'Adult'
         ELSE 'Youth'
       END AS age_group
FROM users;
```

This query groups users into age categories based on their age:
| name   | age_group |
|--------|-----------|
| Alice  | Youth     |
| Bob    | Adult     |
| Carol  | Senior    |
| David  | Youth     |
| Emily  | Senior    |

---

## `CASE` with aggregate functions
This could be hard at the very first few times, we could try this template:
```sql
SELECT 
  CASE 
    WHEN age < 18 THEN 'Under 18'
    WHEN age BETWEEN 18 AND 29 THEN '18-29'
    WHEN age >= 30 THEN '30+'
    ELSE 'Unknown'
  END AS age_group,
  * -- Can be replaced by any aggregation function
FROM users
____ -- Can add a GROUP BY, ORDER BY, etc
```

For example:
```sql
SELECT 
  CASE 
    WHEN age < 18 THEN 'Under 18'
    WHEN age BETWEEN 18 AND 29 THEN '18-29'
    WHEN age >= 30 THEN '30+'
    ELSE 'Unknown'
  END AS age_group,
  COUNT(*) AS count
FROM users
GROUP BY 
  CASE 
    WHEN age < 18 THEN 'Under 18'
    WHEN age BETWEEN 18 AND 29 THEN '18-29'
    WHEN age >= 30 THEN '30+'
    ELSE 'Unknown'
  END;
```
| age_group | count |
|-----------|-------|
| Under 18  | 4     |
| 18-29     | 10    |
| 30+       | 3     |

---

### `CASE` inside of aggregate functions
#### Example: using `CASE` inside aggregate functions to pivot data horizontally
```sql
SELECT 
  COUNT(CASE WHEN age < 18 THEN 1 ELSE NULL END) AS under_18,
  COUNT(CASE WHEN age BETWEEN 18 AND 29 THEN 1 ELSE NULL END) AS age_18_29,
  COUNT(CASE WHEN age >= 30 THEN 1 ELSE NULL END) AS age_30_plus
FROM users;
```
| under_18 | age_18_29 | age_30_plus |
|----------|-----------|-------------|
| 4        | 10        | 3           | 

---

## Reference
These notes are based on the [Mode Intermediate SQL: CASE](https://mode.com/sql-tutorial/sql-case). I've written them to help myself quickly recall `CASE` in SQL.