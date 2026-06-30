# Day 12: REPLACE() Function

## Introduction

The `REPLACE()` function in MySQL is used to replace all occurrences of a specified substring within a string with another substring.

It is useful when you need to modify text, correct spelling mistakes, update words, or format string values without changing the original data stored in the table.

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
+-----+---------+-----+---------+--------+-------+
| id  | name    | age | city    | course | marks |
+-----+---------+-----+---------+--------+-------+
|101  | Rahul   | 21  | Pune    | BCA    | 85    |
|102  | Navin   | 22  | Pune    | BCA    | 90    |
|103  | Dikshi  | 21  | Mumbai  | BTech  | 95    |
|104  | Amit    | 23  | Delhi   | BCA    | 70    |
|105  | Priya   | 22  | Mumbai  | BCom   | 88    |
|106  | Rohit   | 20  | Pune    | BTech  | 76    |
|107  | Sneha   | 21  | Delhi   | BCA    | 92    |
|108  | Neha    | 22  | Mumbai  | BCom   | 80    |
+-----+---------+-----+---------+--------+-------+
```

---

## Syntax

```sql
REPLACE(string, old_substring, new_substring)
```

### Parameters

- **string** → Original string.
- **old_substring** → Text to be replaced.
- **new_substring** → Replacement text.

---

## Example 1

### Query

```sql
SELECT REPLACE('I Love Java','Java','MySQL') AS Result;
```

### Output

```text
+--------------+
| Result       |
+--------------+
| I Love MySQL |
+--------------+
```

### Explanation

The word **Java** is replaced with **MySQL**.

---

## Example 2

### Query

```sql
SELECT
name,
REPLACE(city,'Pune','Hyderabad') AS New_City
FROM students;
```

### Output

```text
+---------+------------+
| name    | New_City   |
+---------+------------+
| Rahul   | Hyderabad  |
| Navin   | Hyderabad  |
| Dikshi  | Mumbai     |
| Amit    | Delhi      |
| Priya   | Mumbai     |
| Rohit   | Hyderabad  |
| Sneha   | Delhi      |
| Neha    | Mumbai     |
+---------+------------+
```

### Explanation

Only the displayed result changes. The actual values stored in the table remain unchanged.

---

## Example 3

### Query

```sql
SELECT
name,
REPLACE(course,'B','Bachelor of ') AS Full_Course
FROM students;
```

### Output

```text
+---------+--------------------+
| name    | Full_Course        |
+---------+--------------------+
| Rahul   | Bachelor of CA     |
| Navin   | Bachelor of CA     |
| Dikshi  | Bachelor of Tech   |
| Amit    | Bachelor of CA     |
| Priya   | Bachelor of Com    |
| Rohit   | Bachelor of Tech   |
| Sneha   | Bachelor of CA     |
| Neha    | Bachelor of Com    |
+---------+--------------------+
```

### Explanation

The first letter **B** is replaced with **Bachelor of ** in every course name.

---

## Important Notes

- `REPLACE()` is **case-sensitive**.
- It replaces **all occurrences** of the specified substring.
- It returns a new string without modifying the original data.
- If the substring is not found, the original string is returned.
- It can be used inside `SELECT`, `UPDATE`, `WHERE`, and other SQL statements.

---

## Common Errors

### Error 1

#### Wrong

```sql
SELECT REPLACE(name,'Rahul');
```

#### Correct

```sql
SELECT REPLACE(name,'Rahul','Rohan')
FROM students;
```

#### Reason

`REPLACE()` requires **three arguments**.

---

### Error 2

#### Wrong

```sql
SELECT REPLACE(city, Pune, Hyderabad)
FROM students;
```

#### Correct

```sql
SELECT REPLACE(city,'Pune','Hyderabad')
FROM students;
```

#### Reason

String values must always be enclosed within single quotes.

---

## Interview Questions

### Q1. What is the purpose of the REPLACE() function?

#### Answer

It replaces all occurrences of a specified substring with another substring in a string.

---

### Q2. Does REPLACE() modify the original data?

#### Answer

No. It only returns the modified string unless it is used inside an `UPDATE` statement.

---

### Q3. Is REPLACE() case-sensitive?

#### Answer

Yes. It searches for the substring exactly as specified.

---

## Commands Covered

```sql
REPLACE()

SELECT

AS
```

---

## SQL Query Execution Order (If Applicable)

```text
1. FROM
2. SELECT
3. REPLACE() Function Execution
4. Display Result
```

---

## Summary

- `REPLACE()` replaces one substring with another.
- It requires three parameters.
- It replaces every occurrence of the specified substring.
- It is case-sensitive.
- It does not change table data unless used with `UPDATE`.
