---
title: SQL Essentials – Data Wrangling & String Functions
date: 2025-05-04
draft: true
summary: Learn how to clean and transform messy data using SQL string functions and wrangling techniques
math: true
tags: [SQL]
---

# 🧹 Data Wrangling with SQL

## What Is Data Wrangling?

Data wrangling (also known as data munging) is the process of programmatically transforming raw, messy, or inconsistent data into a structured format suitable for analysis. 

Common scenarios include:
- Fixing inconsistent date formats
- Splitting or merging columns
- Standardizing text case
- Removing unwanted characters

These tasks are essential before performing meaningful analysis or building dashboards.

---

# SQL String Functions for Cleaning Data

SQL provides a suite of string functions to help clean and manipulate text data:

### `LEFT()`, `RIGHT()`, and `LENGTH()`

Extract substrings from the left or right of a string.

```sql
SELECT
  LEFT(column_name, n) AS left_substring,
  RIGHT(column_name, n) AS right_substring,
  LENGTH(column_name) AS string_length
FROM your_table;
```

### `TRIM()`

Remove leading and trailing spaces or specified characters.

```sql
SELECT TRIM(BOTH ' ' FROM column_name) AS trimmed_column
FROM your_table;
```

### `POSITION()` and `STRPOS()`

Find the position of a substring within a string.

```sql
SELECT POSITION('substring' IN column_name) AS position
FROM your_table;
```

### `SUBSTRING()`

Extract a substring from a string starting at any position.

```sql
SELECT SUBSTRING(column_name FROM start_position FOR length) AS substring
FROM your_table;
```

### `CONCAT()`

Concatenate two or more strings.

```sql
SELECT CONCAT(column1, ' ', column2) AS full_name
FROM your_table;
```

### `UPPER()` and `LOWER()`

Convert strings to uppercase or lowercase.

```sql
SELECT UPPER(column_name) AS uppercased, LOWER(column_name) AS lowercased
FROM your_table;
```

### `COALESCE()`

Return the first non-null value in a list.

```sql
SELECT COALESCE(column1, column2, 'default') AS result
FROM your_table;
```

---

#  Handling Dates Stored as Strings

When dates are stored as strings, it's crucial to convert them to proper date formats for accurate analysis.

### Extracting Date and Time Components

Assuming a datetime string in the format `'YYYY-MM-DD HH:MM:SS'`:

```sql
SELECT
  LEFT(datetime_column, 10) AS date_part,
  RIGHT(datetime_column, 8) AS time_part
FROM your_table;
```

### Converting Strings to Dates

Convert a string to a date using `TO_DATE()` or `CAST()`:

```sql
SELECT TO_DATE('2025-05-04', 'YYYY-MM-DD') AS converted_date;
-- or
SELECT CAST('2025-05-04' AS DATE) AS converted_date;
```

---

# 📚 References

- [Data Wrangling with SQL – Mode Analytics](https://mode.com/sql-tutorial/data-wrangling-with-sql/)
- [Using SQL String Functions to Clean Data – Mode Analytics](https://mode.com/sql-tutorial/sql-string-functions-for-cleaning/)
