# Day 3: SELECT Statement & Data Retrieval

## Introduction

The `SELECT` statement is the most commonly used SQL command. It is used to retrieve data from one or more tables. Using SELECT, we can fetch specific columns, all columns, filter records, sort data, limit results, remove duplicates, perform calculations, and group data.

---

## Syntax

```sql
SELECT column_name
FROM table_name;
```

Retrieve all columns:

```sql
SELECT *
FROM table_name;
```

---

## Example

### Select Specific Columns

```sql
SELECT id, name
FROM students;
```

### Select All Columns

```sql
SELECT *
FROM students;
```

### Filter Data Using WHERE

```sql
SELECT *
FROM students
WHERE city = 'Pune';
```

### Sort Data

```sql
SELECT *
FROM students
ORDER BY marks DESC;
```

### Limit Records

```sql
SELECT *
FROM students
LIMIT 3;
```

---

## Output

### Query

```sql
SELECT id, name
FROM students;
```

### Result

| id  | name   |
| --- | ------ |
| 101 | Rahul  |
| 102 | Navin  |
| 103 | Dikshi |
| 104 | Amit   |

The query returns only the selected columns.

---

## Important Notes

* `SELECT *` returns all columns from a table.
* `WHERE` is used to filter rows.
* `ORDER BY` is used to sort records.
* `LIMIT` restricts the number of rows returned.
* `DISTINCT` removes duplicate values.
* `GROUP BY` creates groups of rows.
* `HAVING` filters grouped data.
* `LIKE` is used for pattern matching.

---

## Common Errors

### Missing FROM Clause

```sql
SELECT id, name;
```

Error occurs because the table name is missing.

### Using HAVING Without GROUP BY

```sql
SELECT city
FROM students
HAVING COUNT(*) > 1;
```

HAVING is generally used with GROUP BY.

### Incorrect String Quotes

```sql
SELECT *
FROM students
WHERE city = Pune;
```

Correct:

```sql
SELECT *
FROM students
WHERE city = 'Pune';
```

---

## Interview Questions

### Q1. What is the difference between WHERE and HAVING?

**Answer:**

* WHERE filters rows before grouping.
* HAVING filters groups after GROUP BY.

### Q2. What is the difference between DISTINCT and GROUP BY?

**Answer:**

* DISTINCT removes duplicate rows.
* GROUP BY groups rows and is commonly used with aggregate functions.

### Q3. What is the purpose of ORDER BY?

**Answer:**

ORDER BY sorts the result set in ascending (ASC) or descending (DESC) order.

### Q4. What is the difference between COUNT(*) and COUNT(column_name)?

**Answer:**

* COUNT(*) counts all rows.
* COUNT(column_name) counts only non-NULL values.

---

## Commands Covered

### Basic SELECT

```sql
SELECT * FROM students;

SELECT name FROM students;

SELECT id, name FROM students;
```

### WHERE

```sql
SELECT *
FROM students
WHERE city = 'Pune';

SELECT *
FROM students
WHERE marks > 80;
```

### AND / OR

```sql
SELECT *
FROM students
WHERE city = 'Pune'
AND marks > 80;
```

```sql
SELECT *
FROM students
WHERE city = 'Pune'
OR city = 'Mumbai';
```

### ORDER BY

```sql
SELECT *
FROM students
ORDER BY name ASC;
```

```sql
SELECT *
FROM students
ORDER BY marks DESC;
```

### LIMIT

```sql
SELECT *
FROM students
LIMIT 3;
```

### DISTINCT

```sql
SELECT DISTINCT city
FROM students;
```

### LIKE

```sql
SELECT *
FROM students
WHERE name LIKE 'N%';
```

```sql
SELECT *
FROM students
WHERE name LIKE '%a';
```

```sql
SELECT *
FROM students
WHERE name LIKE '%a%';
```

### BETWEEN

```sql
SELECT *
FROM students
WHERE marks BETWEEN 80 AND 90;
```

### IN

```sql
SELECT *
FROM students
WHERE city IN ('Pune', 'Mumbai');
```

### Aggregate Functions

```sql
SELECT COUNT(*) FROM students;

SELECT MAX(marks) FROM students;

SELECT MIN(marks) FROM students;

SELECT AVG(marks) FROM students;

SELECT SUM(marks) FROM students;
```

### GROUP BY

```sql
SELECT city, COUNT(*)
FROM students
GROUP BY city;
```

```sql
SELECT course, AVG(marks)
FROM students
GROUP BY course;
```

### HAVING

```sql
SELECT city, COUNT(*)
FROM students
GROUP BY city
HAVING COUNT(*) > 1;
```

---

## Summary

In this chapter, we learned how to retrieve data using the SELECT statement. We explored filtering data with WHERE, sorting records using ORDER BY, limiting rows with LIMIT, removing duplicates using DISTINCT, pattern matching using LIKE, range searching with BETWEEN, multiple-value filtering using IN, aggregate functions, grouping data using GROUP BY, and filtering groups using HAVING.

### SQL Query Execution Order

```sql
FROM
WHERE
GROUP BY
HAVING
SELECT
ORDER BY
LIMIT
```
