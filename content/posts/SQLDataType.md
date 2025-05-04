---
title: SQL Essentials - Data Types
date: 2025-05-04
draft: true
summary: Understand common SQL data types
math: true
tags: [SQL]
---

# SQL Data Types

## Why Data Types Matter

Data types define the kind of values a column can store. Choosing appropriate types ensures data accuracy, enables correct operations (like `SUM`, `AVG`), and optimizes storage.

---

## Common SQL Data Types in Mode

| Imported As | Stored As         | Description                                          |
|-------------|------------------|------------------------------------------------------|
| String      | `VARCHAR(1024)`  | Text strings up to 1024 characters.                  |
| Date/Time   | `TIMESTAMP`      | Date & time in `YYYY-MM-DD hh:mm:ss` format.         |
| Number      | `DOUBLE PRECISION` | Numeric values with up to 17 significant digits.    |
| Boolean     | `BOOLEAN`        | Stores `TRUE` or `FALSE` values.                    |

---

## Changing Data Types

Use these to convert column types:

```sql
-- CAST syntax
CAST(column_name AS target_type)

-- PostgreSQL-style
column_name::target_type
```

Useful for converting between text and numeric/date types when operations require it.

---


## Reference

Based on [Mode SQL Tutorial - Data Types](https://mode.com/sql-tutorial/sql-data-types).
