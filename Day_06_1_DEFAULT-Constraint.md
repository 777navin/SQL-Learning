# Day 6: DEFAULT Constraint in SQL

## Introduction

The DEFAULT constraint is used to provide a default value for a column when no value is specified during an INSERT operation.

If the user does not enter a value for that column, SQL automatically inserts the predefined default value.

DEFAULT helps:
- Reduce NULL values
- Maintain consistent data
- Automatically fill common values
- Simplify INSERT statements

---

## Syntax

### While Creating a Table

```sql
CREATE TABLE table_name (
    column_name datatype DEFAULT default_value
);
```

### Example

```sql
CREATE TABLE students (
    id INT,
    name VARCHAR(50),
    city VARCHAR(30) DEFAULT 'Pune'
);
```

---

## Example 1: DEFAULT Value Applied Automatically

### Create Table

```sql
CREATE TABLE students (
    id INT,
    name VARCHAR(50),
    city VARCHAR(30) DEFAULT 'Pune'
);
```

### Insert Data Without City

```sql
INSERT INTO students(id, name)
VALUES (101, 'Rahul');
```

### View Data

```sql
SELECT * FROM students;
```

### Output

```text
+------+-------+------+
| id   | name  | city |
+------+-------+------+
| 101  | Rahul | Pune |
+------+-------+------+
```

Since city was not provided, SQL inserted the default value "Pune".

---

## Example 2: Override DEFAULT Value

### Insert Data With City

```sql
INSERT INTO students(id, name, city)
VALUES (102, 'Navin', 'Mumbai');
```

### View Data

```sql
SELECT * FROM students;
```

### Output

```text
+------+-------+--------+
| id   | name  | city   |
+------+-------+--------+
| 101  | Rahul | Pune   |
| 102  | Navin | Mumbai |
+------+-------+--------+
```

DEFAULT is ignored because a value was supplied.

---

## Example 3: DEFAULT Numeric Value

### Create Table

```sql
CREATE TABLE employees (
    emp_id INT,
    emp_name VARCHAR(50),
    salary INT DEFAULT 25000
);
```

### Insert Record

```sql
INSERT INTO employees(emp_id, emp_name)
VALUES (1, 'Amit');
```

### Output

```text
+--------+----------+--------+
| emp_id | emp_name | salary |
+--------+----------+--------+
| 1      | Amit     | 25000  |
+--------+----------+--------+
```

---

## Example 4: DEFAULT Current Date

### Create Table

```sql
CREATE TABLE orders (
    order_id INT,
    order_date DATE DEFAULT (CURRENT_DATE)
);
```

### Insert Record

```sql
INSERT INTO orders(order_id)
VALUES (1);
```

### Output

```text
+----------+------------+
| order_id | order_date |
+----------+------------+
| 1        | Today's Date |
+----------+------------+
```

SQL automatically stores the current date.

---

## Adding DEFAULT to Existing Column

### Syntax

```sql
ALTER TABLE table_name
ALTER column_name SET DEFAULT default_value;
```

### MySQL Method

```sql
ALTER TABLE students
MODIFY city VARCHAR(30) DEFAULT 'Pune';
```

---

## Removing DEFAULT Constraint

### MySQL

```sql
ALTER TABLE students
ALTER city DROP DEFAULT;
```

or

```sql
ALTER TABLE students
MODIFY city VARCHAR(30);
```

---

## Using DEFAULT Keyword Explicitly

### Insert Statement

```sql
INSERT INTO students(id, name, city)
VALUES (103, 'Kajal', DEFAULT);
```

### Output

```text
+------+-------+------+
| id   | name  | city |
+------+-------+------+
| 103  | Kajal | Pune |
+------+-------+------+
```

---

## DEFAULT with NOT NULL

### Create Table

```sql
CREATE TABLE students (
    id INT PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    city VARCHAR(30) NOT NULL DEFAULT 'Pune'
);
```

### Insert

```sql
INSERT INTO students(id, name)
VALUES (104, 'Rohit');
```

### Output

```text
+------+-------+------+
| id   | name  | city |
+------+-------+------+
| 104  | Rohit | Pune |
+------+-------+------+
```

---

## Commands Covered

### Create Table with DEFAULT

```sql
CREATE TABLE students (
    id INT,
    city VARCHAR(30) DEFAULT 'Pune'
);
```

### Insert Without Specifying Column

```sql
INSERT INTO students(id)
VALUES (101);
```

### Insert Using DEFAULT Keyword

```sql
INSERT INTO students(id, city)
VALUES (102, DEFAULT);
```

### Modify Existing Column

```sql
ALTER TABLE students
MODIFY city VARCHAR(30) DEFAULT 'Pune';
```

### Remove DEFAULT

```sql
ALTER TABLE students
ALTER city DROP DEFAULT;
```

### View Table Structure

```sql
DESC students;
```

---

## Important Notes

- DEFAULT works only when no value is provided.
- If a value is supplied, DEFAULT is ignored.
- DEFAULT can be used with numbers, strings, dates, and timestamps.
- DEFAULT reduces manual data entry.
- DEFAULT can be combined with NOT NULL.
- DEFAULT does not replace explicitly inserted NULL values (unless restricted by NOT NULL).

---

## Common Errors

### Error 1

```sql
INSERT INTO students(id, city)
VALUES (101, NULL);
```

Result:

```text
NULL is inserted, not the DEFAULT value.
```

Reason:
DEFAULT is applied only when the column is omitted or DEFAULT keyword is used.

---

### Error 2

```sql
CREATE TABLE students (
    city VARCHAR(30) DEFAULT Pune
);
```

Error:

```text
Unknown column 'Pune'
```

Correct:

```sql
CREATE TABLE students (
    city VARCHAR(30) DEFAULT 'Pune'
);
```

String values must be enclosed in quotes.

---

## Interview Questions

### 1. What is the DEFAULT constraint?

A DEFAULT constraint provides a value automatically when no value is supplied during insertion.

---

### 2. Can DEFAULT be used with NOT NULL?

Yes.

```sql
city VARCHAR(30) NOT NULL DEFAULT 'Pune'
```

---

### 3. Does DEFAULT work if NULL is explicitly inserted?

No.

```sql
INSERT INTO students(city)
VALUES(NULL);
```

NULL will be stored unless NOT NULL is applied.

---

### 4. How do you use the DEFAULT keyword?

```sql
INSERT INTO students(id, city)
VALUES (101, DEFAULT);
```

---

### 5. Can DEFAULT be removed later?

Yes.

```sql
ALTER TABLE students
ALTER city DROP DEFAULT;
```

---

## Summary

- DEFAULT automatically inserts a predefined value.
- Used when a column value is not provided.
- Works with text, numbers, dates, and timestamps.
- Can be combined with NOT NULL.
- Can be added or removed using ALTER TABLE.
- Helps maintain consistent and cleaner data.
