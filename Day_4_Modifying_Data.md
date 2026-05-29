# Day 4: Modifying Data in SQL (DML Commands)

## Introduction

Data Manipulation Language (DML) commands are used to modify the data stored inside database tables. These commands allow you to insert new records, update existing records, and delete unwanted records.

For practice, we will use the table:

```sql
student_db.students
```

which already contains data.

---

## Commands Covered

* INSERT
* INSERT Multiple Rows
* INSERT Without Column Names
* UPDATE
* UPDATE Multiple Columns
* UPDATE Using Arithmetic
* UPDATE All Rows
* DELETE
* DELETE Multiple Rows
* DELETE Using Comparison Operators
* DELETE All Rows
* TRUNCATE
* REPLACE
* INSERT IGNORE
* INSERT ... ON DUPLICATE KEY UPDATE

---

## 1. INSERT

### Introduction

Used to add new records into a table.

---

## Syntax

```sql
INSERT INTO table_name(column1,column2,column3,...)
VALUES(value1,value2,value3,...);
```

---

## Example

```sql
INSERT INTO students
(id,name,age,city,course,marks)
VALUES
(109,'Karan',22,'Pune','BCA',87);
```

---

## Output

```text
109 | Karan | 22 | Pune | BCA | 87
```

---

## Important Notes

* Adds a new row.
* Column names can be specified.
* Values must match column data types.

---

## Common Errors

### Column Count Doesn't Match

Number of columns and values are different.

### Data Type Mismatch

Wrong value type inserted into a column.

---

## Interview Questions

### Q1. What is INSERT used for?

INSERT is used to add new records into a table.

### Q2. Can we insert data into selected columns only?

Yes, by specifying column names.

---

## Summary

INSERT adds new records to a table.

---

# 2. INSERT Multiple Rows

## Introduction

Used to insert multiple records using a single query.

---

## Syntax

```sql
INSERT INTO table_name
VALUES
(...),
(...),
(...);
```

---

## Example

```sql
INSERT INTO students
VALUES
(110,'Ankit',21,'Delhi','BCA',75),
(111,'Pooja',22,'Mumbai','BCom',82),
(112,'Riya',20,'Pune','BTech',91);
```

---

## Output

```text
3 rows inserted successfully.
```

---

## Important Notes

* Faster than multiple INSERT statements.
* Improves performance.

---

## Common Errors

### Missing Comma

Rows must be separated by commas.

### Incorrect Values

Each row must have the correct number of values.

---

## Interview Questions

### Q1. Why use multiple-row INSERT?

It improves performance and reduces query execution time.

### Q2. Can rows have different column counts?

No.

---

## Summary

Multiple rows can be inserted in a single query.

---

# 3. INSERT Without Column Names

## Introduction

Used when values are provided in the exact table column order.

---

## Syntax

```sql
INSERT INTO table_name
VALUES(...);
```

---

## Example

```sql
INSERT INTO students
VALUES
(113,'Vikas',23,'Nagpur','BCA',78);
```

---

## Output

```text
1 row inserted.
```

---

## Important Notes

* Must follow exact column order.
* Not recommended for large tables.

---

## Common Errors

### Wrong Column Order

Data may go into incorrect columns.

### Missing Values

All columns must receive values.

---

## Interview Questions

### Q1. Is specifying column names mandatory?

No.

### Q2. Why is specifying columns preferred?

It makes queries safer and more readable.

---

## Summary

Values must match the exact column order.

---

# 4. UPDATE

## Introduction

Used to modify existing records.

---

## Syntax

```sql
UPDATE table_name
SET column_name=value
WHERE condition;
```

---

## Example

```sql
UPDATE students
SET marks=95
WHERE id=102;
```

---

## Output

```text
102 | Navin | 22 | Pune | BCA | 95
```

---

## Important Notes

* WHERE clause limits affected rows.
* Without WHERE, all rows are updated.

---

## Common Errors

### Missing WHERE Clause

Updates every row.

### Invalid Column Name

Column does not exist.

---

## Interview Questions

### Q1. What happens if WHERE is omitted?

All rows get updated.

### Q2. Can UPDATE modify multiple rows?

Yes.

---

## Summary

UPDATE modifies existing data.

---

# 5. UPDATE Multiple Columns

## Introduction

Updates more than one column in a single query.

---

## Syntax

```sql
UPDATE table_name
SET col1=value1,
    col2=value2
WHERE condition;
```

---

## Example

```sql
UPDATE students
SET city='Bangalore',
    marks=98
WHERE id=102;
```

---

## Output

```text
102 | Navin | 22 | Bangalore | BCA | 98
```

---

## Important Notes

* Multiple columns can be updated together.
* Reduces query count.

---

## Common Errors

### Missing Comma

Columns must be separated by commas.

### Invalid WHERE Condition

Wrong rows may get updated.

---

## Interview Questions

### Q1. Can multiple columns be updated together?

Yes.

### Q2. Why is this useful?

Improves efficiency.

---

## Summary

Multiple columns can be modified in one UPDATE statement.

---

# 6. UPDATE Using Arithmetic

## Introduction

Used to increase or decrease numeric values.

---

## Syntax

```sql
UPDATE table_name
SET column=column+value
WHERE condition;
```

---

## Example

```sql
UPDATE students
SET marks=marks+5
WHERE city='Pune';
```

---

## Output

```text
All Pune students receive 5 additional marks.
```

---

## Important Notes

* Useful for salary, marks, bonus calculations.
* Works on numeric columns.

---

## Common Errors

### Using Text Columns

Arithmetic operations require numeric data.

### Missing WHERE Clause

Updates all rows.

---

## Interview Questions

### Q1. Can UPDATE perform calculations?

Yes.

### Q2. Where is this commonly used?

Salary increments and score updates.

---

## Summary

Arithmetic expressions can be used inside UPDATE.

---

# 7. UPDATE All Rows

## Introduction

Updates every row in the table.

---

## Syntax

```sql
UPDATE table_name
SET column=value;
```

---

## Example

```sql
UPDATE students
SET marks=100;
```

---

## Output

```text
All students now have marks = 100.
```

---

## Important Notes

* Affects every row.
* Use carefully.

---

## Common Errors

### Forgetting WHERE Clause

Accidental mass updates.

---

## Interview Questions

### Q1. How do you update every row?

By omitting the WHERE clause.

### Q2. Is it reversible?

Only if backup exists.

---

## Summary

UPDATE without WHERE affects all rows.

---

# 8. DELETE

## Introduction

Removes specific rows from a table.

---

## Syntax

```sql
DELETE FROM table_name
WHERE condition;
```

---

## Example

```sql
DELETE FROM students
WHERE id=109;
```

---

## Output

```text
Student Karan deleted.
```

---

## Important Notes

* Removes selected rows.
* Table structure remains.

---

## Common Errors

### Missing WHERE Clause

Deletes all rows.

### Wrong Condition

Incorrect rows removed.

---

## Interview Questions

### Q1. Does DELETE remove the table?

No.

### Q2. What remains after DELETE?

Table structure remains.

---

## Summary

DELETE removes records based on conditions.

---

# 9. DELETE Multiple Rows

## Example

```sql
DELETE FROM students
WHERE course='BCom';
```

---

## Output

```text
All BCom students deleted.
```

---

## Summary

DELETE can remove multiple matching rows.

---

# 10. DELETE Using Comparison Operators

## Example

```sql
DELETE FROM students
WHERE marks < 80;
```

---

## Output

```text
Students with marks below 80 deleted.
```

---

## Summary

Comparison operators can be used with DELETE.

---

# 11. DELETE All Rows

## Syntax

```sql
DELETE FROM table_name;
```

---

## Example

```sql
DELETE FROM students;
```

---

## Output

```text
All rows deleted.
Table still exists.
```

---

## Summary

Deletes all records but keeps the table structure.

---

# 12. TRUNCATE

## Introduction

Deletes all rows instantly.

---

## Syntax

```sql
TRUNCATE TABLE table_name;
```

---

## Example

```sql
TRUNCATE TABLE students;
```

---

## Output

```text
All rows removed instantly.
```

---

## Important Notes

* Faster than DELETE.
* Table structure remains.

---

## Common Errors

### Using Without Backup

Data cannot be recovered easily.

---

## Interview Questions

### Q1. Difference between DELETE and TRUNCATE?

DELETE removes rows one by one.
TRUNCATE removes all rows instantly.

### Q2. Which is faster?

TRUNCATE.

---

## Summary

TRUNCATE quickly clears a table.

---

# 13. REPLACE

## Introduction

Inserts a new row or replaces an existing one.

---

## Syntax

```sql
REPLACE INTO table_name
VALUES(...);
```

---

## Example

```sql
REPLACE INTO students
VALUES
(102,'Navin',22,'Pune','BCA',99);
```

---

## Output

```text
Existing row replaced or new row inserted.
```

---

## Important Notes

* Deletes old row and inserts new row.
* Requires PRIMARY KEY or UNIQUE KEY.

---

## Summary

REPLACE acts like DELETE + INSERT.

---

# 14. INSERT IGNORE

## Introduction

Ignores duplicate key errors.

---

## Syntax

```sql
INSERT IGNORE INTO table_name
VALUES(...);
```

---

## Example

```sql
INSERT IGNORE INTO students
VALUES
(102,'Navin',22,'Pune','BCA',90);
```

---

## Output

```text
Duplicate row skipped without error.
```

---

## Important Notes

* Useful for bulk imports.
* Prevents query failure.

---

## Summary

Duplicate rows are ignored safely.

---

# 15. INSERT ... ON DUPLICATE KEY UPDATE

## Introduction

Insert a row or update it if the key already exists.

---

## Syntax

```sql
INSERT INTO table_name(...)
VALUES(...)
ON DUPLICATE KEY UPDATE
column=value;
```

---

## Example

```sql
INSERT INTO students
(id,name,age,city,course,marks)
VALUES
(102,'Navin',22,'Pune','BCA',100)

ON DUPLICATE KEY UPDATE
marks=100;
```

---

## Output

```text
If ID exists → Marks updated.
If ID doesn't exist → New row inserted.
```

---

## Important Notes

* Frequently asked in interviews.
* Useful for UPSERT operations.

---

## Interview Questions

### Q1. What is UPSERT?

Insert new data or update existing data.

### Q2. Which command provides UPSERT functionality in MySQL?

INSERT ... ON DUPLICATE KEY UPDATE.

---

## Summary

Performs insert and update in a single query.

---

# Practice Commands

Run these commands one by one:

```sql
INSERT INTO students VALUES(109,'Karan',22,'Pune','BCA',87);

UPDATE students
SET marks=95
WHERE id=102;

UPDATE students
SET marks=marks+5
WHERE city='Pune';

DELETE FROM students
WHERE id=109;

INSERT IGNORE INTO students
VALUES(102,'Navin',22,'Pune','BCA',90);

REPLACE INTO students
VALUES(102,'Navin',22,'Pune','BCA',99);
```

---

# Day 4 Summary

In this chapter, you learned how to modify data using DML commands. You practiced inserting, updating, deleting, truncating, replacing, and handling duplicate records. These commands are among the most important SQL topics for interviews and real-world database management.
