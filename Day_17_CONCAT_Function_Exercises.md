# Day 17: CONCAT() Function Exercises

## Introduction

The `CONCAT()` function is used to join two or more strings into a single string. It is commonly used to combine column values, add separators, and create formatted output.

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
CREATE TABLE employee(
    emp_id INT PRIMARY KEY,
    fname VARCHAR(30),
    lname VARCHAR(30),
    desig VARCHAR(30),
    dept VARCHAR(30)
);
```

### Insert Data

```sql
INSERT INTO employee
VALUES
(101,'Raju','Rastogi','Manager','Loan'),
(102,'Sham','Mohan','Cashier','Cash'),
(103,'Baburao','Apte','Associate','Loan'),
(104,'Paul','Philip','Accountant','Account'),
(105,'Alex','Watt','Associate','Deposit');
```

---

## View Data

```sql
SELECT * FROM employee;
```

### Output

```text
+--------+---------+---------+------------+----------+
| emp_id | fname   | lname   | desig      | dept     |
+--------+---------+---------+------------+----------+
| 101    | Raju    | Rastogi | Manager    | Loan     |
| 102    | Sham    | Mohan   | Cashier    | Cash     |
| 103    | Baburao | Apte    | Associate  | Loan     |
| 104    | Paul    | Philip  | Accountant | Account  |
| 105    | Alex    | Watt    | Associate  | Deposit  |
+--------+---------+---------+------------+----------+
```

---

## Syntax

```sql
CONCAT(string1, string2, string3, ...)
```

---

# Exercise 1

### Task

Display the employee ID, first name, designation, and department separated by a colon (`:`).

### Query

```sql
SELECT CONCAT(emp_id,':',fname,':',desig,':',dept) AS employee_details
FROM employee;
```

### Output

```text
+--------------------------+
| employee_details         |
+--------------------------+
| 101:Raju:Manager:Loan    |
| 102:Sham:Cashier:Cash    |
| 103:Baburao:Associate:Loan |
| 104:Paul:Accountant:Account |
| 105:Alex:Associate:Deposit |
+--------------------------+
```

### Explanation

`CONCAT()` joins multiple column values into one string using `:` as a separator.

---

# Exercise 2

### Task

Display employee ID, first name, last name, designation, and department separated by a colon.

### Query

```sql
SELECT CONCAT(emp_id,':',fname,' ',lname,':',desig,':',dept) AS employee_details
FROM employee;
```

### Output

```text
+------------------------------------+
| employee_details                   |
+------------------------------------+
| 101:Raju Rastogi:Manager:Loan      |
| 102:Sham Mohan:Cashier:Cash        |
| 103:Baburao Apte:Associate:Loan    |
| 104:Paul Philip:Accountant:Account |
| 105:Alex Watt:Associate:Deposit    |
+------------------------------------+
```

### Explanation

A space is added between first and last names, while colons separate the remaining values.

---

# Exercise 3

### Task

Display employee ID, first name, designation (in uppercase), and department.

### Query

```sql
SELECT CONCAT(emp_id,':',fname,':',UPPER(desig),':',dept) AS employee_details
FROM employee;
```

### Output

```text
+----------------------------+
| employee_details           |
+----------------------------+
| 101:Raju:MANAGER:Loan      |
| 102:Sham:CASHIER:Cash      |
| 103:Baburao:ASSOCIATE:Loan |
| 104:Paul:ACCOUNTANT:Account|
| 105:Alex:ASSOCIATE:Deposit |
+----------------------------+
```

### Explanation

`UPPER()` converts the designation into uppercase before concatenating it.

---

# Exercise 4

### Task

Display employee ID prefixed with **L** if the department is Loan, otherwise prefix with **C**.

### Query

```sql
SELECT
CASE
    WHEN dept='Loan' THEN CONCAT('L',emp_id,' ',fname)
    ELSE CONCAT('C',emp_id,' ',fname)
END AS employee_code
FROM employee;
```

### Output

```text
+---------------+
| employee_code |
+---------------+
| L101 Raju     |
| C102 Sham     |
| L103 Baburao  |
| C104 Paul     |
| C105 Alex     |
+---------------+
```

### Explanation

The `CASE` statement checks the department. If it is **Loan**, `L` is prefixed; otherwise, `C` is prefixed.

---

## Important Notes

- `CONCAT()` joins multiple strings into one.
- Numbers are automatically converted to strings.
- You can use separators like `:`, `-`, `,`, or spaces.
- `CONCAT()` can be combined with functions like `UPPER()`, `LOWER()`, `REVERSE()`, and `CASE`.

---

## Common Errors

### Error 1

#### Wrong

```sql
SELECT emp_id + fname
FROM employee;
```

#### Correct

```sql
SELECT CONCAT(emp_id,fname)
FROM employee;
```

#### Reason

`+` does not concatenate strings in MySQL.

---

### Error 2

#### Wrong

```sql
SELECT CONCAT(emp_id:fname)
FROM employee;
```

#### Correct

```sql
SELECT CONCAT(emp_id,':',fname)
FROM employee;
```

#### Reason

Each value must be separated by commas inside `CONCAT()`.

---

## Interview Questions

### Q1. What does CONCAT() do?

#### Answer

It joins two or more strings into a single string.

---

### Q2. Can CONCAT() join numbers and strings?

#### Answer

Yes. MySQL automatically converts numbers into strings.

---

### Q3. Can CONCAT() be used with other functions?

#### Answer

Yes. It can be combined with functions like `UPPER()`, `LOWER()`, `REVERSE()`, `SUBSTRING()`, and `CASE`.

---

## Commands Covered

```sql
CONCAT()
UPPER()
CASE
SELECT
```

---

## SQL Query Execution Order

```text
1. FROM employee
2. Evaluate CASE (if present)
3. Apply UPPER() (if present)
4. Apply CONCAT()
5. SELECT
6. Display Result
```

---

## Summary

- `CONCAT()` combines multiple strings.
- Separators can be added inside `CONCAT()`.
- It works with numbers and text.
- It can be combined with string functions and `CASE`.
- It is widely used to create formatted output.
