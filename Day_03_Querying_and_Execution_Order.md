# Day 3: SELECT Statement & Data Retrieval

## Introduction

The SELECT statement is the most commonly used SQL command. It is used to retrieve data from one or more tables.

Using SELECT, we can:

- Retrieve all records
- Retrieve specific columns
- Filter records
- Sort data
- Limit results
- Remove duplicates
- Search patterns
- Use aggregate functions
- Group records
- Filter grouped results

For all examples below, we will use the `student_db.students` table.

---

## Database Setup Used

### Create Database

```sql
CREATE DATABASE student_db;
```

### Use Database

```sql
USE student_db;
```

### Create Table

```sql
CREATE TABLE students(
    id INT PRIMARY KEY,
    name VARCHAR(50),
    age INT,
    city VARCHAR(50),
    course VARCHAR(50),
    marks INT
);
```

### Insert Data

```sql
INSERT INTO students(id,name,age,city,course,marks)
VALUES
(101,'Rahul',21,'Pune','BCA',85),
(102,'Navin',22,'Pune','BCA',90),
(103,'Dikshi',21,'Mumbai','BTech',95),
(104,'Amit',23,'Delhi','BCA',70),
(105,'Priya',22,'Mumbai','BCom',88),
(106,'Rohit',20,'Pune','BTech',76),
(107,'Sneha',21,'Delhi','BCA',92),
(108,'Neha',22,'Mumbai','BCom',80);
```

---

## View Complete Data

```sql
SELECT * FROM students;
```

### Output

```text
+-----+--------+------+--------+--------+-------+
| id  | name   | age  | city   | course | marks |
+-----+--------+------+--------+--------+-------+
| 101 | Rahul  | 21   | Pune   | BCA    | 85    |
| 102 | Navin  | 22   | Pune   | BCA    | 90    |
| 103 | Dikshi | 21   | Mumbai | BTech  | 95    |
| 104 | Amit   | 23   | Delhi  | BCA    | 70    |
| 105 | Priya  | 22   | Mumbai | BCom   | 88    |
| 106 | Rohit  | 20   | Pune   | BTech  | 76    |
| 107 | Sneha  | 21   | Delhi  | BCA    | 92    |
| 108 | Neha   | 22   | Mumbai | BCom   | 80    |
+-----+--------+------+--------+--------+-------+
```

---

# SELECT Statement

## Syntax

```sql
SELECT column_name
FROM table_name;
```

### Retrieve All Columns

```sql
SELECT *
FROM table_name;
```

---

# Select Specific Columns

## Query

```sql
SELECT id,name
FROM students;
```

## Output

```text
+-----+--------+
| id  | name   |
+-----+--------+
| 101 | Rahul  |
| 102 | Navin  |
| 103 | Dikshi |
| 104 | Amit   |
| 105 | Priya  |
| 106 | Rohit  |
| 107 | Sneha  |
| 108 | Neha   |
+-----+--------+
```

---

# Select All Columns

## Query

```sql
SELECT *
FROM students;
```

---

# WHERE Clause

Used to filter records.

## Students From Pune

```sql
SELECT *
FROM students
WHERE city='Pune';
```

### Output

```text
+-----+-------+------+-------+--------+-------+
| id  | name  | age  | city  | course | marks |
+-----+-------+------+-------+--------+-------+
| 101 | Rahul | 21   | Pune  | BCA    | 85    |
| 102 | Navin | 22   | Pune  | BCA    | 90    |
| 106 | Rohit | 20   | Pune  | BTech  | 76    |
+-----+-------+------+-------+--------+-------+
```

---

## Marks Greater Than 80

```sql
SELECT *
FROM students
WHERE marks > 80;
```

### Output

```text
101 Rahul
102 Navin
103 Dikshi
105 Priya
107 Sneha
```

---

# AND Operator

```sql
SELECT *
FROM students
WHERE city='Pune'
AND marks>80;
```

### Output

```text
Rahul
Navin
```

---

# OR Operator

```sql
SELECT *
FROM students
WHERE city='Pune'
OR city='Mumbai';
```

### Output

```text
Rahul
Navin
Dikshi
Priya
Rohit
Neha
```

---

# ORDER BY

Used to sort records.

## Ascending Order

```sql
SELECT *
FROM students
ORDER BY name ASC;
```

### Output

```text
Amit
Dikshi
Navin
Neha
Priya
Rahul
Rohit
Sneha
```

---

## Descending Order

```sql
SELECT *
FROM students
ORDER BY marks DESC;
```

### Output

```text
95
92
90
88
85
80
76
70
```

---

# LIMIT

Used to restrict number of rows.

## Query

```sql
SELECT *
FROM students
LIMIT 3;
```

### Output

```text
101 Rahul
102 Navin
103 Dikshi
```

---

# DISTINCT

Used to remove duplicate values.

## Query

```sql
SELECT DISTINCT city
FROM students;
```

### Output

```text
Pune
Mumbai
Delhi
```

---

# LIKE Operator

Used for pattern matching.

## Names Starting With N

```sql
SELECT *
FROM students
WHERE name LIKE 'N%';
```

### Output

```text
Navin
Neha
```

---

## Names Ending With a

```sql
SELECT *
FROM students
WHERE name LIKE '%a';
```

### Output

```text
Priya
Neha
Sneha
```

---

## Names Containing a

```sql
SELECT *
FROM students
WHERE name LIKE '%a%';
```

### Output

```text
Rahul
Navin
Amit
Priya
Sneha
Neha
```

---

# BETWEEN

Used to find values within a range.

## Query

```sql
SELECT *
FROM students
WHERE marks BETWEEN 80 AND 90;
```

### Output

```text
Rahul
Navin
Priya
Neha
```

---

# IN Operator

Used to match multiple values.

## Query

```sql
SELECT *
FROM students
WHERE city IN ('Pune','Mumbai');
```

### Output

```text
Rahul
Navin
Dikshi
Priya
Rohit
Neha
```

---

# Aggregate Functions

## COUNT

```sql
SELECT COUNT(*)
FROM students;
```

### Output

```text
8
```

---

## MAX

```sql
SELECT MAX(marks)
FROM students;
```

### Output

```text
95
```

---

## MIN

```sql
SELECT MIN(marks)
FROM students;
```

### Output

```text
70
```

---

## AVG

```sql
SELECT AVG(marks)
FROM students;
```

### Output

```text
84.50
```

---

## SUM

```sql
SELECT SUM(marks)
FROM students;
```

### Output

```text
676
```

---

# GROUP BY

Used to create groups.

## Count Students By City

```sql
SELECT city,COUNT(*)
FROM students
GROUP BY city;
```

### Output

```text
+--------+----------+
| city   | COUNT(*) |
+--------+----------+
| Pune   | 3        |
| Mumbai | 3        |
| Delhi  | 2        |
+--------+----------+
```

---

## Average Marks By Course

```sql
SELECT course,AVG(marks)
FROM students
GROUP BY course;
```

### Output

```text
+--------+------------+
| course | AVG(marks) |
+--------+------------+
| BCA    | 84.25      |
| BTech  | 85.50      |
| BCom   | 84.00      |
+--------+------------+
```

---

# HAVING

Used to filter grouped data.

## Query

```sql
SELECT city,COUNT(*)
FROM students
GROUP BY city
HAVING COUNT(*) > 1;
```

### Output

```text
Pune    3
Mumbai  3
Delhi   2
```

---

# SQL Query Execution Order

```text
1. FROM
2. WHERE
3. GROUP BY
4. HAVING
5. SELECT
6. ORDER BY
7. LIMIT
```

---

# Important Notes

- SELECT * returns all columns.
- WHERE filters rows.
- ORDER BY sorts records.
- LIMIT restricts output rows.
- DISTINCT removes duplicates.
- GROUP BY creates groups.
- HAVING filters groups.
- LIKE performs pattern matching.
- Aggregate functions return summarized results.

---

# Common Errors

## Missing FROM Clause

```sql
SELECT id,name;
```

### Error

```text
No table specified.
```

### Correct

```sql
SELECT id,name
FROM students;
```

---

## HAVING Without GROUP BY

```sql
SELECT city
FROM students
HAVING COUNT(*) > 1;
```

### Correct

```sql
SELECT city,COUNT(*)
FROM students
GROUP BY city
HAVING COUNT(*) > 1;
```

---

## Missing Quotes

```sql
SELECT *
FROM students
WHERE city=Pune;
```

### Correct

```sql
SELECT *
FROM students
WHERE city='Pune';
```

---

# Interview Questions

## Q1. Difference Between WHERE and HAVING?

### Answer

- WHERE filters rows before grouping.
- HAVING filters groups after GROUP BY.

---

## Q2. Difference Between DISTINCT and GROUP BY?

### Answer

- DISTINCT removes duplicates.
- GROUP BY creates groups for aggregate calculations.

---

## Q3. Purpose of ORDER BY?

### Answer

ORDER BY sorts the result set in ascending (ASC) or descending (DESC) order.

---

## Q4. Difference Between COUNT(*) and COUNT(column_name)?

### Answer

COUNT(*) counts all rows.

COUNT(column_name) counts only non-NULL values.

---

# Summary

In this chapter, we learned:

- SELECT
- WHERE
- AND
- OR
- ORDER BY
- LIMIT
- DISTINCT
- LIKE
- BETWEEN
- IN
- COUNT
- MAX
- MIN
- AVG
- SUM
- GROUP BY
- HAVING

These commands form the foundation of SQL data retrieval and are heavily used in interviews, projects, and real-world database applications.
