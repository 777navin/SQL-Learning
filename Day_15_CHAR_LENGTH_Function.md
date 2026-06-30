# Day 15: CHAR_LENGTH() Function

## Introduction

The `CHAR_LENGTH()` function in MySQL is used to return the number of **characters** in a string. Unlike `LENGTH()`, which returns the number of bytes, `CHAR_LENGTH()` counts actual characters. This is especially useful when working with Unicode or multi-byte characters.

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
| 101 | Rahul  | 21  | Pune    | BCA    | 85    |
| 102 | Navin  | 22  | Pune    | BCA    | 90    |
| 103 | Dikshi | 21  | Mumbai  | BTech  | 95    |
| 104 | Amit   | 23  | Delhi   | BCA    | 70    |
| 105 | Priya  | 22  | Mumbai  | BCom   | 88    |
| 106 | Rohit  | 20  | Pune    | BTech  | 76    |
| 107 | Sneha  | 21  | Delhi   | BCA    | 92    |
| 108 | Neha   | 22  | Mumbai  | BCom   | 80    |
+-----+--------+-----+---------+--------+-------+
```

---

## Syntax

```sql
CHAR_LENGTH(string);
```

---

## Example 1

### Query

```sql
SELECT CHAR_LENGTH('Hello World') AS total_characters;
```

### Output

```text
+------------------+
| total_characters |
+------------------+
| 11               |
+------------------+
```

### Explanation

`Hello World` contains **11 characters**, including the space.

---

## Example 2

### Query

```sql
SELECT name,
       CHAR_LENGTH(name) AS name_length
FROM students;
```

### Output

```text
+--------+-------------+
| name   | name_length |
+--------+-------------+
| Rahul  | 5           |
| Navin  | 5           |
| Dikshi | 7           |
| Amit   | 4           |
| Priya  | 5           |
| Rohit  | 5           |
| Sneha  | 5           |
| Neha   | 4           |
+--------+-------------+
```

### Explanation

`CHAR_LENGTH()` returns the number of characters in each student's name.

---

## Example 3

### Query

```sql
SELECT city,
       CHAR_LENGTH(city) AS city_length
FROM students;
```

### Output

```text
+---------+-------------+
| city    | city_length |
+---------+-------------+
| Pune    | 4           |
| Pune    | 4           |
| Mumbai  | 7           |
| Delhi   | 5           |
| Mumbai  | 7           |
| Pune    | 4           |
| Delhi   | 5           |
| Mumbai  | 7           |
+---------+-------------+
```

### Explanation

The function calculates the number of characters in each city name.

---

## Important Notes

- `CHAR_LENGTH()` counts **characters**, not bytes.
- Spaces are counted as characters.
- Works with `VARCHAR`, `CHAR`, and string literals.
- Useful for Unicode and multilingual text.

---

## Common Errors

### Error 1

#### Wrong

```sql
SELECT CHAR_LENGTH(name, city)
FROM students;
```

#### Correct

```sql
SELECT CHAR_LENGTH(name)
FROM students;
```

#### Reason

`CHAR_LENGTH()` accepts **only one string argument**.

---

### Error 2

#### Wrong

```sql
SELECT CHAR_LENGTH
FROM students;
```

#### Correct

```sql
SELECT CHAR_LENGTH(name)
FROM students;
```

#### Reason

`CHAR_LENGTH` is a function and must include parentheses.

---

## Interview Questions

### Q1. What does `CHAR_LENGTH()` return?

#### Answer

It returns the total number of **characters** in a string.

---

### Q2. What is the difference between `CHAR_LENGTH()` and `LENGTH()`?

#### Answer

- `CHAR_LENGTH()` counts characters.
- `LENGTH()` counts bytes.

For ASCII text both usually return the same value, but for Unicode characters they can differ.

---

### Q3. Does `CHAR_LENGTH()` count spaces?

#### Answer

Yes. Spaces are treated as normal characters and are included in the count.

---

## Commands Covered

```sql
CHAR_LENGTH()

SELECT

AS
```

---

## SQL Query Execution Order (If Applicable)

```text
1. FROM students
2. SELECT required columns
3. Apply CHAR_LENGTH()
4. Display the result
```

---

## Summary

- `CHAR_LENGTH()` returns the number of characters in a string.
- It counts letters, numbers, symbols, and spaces.
- It is different from `LENGTH()`, which counts bytes.
- Useful for validating text length and Unicode strings.
- Commonly used with `SELECT`, `WHERE`, and string manipulation queries.
