# Day 9: CONCAT() Function in SQL

## Introduction

The `CONCAT()` function is a **string function** used to join two or more strings into a single string.

It is commonly used to:
- Combine first name and last name
- Join text with columns
- Create custom messages
- Format output

If any argument is `NULL`, MySQL returns `NULL`.

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

### Output

```text
+-----+--------+-----+--------+--------+-------+
| id  | name   | age | city   | course | marks |
+-----+--------+-----+--------+--------+-------+
|101  | Rahul  | 21  | Pune   | BCA    | 85    |
|102  | Navin  | 22  | Pune   | BCA    | 90    |
|103  | Dikshi | 21  | Mumbai | BTech  | 95    |
|104  | Amit   | 23  | Delhi  | BCA    | 70    |
|105  | Priya  | 22  | Mumbai | BCom   | 88    |
|106  | Rohit  | 20  | Pune   | BTech  | 76    |
|107  | Sneha  | 21  | Delhi  | BCA    | 92    |
|108  | Neha   | 22  | Mumbai | BCom   | 80    |
+-----+--------+-----+--------+--------+-------+
```

---

# Syntax

```sql
CONCAT(string1, string2, string3, ...)
```

or

```sql
SELECT CONCAT(column1, column2)
FROM table_name;
```

---

# Example 1

## Query

```sql
SELECT name,
CONCAT(name,' - ',city) AS Student_Details
FROM students;
```

### Output

```text
+--------+-----------------+
| name   | Student_Details |
+--------+-----------------+
| Rahul  | Rahul - Pune    |
| Navin  | Navin - Pune    |
| Dikshi | Dikshi - Mumbai |
| Amit   | Amit - Delhi    |
| Priya  | Priya - Mumbai  |
| Rohit  | Rohit - Pune    |
| Sneha  | Sneha - Delhi   |
| Neha   | Neha - Mumbai   |
+--------+-----------------+
```

### Explanation

`CONCAT()` joins the student's name, separator (`-`), and city into one string.

---

# Example 2

## Query

```sql
SELECT
CONCAT(name,' studies ',course) AS Information
FROM students;
```

### Output

```text
+-----------------------+
| Information           |
+-----------------------+
| Rahul studies BCA     |
| Navin studies BCA     |
| Dikshi studies BTech  |
| Amit studies BCA      |
| Priya studies BCom    |
| Rohit studies BTech   |
| Sneha studies BCA     |
| Neha studies BCom     |
+-----------------------+
```

### Explanation

The function combines text with column values to create readable sentences.

---

# Example 3

## Query

```sql
SELECT
CONCAT(
'Student ',
name,
' scored ',
marks,
' marks.'
) AS Result
FROM students;
```

### Output

```text
+--------------------------------+
| Result                         |
+--------------------------------+
| Student Rahul scored 85 marks. |
| Student Navin scored 90 marks. |
| Student Dikshi scored 95 marks.|
| Student Amit scored 70 marks.  |
| Student Priya scored 88 marks. |
| Student Rohit scored 76 marks. |
| Student Sneha scored 92 marks. |
| Student Neha scored 80 marks.  |
+--------------------------------+
```

### Explanation

`CONCAT()` automatically converts numbers into strings while joining them.

---

# Example 4

## Query

```sql
SELECT
CONCAT(name,' (',course,')') AS Student
FROM students;
```

### Output

```text
+----------------+
| Student        |
+----------------+
| Rahul (BCA)    |
| Navin (BCA)    |
| Dikshi (BTech) |
| Amit (BCA)     |
| Priya (BCom)   |
| Rohit (BTech)  |
| Sneha (BCA)    |
| Neha (BCom)    |
+----------------+
```

### Explanation

Parentheses and spaces can also be added while joining strings.

---

# Example 5 (NULL Example)

## Query

```sql
SELECT CONCAT('Hello ', NULL);
```

### Output

```text
NULL
```

### Explanation

If any argument passed to `CONCAT()` is `NULL`, the entire result becomes `NULL`.

---

# Important Notes

- `CONCAT()` joins multiple strings.
- It accepts both text and numeric values.
- Numbers are automatically converted into strings.
- You can use column names and text together.
- `NULL` in any argument returns `NULL`.
- Spaces are **not added automatically**; include them manually.

---

# Common Errors

## Error 1

### Wrong

```sql
SELECT CONCAT(name city)
FROM students;
```

### Correct

```sql
SELECT CONCAT(name,' ',city)
FROM students;
```

### Reason

Arguments inside `CONCAT()` must be separated by commas.

---

## Error 2

### Wrong

```sql
SELECT CONCAT(name, city
FROM students;
```

### Correct

```sql
SELECT CONCAT(name, city)
FROM students;
```

### Reason

Missing closing parenthesis causes a syntax error.

---

## Error 3

### Wrong

```sql
SELECT CONCAT(name,'-',NULL);
```

### Output

```text
NULL
```

### Correct

```sql
SELECT CONCAT(name,'-',IFNULL(NULL,'Unknown'));
```

### Output

```text
Rahul-Unknown
```

### Reason

`NULL` causes `CONCAT()` to return `NULL`. Use `IFNULL()` or `COALESCE()` to handle NULL values.

---

# Interview Questions

## Q1. What is the purpose of the CONCAT() function?

### Answer

It joins two or more strings into one single string.

---

## Q2. Can CONCAT() join numbers?

### Answer

Yes. MySQL automatically converts numeric values into strings.

Example:

```sql
SELECT CONCAT('Marks = ',95);
```

Output:

```text
Marks = 95
```

---

## Q3. What happens if one argument is NULL?

### Answer

The entire result becomes `NULL`.

Example:

```sql
SELECT CONCAT('Hello',NULL);
```

Output

```text
NULL
```

---

## Q4. Can CONCAT() use both text and column values?

### Answer

Yes.

Example:

```sql
SELECT CONCAT(name,' from ',city)
FROM students;
```

---

# Commands Covered

```sql
CONCAT()

SELECT

AS

IFNULL()

COALESCE()
```

---

# SQL Query Execution Order

```text
1. FROM
2. SELECT
3. CONCAT() Function Executes
4. AS Alias Applied
5. Result Displayed
```

---

# Summary

- `CONCAT()` combines multiple strings into one.
- Supports text, numbers, and column values.
- Spaces must be added manually.
- `NULL` makes the result `NULL`.
- Frequently used for formatting reports and displaying readable output.
- Often combined with aliases using `AS`.
- Commonly used in real-world SQL queries for generating custom output.
