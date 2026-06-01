# Day 6: PRIMARY KEY Constraint in SQL

## Introduction

A **PRIMARY KEY** is a constraint used to uniquely identify each record (row) in a table.

A column defined as a PRIMARY KEY:

- Cannot contain NULL values.
- Must contain unique values.
- There can be only ONE PRIMARY KEY in a table.
- A PRIMARY KEY can consist of one or multiple columns (Composite Primary Key).

Think of it as the **unique identity** of each row.

Example:

| id | name |
|----|------|
| 101 | Rahul |
| 102 | Navin |
| 103 | Dikshi |

Here, `id` is a good PRIMARY KEY because every value is unique.

---

## Why Do We Need a PRIMARY KEY?

Without a PRIMARY KEY:

- Duplicate records can occur.
- Identifying a specific row becomes difficult.
- Relationships between tables become unreliable.

PRIMARY KEY ensures:

- Data integrity
- Uniqueness
- Faster searching and indexing

---

## Syntax

### Create Table with PRIMARY KEY

```sql
CREATE TABLE students (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    city VARCHAR(50)
);
```

---

### PRIMARY KEY Using Constraint Name

```sql
CREATE TABLE students (
    id INT,
    name VARCHAR(50),
    city VARCHAR(50),
    CONSTRAINT pk_student PRIMARY KEY(id)
);
```

---

## Example

### Create Table

```sql
CREATE TABLE students (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    city VARCHAR(50)
);
```

Insert Records

```sql
INSERT INTO students
VALUES
(101,'Rahul','Pune'),
(102,'Navin','Pune'),
(103,'Dikshi','Mumbai');
```

View Data

```sql
SELECT * FROM students;
```

---

## Output

```text
+-----+--------+--------+
| id  | name   | city   |
+-----+--------+--------+
| 101 | Rahul  | Pune   |
| 102 | Navin  | Pune   |
| 103 | Dikshi | Mumbai |
+-----+--------+--------+
```

---

# PRIMARY KEY Violation Examples

## 1. Duplicate Value

```sql
INSERT INTO students
VALUES (101,'Kajal','Delhi');
```

### Error

```text
ERROR 1062 (23000):
Duplicate entry '101' for key 'students.PRIMARY'
```

Reason:

`101` already exists.

---

## 2. NULL Value

```sql
INSERT INTO students
VALUES (NULL,'Kajal','Delhi');
```

### Error

```text
ERROR 1048 (23000):
Column 'id' cannot be null
```

Reason:

PRIMARY KEY cannot contain NULL.

---

# Add PRIMARY KEY to Existing Table

Create Table

```sql
CREATE TABLE employees (
    emp_id INT,
    name VARCHAR(50)
);
```

Add PRIMARY KEY

```sql
ALTER TABLE employees
ADD PRIMARY KEY(emp_id);
```

---

# Drop PRIMARY KEY

```sql
ALTER TABLE employees
DROP PRIMARY KEY;
```

---

# Composite PRIMARY KEY

A PRIMARY KEY made using multiple columns.

### Create Table

```sql
CREATE TABLE student_courses (
    student_id INT,
    course_id INT,
    PRIMARY KEY(student_id, course_id)
);
```

---

## Example

```sql
INSERT INTO student_courses
VALUES
(101,1),
(101,2),
(102,1);
```

Valid because combination is unique.

---

### Invalid Example

```sql
INSERT INTO student_courses
VALUES (101,1);
```

### Error

```text
ERROR 1062 (23000):
Duplicate entry '101-1' for key 'PRIMARY'
```

---

# AUTO_INCREMENT with PRIMARY KEY

Most commonly used together.

```sql
CREATE TABLE students (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50)
);
```

Insert Data

```sql
INSERT INTO students(name)
VALUES
('Rahul'),
('Navin'),
('Dikshi');
```

Output

```text
+----+--------+
| id | name   |
+----+--------+
| 1  | Rahul  |
| 2  | Navin  |
| 3  | Dikshi |
+----+--------+
```

MySQL automatically generates unique IDs.

---

# Show Table Structure

```sql
DESC students;
```

OR

```sql
SHOW COLUMNS FROM students;
```

---

# Show CREATE TABLE

```sql
SHOW CREATE TABLE students;
```

Output will display the PRIMARY KEY definition.

---

# Commands Covered

## Create Table

```sql
CREATE TABLE students (
    id INT PRIMARY KEY,
    name VARCHAR(50)
);
```

---

## Add Primary Key

```sql
ALTER TABLE students
ADD PRIMARY KEY(id);
```

---

## Drop Primary Key

```sql
ALTER TABLE students
DROP PRIMARY KEY;
```

---

## Composite Primary Key

```sql
PRIMARY KEY(student_id, course_id)
```

---

## Auto Increment Primary Key

```sql
id INT AUTO_INCREMENT PRIMARY KEY
```

---

## View Structure

```sql
DESC students;
```

```sql
SHOW CREATE TABLE students;
```

---

# Important Notes

- PRIMARY KEY must be unique.
- PRIMARY KEY cannot contain NULL.
- Only one PRIMARY KEY is allowed per table.
- PRIMARY KEY automatically creates an index.
- PRIMARY KEY is commonly used with AUTO_INCREMENT.
- Composite PRIMARY KEY can use multiple columns.
- PRIMARY KEY is used to uniquely identify every row.

---

# Common Errors

## Error 1062

```text
Duplicate entry for key 'PRIMARY'
```

Cause:

Trying to insert a duplicate PRIMARY KEY value.

---

## Error 1048

```text
Column cannot be null
```

Cause:

Trying to insert NULL into PRIMARY KEY column.

---

## Error While Adding PRIMARY KEY

```sql
ALTER TABLE students
ADD PRIMARY KEY(id);
```

Error occurs if:

- Duplicate values already exist.
- NULL values already exist.

Fix duplicates/NULLs first, then add PRIMARY KEY.

---

# Interview Questions

### 1. What is a PRIMARY KEY?

A column or set of columns that uniquely identifies each row in a table.

---

### 2. Can PRIMARY KEY contain NULL values?

No.

---

### 3. Can a table have multiple PRIMARY KEYs?

No, only one PRIMARY KEY.

---

### 4. Can PRIMARY KEY contain duplicate values?

No.

---

### 5. What is a Composite PRIMARY KEY?

A PRIMARY KEY made from multiple columns.

---

### 6. Does PRIMARY KEY create an index?

Yes, automatically.

---

### 7. Difference Between PRIMARY KEY and UNIQUE KEY?

| PRIMARY KEY | UNIQUE KEY |
|------------|------------|
| Only one per table | Multiple allowed |
| No NULL values | NULL allowed |
| Uniquely identifies row | Ensures uniqueness |

---

# Summary

A PRIMARY KEY is the most important constraint in SQL. It ensures that every row in a table has a unique identity by preventing duplicate and NULL values. It is widely used with AUTO_INCREMENT and is the foundation for creating relationships between tables.
