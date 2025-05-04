---
title: SQL Essentials - Date Format
date: 2025-05-04
draft: false
summary: Learn to store, manipulate, and format dates correctly in SQL for accurate querying and sorting
math: true
tags: [SQL]
---
## PostgreSQL Date Functions

PostgreSQL provides many functions for working with dates and times:

### 1. `NOW()`

Returns the current date and time.

```sql
SELECT NOW();
```

### 2. `CURRENT_DATE` and `CURRENT_TIME`

Returns the current date or time.

```sql
SELECT CURRENT_DATE;
SELECT CURRENT_TIME;
```

### 3. `DATE_PART()`

Extracts parts of a date/time (e.g., year, month, day).

```sql
SELECT DATE_PART('year', TIMESTAMP '2025-05-04 14:45:29');
```
It will return the year part of the timestamp: 2025.


### 4. `DATE_TRUNC()`

Truncates a timestamp to a specified precision.

```sql
SELECT DATE_TRUNC('month', TIMESTAMP '2025-05-04 14:45:29');
```
This will return the timestamp truncated to the start of the month: `2025-05-01 00:00:00`.

### 5. `AGE()`

Returns the interval between two dates or timestamps.

```sql
SELECT AGE(TIMESTAMP '2025-05-04', TIMESTAMP '2020-01-01');
```
This will return the interval between the two timestamps: `5 years 4 months 3 days`.

### 6. `TO_DATE()` and `TO_TIMESTAMP()`

Converts strings into dates or timestamps.

```sql
SELECT TO_DATE('2025-05-04', 'YYYY-MM-DD');
SELECT TO_TIMESTAMP('2025-05-04 14:45:29', 'YYYY-MM-DD HH24:MI:SS');
```


### 7. `TO_CHAR()`

Formats date/time values into strings.

```sql
SELECT TO_CHAR(NOW(), 'YYYY-MM-DD HH24:MI:SS');
```

---

## Date Arithmetic and Intervals

- **Calculating Differences**: Subtracting one date from another returns an `interval`.
- **Adding Intervals**: Use `INTERVAL` to add time durations.

```sql
SELECT CURRENT_DATE - INTERVAL '6 day';
SELECT CURRENT_DATE + INTERVAL '11 week';
```

---


## Reference
These notes are based on the [Mode Date Format](https://mode.com/sql-tutorial/sql-datetime-format) and [PostgreSQL Date Functions and 7 Ways to Use Them in Business Analysis](https://mode.com/blog/postgres-sql-date-functions?utm_medium=referral&utm_source=mode-site&utm_campaign=sql-tutorial). I've written them to help myself quickly recall these useful functions in SQL.