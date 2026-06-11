# Day 8: CREATE DATABASE and CREATE TABLE with Constraints

## Introduction

In SQL, a database is used to store related data. A table is created inside a database to organize data into rows and columns.

In this task, we create a database named `bank_db` and a table named `employees` with the following constraints:

* `emp_id` should be unique and not allow NULL values.
* `emp_id` should automatically increment.
* `name` should not allow NULL values.
* `desig` should have a default value of `'Probation'`.

---

## Database Setup Used

### Create Database

```sql
CREATE DATABASE bank_db;
```

### Use Database

```sql
USE bank_db;
```

### Create Table

```sql
CREATE TABLE employees(
    emp_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(50) NOT NULL,
    desig VARCHAR(50) DEFAULT 'Probation',
    dept VARCHAR(50)
);
```

---

## View Table Structure

```sql
DESC employees;
```

### Output

```text
+--------+-------------+------+-----+------------+----------------+
| Field  | Type        | Null | Key | Default    | Extra          |
+--------+-------------+------+-----+------------+----------------+
| emp_id | int         | NO   | PRI | NULL       | auto_increment |
| name   | varchar(50) | NO   |     | NULL       |                |
| desig  | varchar(50) | YES  |     | Probation  |                |
| dept   | varchar(50) | YES  |     | NULL       |                |
+--------+-------------+------+-----+------------+----------------+
```

---

## Syntax

### Create Database

```sql
CREATE DATABASE database_name;
```

### Use Database

```sql
USE database_name;
```

### Create Table

```sql
CREATE TABLE table_name(
    column_name datatype constraints
);
```

---

## Example 1

### Query

```sql
INSERT INTO employees(name, dept)
VALUES('Rahul', 'IT');
```

### Output

```text
Query OK, 1 row affected
```

### Explanation

Since `emp_id` is AUTO_INCREMENT, MySQL automatically generates its value.

---

## Example 2

### Query

```sql
SELECT * FROM employees;
```

### Output

```text
+--------+-------+-----------+------+
| emp_id | name  | desig     | dept |
+--------+-------+-----------+------+
| 1      | Rahul | Probation | IT   |
+--------+-------+-----------+------+
```

### Explanation

The `desig` column automatically gets the default value `'Probation'`.

---

## Example 3

### Query

```sql
INSERT INTO employees(name, desig, dept)
VALUES('Priya', 'Manager', 'HR');
```

### Output

```text
Query OK, 1 row affected
```

### Explanation

Since a designation is provided, the default value is not used.

---

## Important Notes

* PRIMARY KEY does not allow duplicate values.
* PRIMARY KEY does not allow NULL values.
* AUTO_INCREMENT automatically generates the next number.
* NOT NULL ensures a value must be provided.
* DEFAULT assigns a value when none is specified.

---

## Common Errors

### Error 1

#### Wrong

```sql
INSERT INTO employees(emp_id,name)
VALUES(1,'Rahul');

INSERT INTO employees(emp_id,name)
VALUES(1,'Priya');
```

#### Correct

```sql
INSERT INTO employees(name)
VALUES('Rahul');

INSERT INTO employees(name)
VALUES('Priya');
```

#### Reason

PRIMARY KEY columns cannot contain duplicate values.

---

### Error 2

#### Wrong

```sql
INSERT INTO employees(name)
VALUES(NULL);
```

#### Correct

```sql
INSERT INTO employees(name)
VALUES('Rahul');
```

#### Reason

The `name` column is defined with NOT NULL.

---

## Interview Questions

### Q1. What is a PRIMARY KEY?

#### Answer

A PRIMARY KEY uniquely identifies each record in a table and does not allow NULL or duplicate values.

---

### Q2. What is AUTO_INCREMENT?

#### Answer

AUTO_INCREMENT automatically generates sequential numeric values for a column.

---

### Q3. What is the purpose of DEFAULT?

#### Answer

DEFAULT provides a predefined value when no value is supplied during insertion.

---

### Q4. Difference between PRIMARY KEY and UNIQUE?

#### Answer

PRIMARY KEY does not allow NULL values and only one PRIMARY KEY can exist in a table. UNIQUE allows NULL values (depending on DBMS) and multiple UNIQUE constraints can exist.

---

## Commands Covered

```sql
CREATE DATABASE
USE
CREATE TABLE
DESC
INSERT INTO
SELECT
PRIMARY KEY
AUTO_INCREMENT
NOT NULL
DEFAULT
```

---

## SQL Query Execution Order (If Applicable)

```text
1. CREATE DATABASE bank_db
2. USE bank_db
3. CREATE TABLE employees
4. INSERT records
5. SELECT records
6. DESC employees
```

---

## Summary

* Created database `bank_db`.
* Created table `employees`.
* Applied PRIMARY KEY on `emp_id`.
* Applied AUTO_INCREMENT on `emp_id`.
* Applied NOT NULL on `name`.
* Applied DEFAULT 'Probation' on `desig`.
* Verified table structure using DESC.
* Inserted records successfully.
   
