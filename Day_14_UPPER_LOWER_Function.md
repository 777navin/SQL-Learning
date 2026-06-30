# Day 14: UPPER() and LOWER() Functions

## Introduction

The **UPPER()** and **LOWER()** functions are MySQL string functions used to change the case of text.

- **UPPER()** converts all characters in a string to uppercase.
- **LOWER()** converts all characters in a string to lowercase.

These functions are commonly used for formatting text, performing case-insensitive comparisons, and displaying consistent output.

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

# Syntax

## UPPER()

```sql
SELECT UPPER(column_name)
FROM table_name;
```

## LOWER()

```sql
SELECT LOWER(column_name)
FROM table_name;
```

---

# Example 1

## Query

```sql
SELECT name,
UPPER(name) AS Upper_Name
FROM students;
```

## Output

```text
+--------+------------+
| name   | Upper_Name |
+--------+------------+
| Rahul  | RAHUL      |
| Navin  | NAVIN      |
| Dikshi | DIKSHI     |
| Amit   | AMIT       |
| Priya  | PRIYA      |
| Rohit  | ROHIT      |
| Sneha  | SNEHA      |
| Neha   | NEHA       |
+--------+------------+
```

## Explanation

The **UPPER()** function converts every character of the name into uppercase letters.

---

# Example 2

## Query

```sql
SELECT city,
LOWER(city) AS Lower_City
FROM students;
```

## Output

```text
+---------+------------+
| city    | Lower_City |
+---------+------------+
| Pune    | pune       |
| Pune    | pune       |
| Mumbai  | mumbai     |
| Delhi   | delhi      |
| Mumbai  | mumbai     |
| Pune    | pune       |
| Delhi   | delhi      |
| Mumbai  | mumbai     |
+---------+------------+
```

## Explanation

The **LOWER()** function converts all characters into lowercase.

---

# Example 3

## Query

```sql
SELECT
UPPER(course) AS Upper_Course,
LOWER(course) AS Lower_Course
FROM students;
```

## Output

```text
+--------------+--------------+
| Upper_Course | Lower_Course |
+--------------+--------------+
| BCA          | bca          |
| BCA          | bca          |
| BTECH        | btech        |
| BCA          | bca          |
| BCOM         | bcom         |
| BTECH        | btech        |
| BCA          | bca          |
| BCOM         | bcom         |
+--------------+--------------+
```

## Explanation

You can use both **UPPER()** and **LOWER()** together to display the same data in different letter cases.

---

# Important Notes

- **UPPER()** converts text to uppercase.
- **LOWER()** converts text to lowercase.
- Numbers and special characters remain unchanged.
- These functions do not modify the original table data.
- They are commonly used for formatting reports and case-insensitive searching.

---

# Common Errors

## Error 1

### Wrong

```sql
SELECT UPPER(name, city)
FROM students;
```

### Correct

```sql
SELECT UPPER(name),
UPPER(city)
FROM students;
```

### Reason

`UPPER()` accepts only **one expression** at a time.

---

## Error 2

### Wrong

```sql
SELECT UPPER
FROM students;
```

### Correct

```sql
SELECT UPPER(name)
FROM students;
```

### Reason

The function must include parentheses and a valid column or string.

---

# Interview Questions

## Q1. What is the difference between UPPER() and LOWER()?

### Answer

- **UPPER()** converts text into uppercase.
- **LOWER()** converts text into lowercase.

---

## Q2. Do UPPER() and LOWER() permanently change the data in the table?

### Answer

No.

They only change the displayed result. The original data stored in the table remains unchanged.

---

## Q3. Why are UPPER() and LOWER() useful?

### Answer

They are useful for:

- Formatting output
- Standardizing text
- Case-insensitive comparisons
- Searching regardless of letter case

---

# Commands Covered

```sql
UPPER()

LOWER()

SELECT
```

---

# SQL Query Execution Order (If Applicable)

```text
1. FROM
2. SELECT
3. UPPER() / LOWER() Function
4. Display Result
```

---

# Summary

- UPPER() converts text into uppercase.
- LOWER() converts text into lowercase.
- Original table data is not modified.
- These functions improve text formatting and readability.
- Frequently used for case-insensitive searches and reports.
