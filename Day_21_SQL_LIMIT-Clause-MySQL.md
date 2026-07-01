# Day 21: SQL LIMIT Clause (MySQL)

## Introduction

The **LIMIT** clause is used to **restrict the number of rows returned** by a SQL query.

Instead of displaying the entire table, `LIMIT` allows you to fetch only the required number of records. It is commonly used for **pagination, previews, dashboards, testing queries, and improving performance** when working with large datasets.

> **Think of LIMIT as saying:**  
> "Show me only the first few rows."

---

# Database Setup Used

## Create Database

```sql
CREATE DATABASE student_db;
```

## Use Database

```sql
USE student_db;
```

## Create Table

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

## Insert Data

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

# View Data

```sql
SELECT * FROM students;
```

## Output

| id | name | age | city | course | marks |
|----|------|-----|--------|---------|------|
|101|Rahul|21|Pune|BCA|85|
|102|Navin|22|Pune|BCA|90|
|103|Dikshi|21|Mumbai|BTech|95|
|104|Amit|23|Delhi|BCA|70|
|105|Priya|22|Mumbai|BCom|88|
|106|Rohit|20|Pune|BTech|76|
|107|Sneha|21|Delhi|BCA|92|
|108|Neha|22|Mumbai|BCom|80|

---

# Why Do We Use LIMIT?

Imagine a table containing **10 lakh (1 million)** records.

If you execute:

```sql
SELECT * FROM students;
```

MySQL tries to return every record.

Sometimes you only want:

- First 5 students
- Top 10 records
- First page of data
- Preview of a table

Instead of loading everything, use **LIMIT**.

---

# Syntax

## Return first N rows

```sql
SELECT column_name
FROM table_name
LIMIT number;
```

---

## Return rows after skipping some records

```sql
SELECT column_name
FROM table_name
LIMIT offset, count;
```

OR

```sql
SELECT column_name
FROM table_name
LIMIT count OFFSET offset;
```

---

# Example 1 — Display First 3 Students

## Query

```sql
SELECT *
FROM students
LIMIT 3;
```

## Output

| id | name | marks |
|----|------|------|
|101|Rahul|85|
|102|Navin|90|
|103|Dikshi|95|

## Explanation

`LIMIT 3` tells MySQL to return only the **first three rows**.

---

# Example 2 — Display First 5 Student Names

## Query

```sql
SELECT name
FROM students
LIMIT 5;
```

## Output

| name |
|------|
|Rahul|
|Navin|
|Dikshi|
|Amit|
|Priya|

## Explanation

Only the **name** column is selected, and only **5 records** are returned.

---

# Example 3 — Highest 3 Marks

## Query

```sql
SELECT *
FROM students
ORDER BY marks DESC
LIMIT 3;
```

## Output

| name | marks |
|------|------|
|Dikshi|95|
|Sneha|92|
|Navin|90|

## Explanation

Steps performed:

1. Sort records by marks (Highest → Lowest)
2. Return only the first three rows

This is the most common use of `LIMIT`.

---

# Example 4 — Lowest 2 Marks

## Query

```sql
SELECT *
FROM students
ORDER BY marks ASC
LIMIT 2;
```

## Output

| name | marks |
|------|------|
|Amit|70|
|Rohit|76|

## Explanation

Records are sorted from lowest marks to highest, then only the first two are displayed.

---

# Example 5 — Skip First 2 Records

## Query

```sql
SELECT *
FROM students
LIMIT 2,3;
```

## Output

| id | name |
|----|------|
|103|Dikshi|
|104|Amit|
|105|Priya|

## Explanation

```
LIMIT 2,3
```

means

- Skip first **2 rows**
- Return next **3 rows**

---

# Example 6 — Pagination

## Page 1

```sql
SELECT *
FROM students
LIMIT 0,3;
```

Output

```
101
102
103
```

---

## Page 2

```sql
SELECT *
FROM students
LIMIT 3,3;
```

Output

```
104
105
106
```

---

## Page 3

```sql
SELECT *
FROM students
LIMIT 6,3;
```

Output

```
107
108
```

## Explanation

Pagination works by changing the **offset**.

Formula:

```
Offset = (Page Number - 1) × Records Per Page
```

---

# LIMIT with WHERE

## Query

```sql
SELECT *
FROM students
WHERE city='Pune'
LIMIT 2;
```

## Output

| id | name |
|----|------|
|101|Rahul|
|102|Navin|

## Explanation

1. WHERE filters Pune students.
2. LIMIT returns only the first two matching rows.

---

# LIMIT with ORDER BY

```sql
SELECT *
FROM students
ORDER BY age DESC
LIMIT 4;
```

This first sorts by age and then returns the top four oldest students.

---

# LIMIT with DISTINCT

```sql
SELECT DISTINCT city
FROM students
LIMIT 2;
```

Example Output

```
Pune
Mumbai
```

---

# Important Notes

- LIMIT is supported in MySQL.
- LIMIT always returns records from the beginning unless an offset is specified.
- Usually used together with ORDER BY.
- Helps improve query performance.
- Frequently used in web applications.
- Essential for pagination.
- LIMIT does not permanently remove any data.
- Without ORDER BY, the returned rows may not always appear in the same order.

---

# Common Errors

## Error 1

### Wrong

```sql
LIMIT;
```

### Correct

```sql
LIMIT 5;
```

### Reason

LIMIT always requires a numeric value.

---

## Error 2

### Wrong

```sql
SELECT *
LIMIT 3
FROM students;
```

### Correct

```sql
SELECT *
FROM students
LIMIT 3;
```

### Reason

LIMIT is written **after FROM, WHERE, GROUP BY, HAVING, and ORDER BY**.

---

## Error 3

### Wrong

```sql
SELECT *
FROM students
LIMIT -2;
```

### Correct

```sql
SELECT *
FROM students
LIMIT 2;
```

### Reason

Negative values are not valid for LIMIT.

---

# Real-World Uses

- Display latest blog posts
- Show Top 10 products
- Fetch newest orders
- Dashboard widgets
- Pagination (Page 1, Page 2, ...)
- Preview first few records
- API responses
- Performance optimization

---

# Interview Questions

## Q1. What is the purpose of LIMIT in MySQL?

### Answer

LIMIT restricts the number of rows returned by a SELECT query.

---

## Q2. What is the difference between LIMIT and ORDER BY?

### Answer

- ORDER BY sorts the data.
- LIMIT restricts the number of rows returned.

They are commonly used together.

---

## Q3. What does LIMIT 5,10 mean?

### Answer

Skip the first **5** rows and return the next **10** rows.

---

## Q4. Can LIMIT be used without ORDER BY?

### Answer

Yes.

However, the returned rows may not always be in a predictable order because no sorting is applied.

---

## Q5. Which clause executes first: ORDER BY or LIMIT?

### Answer

MySQL first sorts the data using **ORDER BY**, then applies **LIMIT** to return the requested number of rows.

---

# Commands Covered

```sql
SELECT
FROM
WHERE
ORDER BY
DISTINCT
LIMIT
LIMIT offset,count
LIMIT ... OFFSET ...
```

---

# SQL Query Execution Order

```text
1. FROM
2. WHERE
3. GROUP BY
4. HAVING
5. SELECT
6. DISTINCT
7. ORDER BY
8. LIMIT
```

---

# Quick Revision

| Query | Meaning |
|--------|---------|
|LIMIT 5|First 5 rows|
|LIMIT 10|First 10 rows|
|LIMIT 2,4|Skip 2 rows, return next 4|
|LIMIT 4 OFFSET 2|Same as LIMIT 2,4|
|ORDER BY marks DESC LIMIT 3|Top 3 highest marks|
|ORDER BY marks ASC LIMIT 5|Lowest 5 marks|

---

# Summary

- LIMIT restricts the number of rows returned.
- Used for previews, dashboards, APIs, and pagination.
- Can be combined with WHERE, ORDER BY, and DISTINCT.
- OFFSET allows skipping records before fetching rows.
- ORDER BY should usually be used with LIMIT for predictable results.
- LIMIT improves performance when working with large datasets.
- One of the most frequently used clauses in MySQL.
