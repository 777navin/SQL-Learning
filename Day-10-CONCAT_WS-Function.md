# Day 10: CONCAT_WS() Function

## Introduction

`CONCAT_WS()` stands for **Concatenate With Separator**.

It joins two or more strings into a single string by placing a specified separator between them. Unlike `CONCAT()`, you only specify the separator once, making queries cleaner and easier to read.

> **WS = With Separator**

---

## Database Setup Used

### Create Database

```sql
CREATE DATABASE student_db;
```

### Use Database

```sql
USE student_db;
```

### Create Table

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

### Insert Data

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

```sql
SELECT * FROM students;
```

### Output

```text
+-----+--------+-----+---------+--------+-------+
| id  | name   | age | city    | course | marks |
+-----+--------+-----+---------+--------+-------+
|101  | Rahul  | 21  | Pune    | BCA    | 85    |
|102  | Navin  | 22  | Pune    | BCA    | 90    |
|103  | Dikshi | 21  | Mumbai  | BTech  | 95    |
|104  | Amit   | 23  | Delhi   | BCA    | 70    |
|105  | Priya  | 22  | Mumbai  | BCom   | 88    |
|106  | Rohit  | 20  | Pune    | BTech  | 76    |
|107  | Sneha  | 21  | Delhi   | BCA    | 92    |
|108  | Neha   | 22  | Mumbai  | BCom   | 80    |
+-----+--------+-----+---------+--------+-------+
```

---

## Syntax

```sql
CONCAT_WS(separator, string1, string2, string3, ...);
```

- **separator** → Character(s) placed between strings.
- **string1, string2...** → Strings or column values to combine.

---

## Example 1

### Query

```sql
SELECT CONCAT_WS(' - ', name, city) AS student_info
FROM students;
```

### Output

```text
+------------------+
| student_info     |
+------------------+
| Rahul - Pune     |
| Navin - Pune     |
| Dikshi - Mumbai  |
| Amit - Delhi     |
| Priya - Mumbai   |
| Rohit - Pune     |
| Sneha - Delhi    |
| Neha - Mumbai    |
+------------------+
```

### Explanation

Each student's **name** and **city** are combined with `" - "` between them.

---

## Example 2

### Query

```sql
SELECT CONCAT_WS(', ', name, course, city) AS details
FROM students;
```

### Output

```text
+-------------------------+
| details                 |
+-------------------------+
| Rahul, BCA, Pune        |
| Navin, BCA, Pune        |
| Dikshi, BTech, Mumbai   |
| Amit, BCA, Delhi        |
| Priya, BCom, Mumbai     |
| Rohit, BTech, Pune      |
| Sneha, BCA, Delhi       |
| Neha, BCom, Mumbai      |
+-------------------------+
```

### Explanation

Three columns are joined using `", "` as the separator.

---

## Example 3

### Query

```sql
SELECT
CONCAT_WS(' | ', id, name, marks) AS student_record
FROM students;
```

### Output

```text
+-------------------+
| student_record    |
+-------------------+
| 101 | Rahul | 85  |
| 102 | Navin | 90  |
| 103 | Dikshi | 95 |
| 104 | Amit | 70   |
| 105 | Priya | 88  |
| 106 | Rohit | 76  |
| 107 | Sneha | 92  |
| 108 | Neha | 80   |
+-------------------+
```

### Explanation

Multiple columns are combined into one formatted string.

---

## Example 4

### Query

```sql
SELECT
CONCAT_WS(' ', 'Student:', name) AS result
FROM students;
```

### Output

```text
+------------------+
| result           |
+------------------+
| Student: Rahul   |
| Student: Navin   |
| Student: Dikshi  |
| Student: Amit    |
| Student: Priya   |
| Student: Rohit   |
| Student: Sneha   |
| Student: Neha    |
+------------------+
```

### Explanation

`CONCAT_WS()` can also combine text literals with column values.

---

## Important Notes

- `CONCAT_WS()` means **Concatenate With Separator**.
- Separator is written only once.
- Easier to read than `CONCAT()` when separators are needed.
- Automatically skips **NULL** values.
- Does **not** add extra separators for skipped NULL values.
- Empty strings (`''`) are **not skipped**.
- Can combine text, numbers, and column values.

---

## Common Errors

### Error 1

#### Wrong

```sql
SELECT CONCAT_WS(name, city)
FROM students;
```

#### Correct

```sql
SELECT CONCAT_WS(' - ', name, city)
FROM students;
```

#### Reason

The first argument must always be the separator.

---

### Error 2

#### Wrong

```sql
SELECT CONCAT_WS(name)
FROM students;
```

#### Correct

```sql
SELECT CONCAT_WS('-', name, city)
FROM students;
```

#### Reason

At least one separator and one or more strings are required.

---

## Interview Questions

### Q1. What is the difference between CONCAT() and CONCAT_WS()?

#### Answer

`CONCAT()` joins strings directly, while `CONCAT_WS()` joins strings using a separator that is specified only once.

---

### Q2. What does WS stand for?

#### Answer

**With Separator**.

---

### Q3. Does CONCAT_WS() ignore NULL values?

#### Answer

Yes. `NULL` values are skipped automatically, and no extra separators are added.

---

### Q4. Can CONCAT_WS() combine numbers and strings?

#### Answer

Yes. Numbers are automatically converted into strings before concatenation.

---

## Commands Covered

```sql
CONCAT_WS()

SELECT

AS
```

---

## SQL Query Execution Order (If Applicable)

```text
1. FROM
2. SELECT
3. CONCAT_WS() Function Execution
4. Display Result
```

---

## Summary

- `CONCAT_WS()` means Concatenate With Separator.
- Separator is specified only once.
- Makes formatted output easier to create.
- Automatically ignores NULL values.
- Cleaner and more readable than CONCAT() when separators are needed.
- Frequently used in reports, addresses, labels, and formatted output.
