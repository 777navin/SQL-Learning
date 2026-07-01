# Day 18: DISTINCT Keyword

## Introduction

The `DISTINCT` keyword is used to remove duplicate values from the result set. It returns only unique records from one or more selected columns. If duplicate values exist, `DISTINCT` displays only one occurrence of each unique value.

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

## View Data

```sql
SELECT * FROM students;
```

### Output

```text
+-----+--------+-----+---------+--------+-------+
| id  | name   | age | city    | course | marks |
+-----+--------+-----+---------+--------+-------+
| 101 | Rahul  | 21  | Pune    | BCA    | 85    |
| 102 | Navin  | 22  | Pune    | BCA    | 90    |
| 103 | Dikshi | 21  | Mumbai  | BTech  | 95    |
| 104 | Amit   | 23  | Delhi   | BCA    | 70    |
| 105 | Priya  | 22  | Mumbai  | BCom   | 88    |
| 106 | Rohit  | 20  | Pune    | BTech  | 76    |
| 107 | Sneha  | 21  | Delhi   | BCA    | 92    |
| 108 | Neha   | 22  | Mumbai  | BCom   | 80    |
+-----+--------+-----+---------+--------+-------+
```

---

## Syntax

```sql
SELECT DISTINCT column_name
FROM table_name;
```

For multiple columns:

```sql
SELECT DISTINCT column1, column2
FROM table_name;
```

---

## Example 1

### Query

```sql
SELECT DISTINCT city
FROM students;
```

### Output

```text
+---------+
| city    |
+---------+
| Pune    |
| Mumbai  |
| Delhi   |
+---------+
```

### Explanation

Although multiple students belong to the same city, `DISTINCT` returns each city only once.

---

## Example 2

### Query

```sql
SELECT DISTINCT course
FROM students;
```

### Output

```text
+--------+
| course |
+--------+
| BCA    |
| BTech  |
| BCom   |
+--------+
```

### Explanation

Duplicate course names are removed, showing only unique courses.

---

## Example 3

### Query

```sql
SELECT DISTINCT city, course
FROM students;
```

### Output

```text
+---------+--------+
| city    | course |
+---------+--------+
| Pune    | BCA    |
| Mumbai  | BTech  |
| Delhi   | BCA    |
| Mumbai  | BCom   |
| Pune    | BTech  |
+---------+--------+
```

### Explanation

`DISTINCT` checks the complete combination of `city` and `course`. Only duplicate combinations are removed.

---

## Important Notes

- `DISTINCT` removes duplicate rows from the result.
- It works with one or multiple columns.
- `DISTINCT` does not modify the actual table data.
- `NULL` values are treated as one unique value.
- It is always written immediately after the `SELECT` keyword.

---

## Common Errors

### Error 1

#### Wrong

```sql
SELECT city DISTINCT
FROM students;
```

#### Correct

```sql
SELECT DISTINCT city
FROM students;
```

#### Reason

`DISTINCT` must come immediately after `SELECT`.

---

### Error 2

#### Wrong

```sql
SELECT DISTINCT(city), course
FROM students;
```

#### Correct

```sql
SELECT DISTINCT city, course
FROM students;
```

#### Reason

`DISTINCT` applies to the entire selected column list, not just one column.

---

## Interview Questions

### Q1. What is the purpose of the `DISTINCT` keyword?

#### Answer

`DISTINCT` removes duplicate rows from the query result and returns only unique values.

---

### Q2. Can `DISTINCT` be used with multiple columns?

#### Answer

Yes. It returns unique combinations of all selected columns.

Example:

```sql
SELECT DISTINCT city, course
FROM students;
```

---

### Q3. Does `DISTINCT` remove duplicate records from the table?

#### Answer

No. It only removes duplicate values in the query result. The original table data remains unchanged.

---

## Commands Covered

```sql
SELECT DISTINCT city
FROM students;

SELECT DISTINCT course
FROM students;

SELECT DISTINCT city, course
FROM students;
```

---

## SQL Query Execution Order (If Applicable)

```text
1. FROM
2. SELECT
3. DISTINCT
4. Display Result
```

---

## Summary

- `DISTINCT` returns only unique values.
- Duplicate rows are removed from the output.
- Works with single or multiple columns.
- Does not change the original table.
- Useful for finding unique cities, courses, departments, categories, etc.
