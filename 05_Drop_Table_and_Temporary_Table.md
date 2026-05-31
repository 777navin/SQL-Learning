# Day 5: DROP TABLE & TEMPORARY TABLE

## Introduction

The `DROP TABLE` command is used to permanently remove a table from a database.

When a table is dropped:

- The table structure is deleted.
- All records are deleted.
- Indexes and constraints are removed.
- The operation cannot be undone without a backup.

A **Temporary Table** is a special table that exists only during the current database session. It is automatically deleted when the session ends.

---

## Commands Covered

```sql
DROP TABLE
DROP TABLE IF EXISTS
DROP TABLE table1, table2
CREATE TEMPORARY TABLE
DROP TEMPORARY TABLE
SHOW TABLES
DESC
```

---

# DROP TABLE

## Syntax

```sql
DROP TABLE table_name;
```

## Example

```sql
DROP TABLE students;
```

## Output

```text
Query OK, 0 rows affected
```

The `students` table is permanently removed.

---

# Verify Existing Tables

## Syntax

```sql
SHOW TABLES;
```

## Example

```sql
SHOW TABLES;
```

## Output

```text
+----------------+
| Tables_in_db   |
+----------------+
| students       |
| employees      |
+----------------+
```

---

# DROP TABLE IF EXISTS

Used to avoid errors when the table does not exist.

## Syntax

```sql
DROP TABLE IF EXISTS table_name;
```

## Example

```sql
DROP TABLE IF EXISTS students;
```

## Output

```text
Query OK, 0 rows affected
```

---

# DROP Multiple Tables

## Syntax

```sql
DROP TABLE table1, table2, table3;
```

## Example

```sql
DROP TABLE students, employees;
```

## Output

```text
Query OK, 0 rows affected
```

Both tables are deleted.

---

# View Table Structure

## Syntax

```sql
DESC table_name;
```

## Example

```sql
DESC students;
```

## Output

```text
+--------+-------------+
| Field  | Type        |
+--------+-------------+
| id     | int         |
| name   | varchar(50) |
+--------+-------------+
```

---

# TEMPORARY TABLE

## Introduction

A temporary table exists only during the current database session.

Uses:

- Store intermediate results
- Simplify complex queries
- Temporary data processing
- Reporting operations

When the session ends, the temporary table is automatically removed.

---

# Create Temporary Table

## Syntax

```sql
CREATE TEMPORARY TABLE table_name (
    column1 datatype,
    column2 datatype
);
```

## Example

```sql
CREATE TEMPORARY TABLE temp_students (
    id INT,
    name VARCHAR(50)
);
```

---

# Insert Data Into Temporary Table

## Example

```sql
INSERT INTO temp_students
VALUES
(101,'Rahul'),
(102,'Navin');
```

---

# View Temporary Table Data

## Example

```sql
SELECT * FROM temp_students;
```

## Output

```text
+------+-------+
| id   | name  |
+------+-------+
| 101  | Rahul |
| 102  | Navin |
+------+-------+
```

---

# DROP TEMPORARY TABLE

Used to remove a temporary table before the session ends.

## Syntax

```sql
DROP TEMPORARY TABLE table_name;
```

## Example

```sql
DROP TEMPORARY TABLE temp_students;
```

## Output

```text
Query OK, 0 rows affected
```

The temporary table is deleted immediately.

---

# DROP TABLE vs DROP TEMPORARY TABLE

| DROP TABLE | DROP TEMPORARY TABLE |
|------------|---------------------|
| Deletes permanent table | Deletes temporary table |
| Removes table completely | Removes temporary table only |
| Used for normal tables | Used for temporary tables |
| Table exists until dropped | Table exists only during session |

---

# Example With Same Name

## Create Permanent Table

```sql
CREATE TABLE students (
    id INT
);
```

## Create Temporary Table

```sql
CREATE TEMPORARY TABLE students (
    id INT
);
```

## Drop Temporary Table

```sql
DROP TEMPORARY TABLE students;
```

Only the temporary table is removed.

The permanent table still exists.

---

# Important Notes

- `DROP TABLE` permanently deletes a table.
- All records are removed when a table is dropped.
- Use `DROP TABLE IF EXISTS` to avoid errors.
- Temporary tables are session-specific.
- Temporary tables are automatically deleted when the connection closes.
- Temporary tables are visible only to the current user session.
- `DROP TEMPORARY TABLE` affects only temporary tables.

---

# Common Errors

## Table Does Not Exist

```sql
DROP TABLE students;
```

### Error

```text
ERROR 1051 (42S02): Unknown table 'students'
```

### Solution

```sql
DROP TABLE IF EXISTS students;
```

---

## No Database Selected

```sql
DROP TABLE students;
```

### Error

```text
ERROR 1046 (3D000): No database selected
```

### Solution

```sql
USE student_db;
```

Then run:

```sql
DROP TABLE students;
```

---

## Temporary Table Not Found

```sql
DROP TEMPORARY TABLE temp_students;
```

### Error

```text
ERROR 1051 (42S02): Unknown table 'temp_students'
```

### Reason

The temporary table does not exist in the current session.

---

# Interview Questions

## Q1. What is the difference between DROP and DELETE?

| DROP | DELETE |
|--------|--------|
| Removes table | Removes rows |
| Structure deleted | Structure remains |
| DDL Command | DML Command |

---

## Q2. What is the difference between DROP and TRUNCATE?

| DROP | TRUNCATE |
|--------|--------|
| Deletes table completely | Deletes all rows |
| Structure removed | Structure remains |

---

## Q3. What is a Temporary Table?

A temporary table exists only during the current session and is automatically deleted when the connection closes.

---

## Q4. Can a Temporary Table and Permanent Table Have the Same Name?

Yes. MySQL allows both to exist simultaneously.

---

## Q5. What Happens When a Session Ends?

All temporary tables created in that session are automatically deleted.

---

# Summary

```sql
SHOW TABLES;

DESC students;

DROP TABLE students;

DROP TABLE IF EXISTS students;

DROP TABLE students, employees;

CREATE TEMPORARY TABLE temp_students (
    id INT,
    name VARCHAR(50)
);

SELECT * FROM temp_students;

DROP TEMPORARY TABLE temp_students;
```

In this chapter, we learned:

- DROP TABLE
- DROP TABLE IF EXISTS
- DROP Multiple Tables
- CREATE TEMPORARY TABLE
- DROP TEMPORARY TABLE
- SHOW TABLES
- DESC

These commands are used to manage and remove permanent and temporary tables in MySQL databases.
