---
title: SQL Essentials - JOIN
date: 2025-05-04
draft: false
summary: Understand how SQL JOINs work — including INNER, LEFT, RIGHT, FULL, and SELF JOIN
math: true
tags: [SQL]
---

# JOIN in SQL

## What is a JOIN?

A `JOIN` clause in SQL is used to retrieve data from two or more tables based on a related column between them. It allows for the combination of rows where there is a logical relationship between the datasets.


### Determining Left and Right Tables

In a SQL `JOIN`, the table that appears first after the `FROM` keyword is referred to as the **left table**, and the table that follows the `JOIN` keyword is referred to as the **right table**. This distinction is critical in `LEFT` and `RIGHT` joins.

```sql
SELECT ...
FROM table1 -- Left Table
JOIN table2 -- Right Table
ON table1.id = table2.id; -- Match Condition
```

### Tables Used in Examples

**Table: `students`**

| student_id | name  |
|------------|-------|
| 1          | Alice |
| 2          | Bob   |
| 3          | Carol |
| 4          | David |

**Table: `scores`**

| student_id | score |
|------------|-------|
| 1          | 95    |
| 2          | 88    |
| 4          | 70    |
| 5          | 100   |

---

## Types of JOINs

### 1. INNER JOIN

Returns only those records where there is a match in both tables.
- If we just write `JOIN`, SQL assumes you mean `INNER JOIN` by default.

```sql
SELECT students.name, scores.score
FROM students
INNER JOIN scores -- OR: JOIN scores
ON students.student_id = scores.student_id;
```

**Output:**

| name  | score |
|-------|-------|
| Alice | 95    |
| Bob   | 88    |
| David | 70    |

Carol is not included because she has no score.  
Student ID 5 is not included because there is no matching student.

---

### 2. LEFT JOIN (LEFT OUTER JOIN)

Returns all records from the left table, and the matched records from the right table. If no match exists, NULL values are returned for columns from the right table.

```sql
SELECT students.name, scores.score
FROM students
LEFT JOIN scores
ON students.student_id = scores.student_id;
```

**Example Output:**

| name  | score |
|-------|-------|
| Alice | 95    |
| Bob   | 88    |
| Carol | NULL  |
| David | 70    |

---

### 3. RIGHT JOIN (RIGHT OUTER JOIN)

Returns all records from the right table, and the matched records from the left table. If no match exists, NULL values are returned for columns from the left table.

```sql
SELECT students.name, scores.score
FROM students
RIGHT JOIN scores
ON students.student_id = scores.student_id;
```

**Example Output:**

| name  | score |
|-------|-------|
| Alice | 95    |
| Bob   | 88    |
| David | 70    |
| NULL  | 100   |

The last row represents a score entry without a corresponding student (student_id = 5).

---

### 4. FULL JOIN (FULL OUTER JOIN)

Returns all records when there is a match in either the left or right table. Non-matching rows are returned with NULLs for the missing side.

```sql
SELECT students.name, scores.score
FROM students
FULL JOIN scores
ON students.student_id = scores.student_id;
```

**Example Output:**

| name  | score |
|-------|-------|
| Alice | 95    |
| Bob   | 88    |
| Carol | NULL  |
| David | 70    |
| NULL  | 100   |

Carol has no score, and student_id 5 has a score but no matching student.

---

## Self JOIN

A self join is a join of a table with itself. It is commonly used for hierarchical data, such as employees and their managers.

### Example Table: `employees`

| emp_id | name   | manager_id |
|--------|--------|------------|
| 1      | Alice  | NULL       |
| 2      | Bob    | 1          |
| 3      | Carol  | 1          |
| 4      | David  | 2          |



```sql
SELECT e.name AS employee_name, m.name AS manager_name
FROM employees e
LEFT JOIN employees m
  ON e.manager_id = m.emp_id;
```
| employee_name | manager_name |
|---------------|--------------|
| Alice         | NULL         |
| Bob           | Alice        |
| Carol         | Alice        |
| David         | Bob          |


This allows for comparing records within the same dataset.

---
## JOIN Conditions Using WHERE vs ON

JOIN conditions can be written using either `ON` or `WHERE`. However, the `ON` clause is preferred, especially when working with outer joins, as it clearly separates join logic from filter logic.

```sql
-- Preferred
SELECT ...
FROM a
JOIN b ON a.id = b.id;
```

```sql
-- Less preferred (older style)
SELECT ...
FROM a, b
WHERE a.id = b.id;
```

Filtering after a `LEFT/RIGHT/FULL JOIN` using `WHERE` may unintentionally exclude NULL-matched rows. Use `ON` for conditions that are part of the join logic.

### Example:
```sql
SELECT students.name, scores.score
FROM students
LEFT JOIN scores
  ON students.student_id = scores.student_id AND scores.score > 90;
```
**Result:**

| name  | score |
|-------|-------|
| Alice | 95    |
| Bob   | NULL  |
| Carol | NULL  |
| David | NULL  |
- Alice matches the condition and joins successfully.
- Bob, Carol, and David remain in the result with `NULL` scores because they didn’t meet the filter, but `LEFT JOIN` preserves them.

```sql
SELECT students.name, scores.score
FROM students
LEFT JOIN scores
  ON students.student_id = scores.student_id
WHERE scores.score > 90;
```

**Result:**

| name  | score |
|-------|-------|
| Alice | 95    |
- Only Alice is returned because `WHERE scores.score > 90` filters out all other rows, including those with `NULL`.

---

## JOINs with Comparison Operators

JOINs can be constructed using inequality or range-based conditions. This is useful for business rules like tiered discounts or overlapping date ranges.

```sql
SELECT p.name, p.price, d.discount_percent
FROM products p
JOIN discounts d
  ON p.price >= d.min_price;
```

Use aggregation functions like `MAX()` and `GROUP BY` to obtain the best applicable match.

---

## JOINs on Multiple Keys

In many cases, a single column is insufficient to uniquely identify relationships between rows. Multiple keys can be used with an `AND` operator.

```sql
SELECT ...
FROM orders o
JOIN inventory i
ON o.order_id = i.order_id AND o.product_id = i.product_id;
```

---

## References
These notes are based on the [Mode Intermediate SQL: JOIN](https://mode.com/sql-tutorial/sql-joins). I've written them to help myself quickly recall `JOIN` in SQL.