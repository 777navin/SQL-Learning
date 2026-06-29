# Day 10: SUBSTR() Function in SQL

## Introduction

The `SUBSTR()` (or `SUBSTRING()`) function is a SQL string function used to extract a specific part (substring) from a string. You can specify the starting position and the number of characters to return.

It is commonly used to extract names, initials, city prefixes, course codes, or any portion of text stored in a database.

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
|101  | Rahul  |21   | Pune    | BCA    |85     |
|102  | Navin  |22   | Pune    | BCA    |90     |
|103  | Dikshi |21   | Mumbai  | BTech  |95     |
|104  | Amit   |23   | Delhi   | BCA    |70     |
|105  | Priya  |22   | Mumbai  | BCom   |88     |
|106  | Rohit  |20   | Pune    | BTech  |76     |
|107  | Sneha  |21   | Delhi   | BCA    |92     |
|108  | Neha   |22   | Mumbai  | BCom   |80     |
+-----+--------+-----+---------+--------+-------+
```

---

## Syntax

```sql
SUBSTR(string, start_position, length)
```

### Parameters

- **string** → The text from which characters are extracted.
- **start_position** → Position to start extraction (starts from 1).
- **length** → Number of characters to extract.

---

## Example 1

### Query

```sql
SELECT name,
SUBSTR(name,1,3) AS first_three_letters
FROM students;
```

### Output

```text
+--------+----------------------+
| name   | first_three_letters  |
+--------+----------------------+
| Rahul  | Rah                  |
| Navin  | Nav                  |
| Dikshi | Dik                  |
| Amit   | Ami                  |
| Priya  | Pri                  |
| Rohit  | Roh                  |
| Sneha  | Sne                  |
| Neha   | Neh                  |
+--------+----------------------+
```

### Explanation

Extracts the first three characters from each student's name.

---

## Example 2

### Query

```sql
SELECT city,
SUBSTR(city,2,3) AS extracted_text
FROM students;
```

### Output

```text
+---------+----------------+
| city    | extracted_text |
+---------+----------------+
| Pune    | une            |
| Pune    | une            |
| Mumbai  | umb            |
| Delhi   | elh            |
| Mumbai  | umb            |
| Pune    | une            |
| Delhi   | elh            |
| Mumbai  | umb            |
+---------+----------------+
```

### Explanation

Starts from the second character of the city name and returns the next three characters.

---

## Example 3

### Query

```sql
SELECT course,
SUBSTR(course,1,2) AS code
FROM students;
```

### Output

```text
+--------+------+
| course | code |
+--------+------+
| BCA    | BC   |
| BCA    | BC   |
| BTech  | BT   |
| BCA    | BC   |
| BCom   | BC   |
| BTech  | BT   |
| BCA    | BC   |
| BCom   | BC   |
+--------+------+
```

### Explanation

Extracts the first two characters of the course name.

---

## Example 4

### Query

```sql
SELECT name,
SUBSTR(name,2) AS remaining_name
FROM students;
```

### Output

```text
+--------+----------------+
| name   | remaining_name |
+--------+----------------+
| Rahul  | ahul           |
| Navin  | avin           |
| Dikshi | ikshi          |
| Amit   | mit            |
| Priya  | riya           |
| Rohit  | ohit           |
| Sneha  | neha           |
| Neha   | eha            |
+--------+----------------+
```

### Explanation

If the length is omitted, `SUBSTR()` returns all remaining characters from the specified starting position.

---

## Important Notes

- `SUBSTR()` extracts part of a string.
- Position counting starts from **1**, not 0.
- If length is omitted, the remaining string is returned.
- If the starting position is greater than the string length, an empty string is returned.
- `SUBSTR()` and `SUBSTRING()` are synonyms in MySQL.

---

## Common Errors

### Error 1

#### Wrong

```sql
SELECT SUBSTR(name,0,3)
FROM students;
```

#### Correct

```sql
SELECT SUBSTR(name,1,3)
FROM students;
```

#### Reason

String indexing starts from **1** in MySQL.

---

### Error 2

#### Wrong

```sql
SELECT SUBSTR(name)
FROM students;
```

#### Correct

```sql
SELECT SUBSTR(name,2)
FROM students;
```

#### Reason

The starting position parameter is mandatory.

---

## Interview Questions

### Q1. What is the purpose of the SUBSTR() function?

#### Answer

It extracts a specified number of characters from a string starting at a given position.

---

### Q2. What happens if the length argument is omitted?

#### Answer

MySQL returns all characters from the starting position to the end of the string.

---

### Q3. Does SUBSTR() start counting from 0 or 1?

#### Answer

It starts counting from **1**.

---

## Commands Covered

```sql
SUBSTR()

SELECT

AS
```

---

## SQL Query Execution Order (If Applicable)

```text
1. FROM students
2. SELECT required columns
3. Apply SUBSTR() function
4. Display the final result
```

---

## Summary

- `SUBSTR()` extracts part of a string.
- Position numbering starts from **1**.
- Length parameter is optional.
- Frequently used for extracting prefixes, initials, and codes.
- `SUBSTR()` and `SUBSTRING()` perform the same task in MySQL.
