# Day 6: NOT NULL Constraint in SQL

## Introduction

The `NOT NULL` constraint is used to ensure that a column cannot contain NULL values.

A NULL value means "no value" or "missing value".

When a column is defined as `NOT NULL`, every row must contain a value for that column.

---

## Why Use NOT NULL?

- Prevents missing data.
- Ensures important columns always have values.
- Improves data integrity.
- Commonly used with PRIMARY KEY columns.

---

## Syntax

### While Creating a Table

```sql
CREATE TABLE table_name (
    column1 datatype NOT NULL,
    column2 datatype,
    column3 datatype NOT NULL
);
```

Example:

```sql
CREATE TABLE students (
    id INT NOT NULL,
    name VARCHAR(50) NOT NULL,
    age INT,
    city VARCHAR(50)
);
```

---

## Insert Data

Valid:

```sql
INSERT INTO students(id, name, age, city)
VALUES(101, 'Navin', 22, 'Pune');
```

Valid:

```sql
INSERT INTO students(id, name)
VALUES(102, 'Rahul');
```

Output:

```text
+-----+-------+------+------+
| id  | name  | age  | city |
+-----+-------+------+------+
| 101 | Navin | 22   | Pune |
| 102 | Rahul | NULL | NULL |
+-----+-------+------+------+
```

---

## NOT NULL Violation

Invalid:

```sql
INSERT INTO students(id, age)
VALUES(103, 21);
```

Error:

```text
ERROR 1364 (HY000):
Field 'name' doesn't have a default value
```

Because `name` is NOT NULL.

---

## Add NOT NULL to Existing Column

Syntax:

```sql
ALTER TABLE table_name
MODIFY column_name datatype NOT NULL;
```

Example:

```sql
ALTER TABLE students
MODIFY name VARCHAR(50) NOT NULL;
```

---

## Remove NOT NULL Constraint

Syntax:

```sql
ALTER TABLE table_name
MODIFY column_name datatype NULL;
```

Example:

```sql
ALTER TABLE students
MODIFY name VARCHAR(50) NULL;
```

---

## NOT NULL with PRIMARY KEY

Example:

```sql
CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    emp_name VARCHAR(50) NOT NULL
);
```

Note:

```text
PRIMARY KEY automatically includes:
1. NOT NULL
2. UNIQUE
```

So:

```sql
emp_id INT PRIMARY KEY
```

is equivalent to:

```sql
emp_id INT NOT NULL UNIQUE
```

---

## NOT NULL with DEFAULT

Example:

```sql
CREATE TABLE users (
    id INT PRIMARY KEY,
    country VARCHAR(50) NOT NULL DEFAULT 'India'
);
```

Insert:

```sql
INSERT INTO users(id)
VALUES(1);
```

Output:

```text
+----+---------+
| id | country |
+----+---------+
| 1  | India   |
+----+---------+
```

---

## Show Table Structure

Syntax:

```sql
DESC table_name;
```

Example:

```sql
DESC students;
```

Output:

```text
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| id    | int         | NO   |     | NULL    |       |
| name  | varchar(50) | NO   |     | NULL    |       |
| age   | int         | YES  |     | NULL    |       |
| city  | varchar(50) | YES  |     | NULL    |       |
+-------+-------------+------+-----+---------+-------+
```

`NO` means NOT NULL.

---

## Related Commands

### CREATE TABLE with NOT NULL

```sql
CREATE TABLE products (
    product_id INT NOT NULL,
    product_name VARCHAR(100) NOT NULL,
    price DECIMAL(10,2) NOT NULL
);
```

---

### ALTER TABLE MODIFY NOT NULL

```sql
ALTER TABLE products
MODIFY product_name VARCHAR(100) NOT NULL;
```

---

### ALTER TABLE MODIFY NULL

```sql
ALTER TABLE products
MODIFY product_name VARCHAR(100) NULL;
```

---

### INSERT INTO

```sql
INSERT INTO products
VALUES(1, 'Laptop', 55000);
```

---

### UPDATE

Valid:

```sql
UPDATE products
SET product_name = 'Gaming Laptop'
WHERE product_id = 1;
```

Invalid:

```sql
UPDATE products
SET product_name = NULL
WHERE product_id = 1;
```

Error:

```text
ERROR 1048 (23000):
Column 'product_name' cannot be null
```

---

## Important Notes

- NULL and NOT NULL are constraints.
- NOT NULL prevents storing NULL values.
- Primary Key columns are automatically NOT NULL.
- Existing NULL values must be removed before adding NOT NULL.
- NOT NULL can be used with DEFAULT values.
- Multiple columns can have NOT NULL constraints.

---

## Common Errors

### Error 1

```text
ERROR 1048 (23000):
Column cannot be null
```

Reason:

Trying to insert or update NULL into a NOT NULL column.

---

### Error 2

```text
ERROR 1364 (HY000):
Field doesn't have a default value
```

Reason:

NOT NULL column was omitted during INSERT.

---

### Error 3

```text
ERROR:
Invalid use of NULL value
```

Reason:

Trying to modify a column to NOT NULL while existing rows contain NULL values.

Fix:

```sql
UPDATE students
SET name = 'Unknown'
WHERE name IS NULL;
```

Then:

```sql
ALTER TABLE students
MODIFY name VARCHAR(50) NOT NULL;
```

---

## Interview Questions

### What is NOT NULL?

A constraint that prevents a column from storing NULL values.

---

### What is the difference between NULL and NOT NULL?

| NULL | NOT NULL |
|--------|-----------|
| Value may be missing | Value is mandatory |
| Can store NULL | Cannot store NULL |

---

### Can a PRIMARY KEY contain NULL?

No.

PRIMARY KEY automatically includes NOT NULL.

---

### Can a NOT NULL column have a DEFAULT value?

Yes.

Example:

```sql
country VARCHAR(50) NOT NULL DEFAULT 'India'
```

---

### How do you remove a NOT NULL constraint?

```sql
ALTER TABLE table_name
MODIFY column_name datatype NULL;
```

---

## Commands Covered

```sql
CREATE TABLE
INSERT INTO
UPDATE
ALTER TABLE
MODIFY
DESC
PRIMARY KEY
DEFAULT
NOT NULL
NULL
```

---

## Summary

- `NOT NULL` ensures a column always contains a value.
- Prevents missing or incomplete data.
- Applied during CREATE TABLE or ALTER TABLE.
- Works with PRIMARY KEY and DEFAULT.
- Any INSERT or UPDATE with NULL in a NOT NULL column will fail.
- One of the most commonly used SQL constraints.
