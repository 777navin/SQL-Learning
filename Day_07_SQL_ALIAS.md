# Day 07: SQL ALIAS

## Introduction

ALIAS is used to give a temporary name to a column or table in SQL.

It helps:

- Make output more readable
- Use meaningful column names
- Shorten table names
- Improve query readability

Alias only exists during query execution and does not change the actual table structure.

---

## Commands Covered

- Column Alias
- Table Alias
- Alias using AS
- Alias without AS
- Alias with Aggregate Functions
- Alias with Calculations

---

# What is an Alias?

An Alias is a temporary name assigned to a column or table.

### Syntax

```sql
SELECT column_name AS alias_name
FROM table_name;
```

---

# Column Alias

## Example 1

Display student names with a custom heading.

```sql
SELECT name AS Student_Name
FROM students;
```

### Output

```text
+--------------+
| Student_Name |
+--------------+
| Rahul        |
| Navin        |
| Dikshi       |
| Amit         |
| Priya        |
| Rohit        |
| Sneha        |
| Neha         |
+--------------+
```

---

## Example 2

Rename multiple columns.

```sql
SELECT
id AS Student_ID,
name AS Student_Name,
marks AS Total_Marks
FROM students;
```

### Output

```text
+------------+--------------+-------------+
| Student_ID | Student_Name | Total_Marks |
+------------+--------------+-------------+
| 101        | Rahul        | 85          |
| 102        | Navin        | 90          |
| 103        | Dikshi       | 95          |
| 104        | Amit         | 70          |
| 105        | Priya        | 88          |
| 106        | Rohit        | 76          |
| 107        | Sneha        | 92          |
| 108        | Neha         | 80          |
+------------+--------------+-------------+
```

---

# Alias Without AS

The AS keyword is optional.

## Example

```sql
SELECT name Student_Name
FROM students;
```

OR

```sql
SELECT marks Total_Marks
FROM students;
```

Both queries work correctly.

---

# Alias with Calculations

## Example

Add 5 bonus marks and display with a custom heading.

```sql
SELECT
name,
marks + 5 AS Bonus_Marks
FROM students;
```

### Output

```text
+--------+-------------+
| name   | Bonus_Marks |
+--------+-------------+
| Rahul  | 90          |
| Navin  | 95          |
| Dikshi | 100         |
| Amit   | 75          |
| Priya  | 93          |
| Rohit  | 81          |
| Sneha  | 97          |
| Neha   | 85          |
+--------+-------------+
```

---

# Alias with Aggregate Functions

## AVG()

```sql
SELECT AVG(marks) AS Average_Marks
FROM students;
```

### Output

```text
+---------------+
| Average_Marks |
+---------------+
| 84.50         |
+---------------+
```

---

## COUNT()

```sql
SELECT COUNT(*) AS Total_Students
FROM students;
```

### Output

```text
+----------------+
| Total_Students |
+----------------+
| 8              |
+----------------+
```

---

## MAX()

```sql
SELECT MAX(marks) AS Highest_Marks
FROM students;
```

### Output

```text
+---------------+
| Highest_Marks |
+---------------+
| 95            |
+---------------+
```

---

## MIN()

```sql
SELECT MIN(marks) AS Lowest_Marks
FROM students;
```

### Output

```text
+--------------+
| Lowest_Marks |
+--------------+
| 70           |
+--------------+
```

---

## SUM()

```sql
SELECT SUM(marks) AS Total_Marks
FROM students;
```

### Output

```text
+-------------+
| Total_Marks |
+-------------+
| 676         |
+-------------+
```

---

# Table Alias

Table aliases are mainly used to reduce typing and improve readability.

### Syntax

```sql
SELECT *
FROM table_name AS alias_name;
```

---

## Example

```sql
SELECT s.name, s.marks
FROM students AS s;
```

### Output

```text
+--------+-------+
| name   | marks |
+--------+-------+
| Rahul  | 85    |
| Navin  | 90    |
| Dikshi | 95    |
| Amit   | 70    |
| Priya  | 88    |
| Rohit  | 76    |
| Sneha  | 92    |
| Neha   | 80    |
+--------+-------+
```

---

# Real-World Examples

## Example 1

```sql
SELECT
name AS Student_Name,
city AS Student_City
FROM students;
```

---

## Example 2

```sql
SELECT
course AS Course_Name,
marks AS Student_Marks
FROM students;
```

---

## Example 3

```sql
SELECT
age AS Student_Age
FROM students;
```

---

# Important Notes

- Alias is temporary.
- Alias does not change actual column names.
- AS keyword is optional.
- Alias improves readability.
- Widely used in reports and JOIN queries.
- Useful with aggregate functions.

---

# Common Errors

## Error 1: Using Alias in WHERE Clause

### Wrong

```sql
SELECT marks AS Total_Marks
FROM students
WHERE Total_Marks > 80;
```

### Error Reason

WHERE executes before SELECT, so the alias is not recognized.

### Correct

```sql
SELECT marks AS Total_Marks
FROM students
WHERE marks > 80;
```

---

## Error 2: Unknown Column

### Wrong

```sql
SELECT namm AS Student_Name
FROM students;
```

### Error

```text
ERROR 1054 (42S22): Unknown column 'namm'
```

### Correct

```sql
SELECT name AS Student_Name
FROM students;
```

---

# Interview Questions

## What is Alias in SQL?

Alias is a temporary name assigned to a column or table.

---

## Which keyword is used for Alias?

```sql
AS
```

---

## Is AS mandatory?

No. It is optional.

---

## Does Alias permanently rename a column?

No. It only changes the display name in the query result.

---

## Why do we use Alias?

To improve readability and make query output easier to understand.

---

# Commands Practiced

```sql
SELECT name AS Student_Name
FROM students;

SELECT marks AS Total_Marks
FROM students;

SELECT AVG(marks) AS Average_Marks
FROM students;

SELECT COUNT(*) AS Total_Students
FROM students;

SELECT MAX(marks) AS Highest_Marks
FROM students;

SELECT MIN(marks) AS Lowest_Marks
FROM students;

SELECT SUM(marks) AS Total_Marks
FROM students;

SELECT s.name, s.marks
FROM students AS s;
```

---

# Summary

- ALIAS provides a temporary name for columns and tables.
- AS keyword can be used to define aliases.
- AS is optional in SQL.
- Alias improves readability of query results.
- Commonly used with aggregate functions and JOIN operations.
- Alias does not modify the original table structure.
