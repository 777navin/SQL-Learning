# Day 2: Tables and Data Insertion

## What is a Table?

A table is a collection of related data organized into rows and columns within a database.

- Row → Individual Record
- Column → Attribute / Field

Example:

| ID | Name  | City   |
|-----|--------|--------|
| 101 | Navin | Pune   |
| 102 | Rahul | Mumbai |

---

## Create Table

### Syntax

```sql
CREATE TABLE table_name (
    column1 datatype(size),
    column2 datatype(size),
    column3 datatype(size)
);
```

### Example

```sql
CREATE TABLE Student (
    id INT,
    name VARCHAR(100)
);
```

---

## Create Table If Not Exists

```sql
CREATE TABLE IF NOT EXISTS Student (
    id INT,
    name VARCHAR(100)
);
```

---

## Create Table As Select (Copy Existing Table)

### Syntax

```sql
CREATE TABLE new_table AS
SELECT *
FROM existing_table;
```

### Example

```sql
CREATE TABLE Student_Backup AS
SELECT *
FROM Student;
```

---

## Show All Tables

```sql
SHOW TABLES;
```

---

## Describe Table

```sql
DESCRIBE Student;
```

or

```sql
DESC Student;
```

---

## Example Table

```sql
CREATE TABLE Students (
    id INT,
    name VARCHAR(100),
    city VARCHAR(50)
);
```

---

## Insert Data Into Table

### Insert Specific Columns

```sql
INSERT INTO Students(id, name)
VALUES(101, 'Rahul');
```

```sql
INSERT INTO Students(id, name)
VALUES(102, 'Ram');
```

```sql
INSERT INTO Students(id, name)
VALUES(103, 'Sham');
```

> Only mentioned columns are mandatory.

---

## Insert Into All Columns

```sql
INSERT INTO Students
VALUES(101, 'Navin', 'Pune');
```

> Values must follow the same order as table columns.

---

## Insert Multiple Rows

```sql
INSERT INTO Students(id, name, city)
VALUES
(101, 'Rahul', 'Pune'),
(102, 'Ram', 'Mumbai'),
(103, 'Sham', 'Delhi');
```

---

## Insert Data From One Table to Another

### Copy All Columns

```sql
INSERT INTO Students_Backup
SELECT *
FROM Students;
```

### Copy Specific Columns

```sql
INSERT INTO Student_New(name, age)
SELECT name, age
FROM Students;
```

### Copy Rows Using Condition

```sql
INSERT INTO Students
SELECT *
FROM Old_Students
WHERE age > 20;
```

---

## Commands Covered

- CREATE TABLE
- CREATE TABLE IF NOT EXISTS
- CREATE TABLE AS SELECT
- SHOW TABLES
- DESCRIBE / DESC
- INSERT INTO
- INSERT INTO VALUES
- INSERT MULTIPLE ROWS
- INSERT INTO SELECT

---

### End of Day 2 - Tables & Data Insertion
