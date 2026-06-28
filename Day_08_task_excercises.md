# Day 8: SQL DML Commands (INSERT, UPDATE & DELETE)

## Introduction

Data Manipulation Language (DML) is used to add, modify, and remove data from database tables. The three most commonly used DML commands are **INSERT**, **UPDATE**, and **DELETE**. These commands affect only the data inside a table, not the table structure.

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

### Insert Data

```sql
INSERT INTO employees (emp_id, name, desig, dept)
VALUES
(101, 'Raju', 'Manager', 'Loan'),
(102, 'Sham', 'Cashier', 'Cash'),
(103, 'Paul', 'Associate', 'Loan'),
(104, 'Alex', 'Accountant', 'Account'),
(105, 'Victor', 'Associate', 'Deposit');
```

---

## View Data

```sql
SELECT * FROM employees;
```

### Output

```text
+--------+--------+------------+----------+
| emp_id | name   | desig      | dept     |
+--------+--------+------------+----------+
| 101    | Raju   | Manager    | Loan     |
| 102    | Sham   | Cashier    | Cash     |
| 103    | Paul   | Associate  | Loan     |
| 104    | Alex   | Accountant | Account  |
| 105    | Victor | Associate  | Deposit  |
+--------+--------+------------+----------+
```

---

## Syntax

### INSERT

```sql
INSERT INTO table_name(column1, column2, ...)
VALUES(value1, value2, ...);
```

### UPDATE

```sql
UPDATE table_name
SET column_name = value
WHERE condition;
```

### DELETE

```sql
DELETE FROM table_name
WHERE condition;
```

---

## Example 1 - INSERT

### Query

```sql
INSERT INTO employees(emp_id, name, desig, dept)
VALUES
(106, 'Kiran', 'Clerk', 'Loan');
```

### Output

```text
1 row inserted successfully.
```

### Explanation

A new employee record is inserted into the `employees` table.

---

## Example 2 - UPDATE

### Query

```sql
UPDATE employees
SET dept = 'IT'
WHERE emp_id = 103;
```

### Output

```text
Query OK, 1 row affected.
```

### Explanation

The department of employee **Paul (emp_id = 103)** is changed from **Loan** to **IT**.

---

## Example 3 - DELETE

### Query

```sql
DELETE FROM employees
WHERE emp_id = 102;
```

### Output

```text
Query OK, 1 row affected.
```

### Explanation

The employee record with **emp_id = 102 (Sham)** is permanently removed from the table.

---

## Important Notes

* `INSERT` adds new rows to a table.
* `UPDATE` modifies existing rows.
* `DELETE` removes rows but keeps the table structure.
* Always use a `WHERE` clause with `UPDATE` and `DELETE` to avoid affecting all rows.
* `AUTO_INCREMENT` automatically generates IDs if `emp_id` is not specified during insertion.

---

## Common Errors

### Error 1

#### Wrong

```sql
UPDATE employees
SET dept = 'IT';
```

#### Correct

```sql
UPDATE employees
SET dept = 'IT'
WHERE emp_id = 103;
```

#### Reason

Without the `WHERE` clause, **every employee's department** will become `IT`.

---

### Error 2

#### Wrong

```sql
DELETE employees
WHERE emp_id = 102;
```

#### Correct

```sql
DELETE FROM employees
WHERE emp_id = 102;
```

#### Reason

The `DELETE` statement must always use the `FROM` keyword.

---

## Interview Questions

### Q1. What is the difference between INSERT, UPDATE, and DELETE?

#### Answer

* **INSERT** adds new records.
* **UPDATE** modifies existing records.
* **DELETE** removes existing records.

---

### Q2. Why is the WHERE clause important in UPDATE and DELETE?

#### Answer

The `WHERE` clause specifies which rows should be modified or deleted. Without it, all rows in the table are affected.

---

### Q3. Why does UPDATE not use the FROM keyword?

#### Answer

`UPDATE` directly specifies the table to modify:

```sql
UPDATE employees
```

The `FROM` keyword is unnecessary in standard MySQL syntax. `DELETE`, however, requires `FROM` because it specifies the table from which rows are removed.

---

## Commands Covered

```sql
INSERT INTO
UPDATE
SET
DELETE FROM
SELECT
```

---

## SQL Query Execution Order (If Applicable)

```text
INSERT
1. Identify the target table.
2. Validate column values.
3. Insert the new row.

UPDATE
1. Find rows using the WHERE clause.
2. Update specified columns.
3. Save the changes.

DELETE
1. Find rows using the WHERE clause.
2. Remove matching rows.
3. Save the changes.
```

---

## Summary

* DML commands manipulate data stored in tables.
* `INSERT` is used to add new records.
* `UPDATE` modifies existing records.
* `DELETE` removes records from a table.
* Always use the `WHERE` clause with `UPDATE` and `DELETE` for safe operations.
* `DELETE` removes data only; the table structure remains unchanged.
* `UPDATE` does not use `FROM`, while `DELETE` requires `FROM`.
