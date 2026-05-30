# Day 2: Database Creation and Data Insertion

## Introduction

Before storing data in SQL, we must:

1. Create a Database
2. Select the Database
3. Create Tables
4. Insert Records into Tables

These are the foundation steps of every SQL project.

---

## Commands Covered

- CREATE DATABASE
- SHOW DATABASES
- USE
- CREATE TABLE
- DESC
- INSERT INTO
- SELECT

---

## 1. Create Database

### Syntax

```sql
CREATE DATABASE database_name;
```

### Example

```sql
CREATE DATABASE student_db;
```

### Verify Database

```sql
SHOW DATABASES;
```

### Output

```text
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| student_db         |
| sys                |
+--------------------+
```

---

## 2. Select Database

### Syntax

```sql
USE database_name;
```

### Example

```sql
USE student_db;
```

### Output

```text
Database changed
```

---

## 3. Create Table

### Syntax

```sql
CREATE TABLE table_name(
    column1 datatype,
    column2 datatype,
    ...
);
```

### Example

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

### Verify Table

```sql
SHOW TABLES;
```

### Output

```text
+----------------------+
| Tables_in_student_db |
+----------------------+
| students             |
+----------------------+
```

---

## 4. View Table Structure

### Syntax

```sql
DESC table_name;
```

### Example

```sql
DESC students;
```

### Output

```text
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| id     | int         | NO   | PRI | NULL    |       |
| name   | varchar(50) | YES  |     | NULL    |       |
| age    | int         | YES  |     | NULL    |       |
| city   | varchar(50) | YES  |     | NULL    |       |
| course | varchar(50) | YES  |     | NULL    |       |
| marks  | int         | YES  |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
```

---

# Data Insertion

## 1. Insert Single Record

### Syntax

```sql
INSERT INTO table_name(column1,column2,...)
VALUES(value1,value2,...);
```

### Example

```sql
INSERT INTO students(id,name,age,city,course,marks)
VALUES(101,'Rahul',21,'Pune','BCA',85);
```

### Verify

```sql
SELECT * FROM students;
```

---

## 2. Insert Multiple Records

### Syntax

```sql
INSERT INTO table_name(column1,column2,...)
VALUES
(value1,value2,...),
(value1,value2,...),
(value1,value2,...);
```

### Example

```sql
INSERT INTO students(id,name,age,city,course,marks)
VALUES
(102,'Navin',22,'Pune','BCA',90),
(103,'Dikshi',21,'Mumbai','BTech',95),
(104,'Amit',23,'Delhi','BCA',70),
(105,'Priya',22,'Mumbai','BCom',88),
(106,'Rohit',20,'Pune','BTech',76),
(107,'Sneha',21,'Delhi','BCA',92),
(108,'Neha',22,'Mumbai','BCom',80);
```

---

## Complete Dataset

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

### Syntax

```sql
SELECT * FROM table_name;
```

### Example

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

## Important Notes

- Database names must be unique.
- Always select a database using `USE database_name;`.
- Table names must be unique within a database.
- String values must be enclosed in single quotes.
- Multiple records can be inserted using one INSERT statement.
- PRIMARY KEY values cannot be duplicated.

---

## Common Errors

### Unknown Database

```sql
USE students_db;
```

Error:

```text
ERROR 1049 (42000): Unknown database 'students_db'
```

Reason:
Database does not exist.

Correct:

```sql
USE student_db;
```

---

### Table Doesn't Exist

```sql
SELECT * FROM studnets;
```

Error:

```text
ERROR 1146 (42S02)
```

Reason:
Table name is misspelled.

Correct:

```sql
SELECT * FROM students;
```

---

### SQL Syntax Error

```sql
use_studnet_db;
```

Error:

```text
ERROR 1064 (42000)
```

Reason:
Invalid SQL syntax.

Correct:

```sql
USE student_db;
```

---

## Interview Questions

### What is a database?

A database is an organized collection of data stored electronically.

### Which command creates a database?

```sql
CREATE DATABASE database_name;
```

### Which command selects a database?

```sql
USE database_name;
```

### Which command creates a table?

```sql
CREATE TABLE table_name(...);
```

### Which command inserts data?

```sql
INSERT INTO table_name VALUES(...);
```

### Which command displays all records?

```sql
SELECT * FROM table_name;
```

---

## Summary

- Created a database using CREATE DATABASE.
- Selected a database using USE.
- Created a table using CREATE TABLE.
- Viewed structure using DESC.
- Inserted single and multiple records using INSERT INTO.
- Displayed data using SELECT.
- Learned common beginner mistakes and their solutions.
