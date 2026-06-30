# Day 13: REVERSE() Function

## Introduction

The `REVERSE()` function in MySQL is a string function used to reverse the order of characters in a string. It returns the input string with all characters arranged from last to first. It is commonly used for string manipulation, pattern matching, data formatting, and interview questions.

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
REVERSE(string);
```

- **string** → The text or column whose characters need to be reversed.

---

## Example 1

### Query

```sql
SELECT REVERSE('MySQL') AS reversed_text;
```

### Output

```text
+---------------+
| reversed_text |
+---------------+
| LQSyM         |
+---------------+
```

### Explanation

The characters in the string **MySQL** are reversed one by one.

---

## Example 2

### Query

```sql
SELECT name, REVERSE(name) AS reversed_name
FROM students;
```

### Output

```text
+--------+---------------+
| name   | reversed_name |
+--------+---------------+
| Rahul  | luhaR         |
| Navin  | nivaN         |
| Dikshi | ihskiD        |
| Amit   | timA          |
| Priya  | ayirP         |
| Rohit  | tihoR         |
| Sneha  | ahenS         |
| Neha   | aheN          |
+--------+---------------+
```

### Explanation

Each student's name is displayed along with its reversed version.

---

## Example 3

### Query

```sql
SELECT
    city,
    REVERSE(city) AS reversed_city
FROM students;
```

### Output

```text
+---------+---------------+
| city    | reversed_city |
+---------+---------------+
| Pune    | enuP          |
| Pune    | enuP          |
| Mumbai  | iabmuM        |
| Delhi   | ihleD         |
| Mumbai  | iabmuM        |
| Pune    | enuP          |
| Delhi   | ihleD         |
| Mumbai  | iabmuM        |
+---------+---------------+
```

### Explanation

The `REVERSE()` function reverses every city name stored in the table.

---

## Important Notes

- `REVERSE()` returns a new reversed string.
- The original data stored in the table is not modified.
- It works with string literals as well as column values.
- Numbers stored as strings can also be reversed.
- NULL input returns NULL.

---

## Common Errors

### Error 1

#### Wrong

```sql
SELECT REVERSE(name, city)
FROM students;
```

#### Correct

```sql
SELECT REVERSE(name)
FROM students;
```

#### Reason

`REVERSE()` accepts only **one argument**.

---

### Error 2

#### Wrong

```sql
SELECT REVERSE
FROM students;
```

#### Correct

```sql
SELECT REVERSE(name)
FROM students;
```

#### Reason

`REVERSE` is a function and must be followed by parentheses containing the string.

---

## Interview Questions

### Q1. What does the REVERSE() function do?

#### Answer

It reverses the order of characters in a string and returns the reversed string.

---

### Q2. Does REVERSE() modify the original column values?

#### Answer

No. It only returns the reversed result in the query output. The original data remains unchanged.

---

### Q3. Can REVERSE() be used with both string literals and table columns?

#### Answer

Yes. It works with string constants as well as VARCHAR, CHAR, and TEXT columns.

---

## Commands Covered

```sql
REVERSE()

SELECT REVERSE('MySQL');

SELECT name, REVERSE(name)
FROM students;

SELECT city, REVERSE(city)
FROM students;
```

---

## SQL Query Execution Order (If Applicable)

```text
1. FROM
2. SELECT
3. REVERSE() function is applied
4. Display the result
```

---

## Summary

- `REVERSE()` reverses the characters of a string.
- It accepts only one string argument.
- It does not modify the original data.
- It can be used with string literals and table columns.
- It is useful for string manipulation, formatting, and interview questions.
