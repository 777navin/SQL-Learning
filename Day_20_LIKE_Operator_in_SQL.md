# Day 20: LIKE Operator in SQL (MySQL)

## Introduction

The `LIKE` operator is used to search for a specific pattern in text values. It is commonly used with the `WHERE` clause to filter rows based on partial matches instead of exact matches.

`LIKE` is very useful when you don't know the complete value but know part of it.

For example:
- Find all students whose names start with "N"
- Find all cities ending with "i"
- Find all courses containing "Tech"

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

# View Data

```sql
SELECT * FROM students;
```

### Output

| id | name | age | city | course | marks |
|----|-------|-----|--------|---------|------|
|101|Rahul|21|Pune|BCA|85|
|102|Navin|22|Pune|BCA|90|
|103|Dikshi|21|Mumbai|BTech|95|
|104|Amit|23|Delhi|BCA|70|
|105|Priya|22|Mumbai|BCom|88|
|106|Rohit|20|Pune|BTech|76|
|107|Sneha|21|Delhi|BCA|92|
|108|Neha|22|Mumbai|BCom|80|

---

# What is LIKE?

The `LIKE` operator compares a column with a pattern.

Unlike `=`, which checks for an exact match, `LIKE` checks whether the value matches a specified pattern.

Example:

Instead of searching for exactly

```text
Navin
```

you can search for

```text
Starts with N
Ends with a
Contains av
```

---

# Wildcards Used with LIKE

## 1. % (Percent)

Represents **zero, one, or many characters.**

Examples

```text
'N%'      -> Starts with N
'%a'      -> Ends with a
'%av%'    -> Contains av
'%'       -> Everything
```

---

## 2. _ (Underscore)

Represents **exactly one character.**

Examples

```text
_Nvin
```

Matches

```text
Navin
```

because only one character is before "vin".

---

```text
_____
```

Matches any word having exactly five letters.

Example

```text
Rahul
Priya
Rohit
Sneha
```

---

# Syntax

```sql
SELECT column_name
FROM table_name
WHERE column_name LIKE 'pattern';
```

---

# Example 1 — Starts With

### Find students whose names start with 'N'

### Query

```sql
SELECT *
FROM students
WHERE name LIKE 'N%';
```

### Output

|id|name|
|--|----|
|102|Navin|
|108|Neha|

### Explanation

`N%`

means

Starts with **N** followed by any number of characters.

Examples matched

```
Navin
Neha
```

---

# Example 2 — Ends With

### Find students whose names end with 'a'

### Query

```sql
SELECT *
FROM students
WHERE name LIKE '%a';
```

### Output

|id|name|
|--|----|
|105|Priya|

### Explanation

`%a`

means

Any number of characters before **a**.

Only Priya ends with "a".

---

# Example 3 — Contains

### Find cities containing 'um'

### Query

```sql
SELECT *
FROM students
WHERE city LIKE '%um%';
```

### Output

|id|city|
|--|------|
|103|Mumbai|
|105|Mumbai|
|108|Mumbai|

### Explanation

`%um%`

means

Anything before "um" and anything after "um".

Mumbai contains "um".

---

# Example 4 — Starts and Ends

### Find names starting with 'R' and ending with 't'

### Query

```sql
SELECT *
FROM students
WHERE name LIKE 'R%t';
```

### Output

|id|name|
|--|------|
|106|Rohit|

### Explanation

The name must

- start with R
- end with t

Only Rohit satisfies both conditions.

---

# Example 5 — Exactly Five Letters

### Query

```sql
SELECT *
FROM students
WHERE name LIKE '_____';
```

### Output

|id|name|
|--|------|
|101|Rahul|
|105|Priya|
|106|Rohit|
|107|Sneha|

### Explanation

Each underscore represents one character.

```
_____
```

means exactly five characters.

---

# Example 6 — Second Letter is 'a'

### Query

```sql
SELECT *
FROM students
WHERE name LIKE '_a%';
```

### Output

|id|name|
|--|------|
|101|Rahul|
|102|Navin|

### Explanation

```
_a%
```

means

- first character can be anything
- second character must be 'a'
- remaining characters can be anything

---

# Example 7 — Course Starts with B

### Query

```sql
SELECT *
FROM students
WHERE course LIKE 'B%';
```

### Output

|id|course|
|--|------|
|101|BCA|
|102|BCA|
|103|BTech|
|104|BCA|
|105|BCom|
|106|BTech|
|107|BCA|
|108|BCom|

### Explanation

Every course begins with the letter B.

---

# Example 8 — City Ends with 'i'

### Query

```sql
SELECT *
FROM students
WHERE city LIKE '%i';
```

### Output

|id|city|
|--|------|
|103|Mumbai|
|104|Delhi|
|105|Mumbai|
|107|Delhi|
|108|Mumbai|

### Explanation

Cities ending with "i" are

- Mumbai
- Delhi

---

# LIKE vs =

|=|LIKE|
|---|---|
|Exact match|Pattern matching|
|No wildcard|Supports `%` and `_`|
|Faster|Slightly slower|
|Used for fixed values|Used for searching text|

Example

```sql
WHERE city='Pune'
```

Finds only Pune.

---

```sql
WHERE city LIKE 'P%'
```

Finds

```
Pune
Paris
Patna
Pimpri
```

if they exist.

---

# Pattern Cheat Sheet

|Pattern|Meaning|
|--------|--------|
|A%|Starts with A|
|%A|Ends with A|
|%A%|Contains A|
|_A%|Second letter is A|
|A___|Starts with A and has exactly 4 letters|
|_____|Exactly 5 letters|
|%|Everything|

---

# Important Notes

- `LIKE` works only with text (VARCHAR, CHAR, TEXT).
- `%` represents zero or more characters.
- `_` represents exactly one character.
- `LIKE` is usually used with the `WHERE` clause.
- Multiple wildcards can be combined.
- `LIKE '%'` returns all rows.
- MySQL is generally case-insensitive for `LIKE` with default collations.

---

# Common Errors

## Error 1

### Wrong

```sql
SELECT *
FROM students
WHERE name = 'N%';
```

### Correct

```sql
SELECT *
FROM students
WHERE name LIKE 'N%';
```

### Reason

`=` searches for the exact text `N%`.

`LIKE` understands `%` as a wildcard.

---

## Error 2

### Wrong

```sql
SELECT *
FROM students
WHERE name LIKE N%;
```

### Correct

```sql
SELECT *
FROM students
WHERE name LIKE 'N%';
```

### Reason

Patterns must always be written inside single quotes.

---

## Error 3

### Wrong

```sql
SELECT *
FROM students
WHERE name LIKE "%N";
```

### Correct

```sql
SELECT *
FROM students
WHERE name LIKE '%N';
```

### Reason

Although MySQL may allow double quotes in some SQL modes, string literals should be written using single quotes for portability and standard SQL syntax.

---

# Interview Questions

### Q1. What is the difference between LIKE and = ?

#### Answer

`=` checks for an exact value.

`LIKE` searches using patterns and wildcards.

---

### Q2. What does `%` represent?

#### Answer

Zero, one, or many characters.

Example

```sql
LIKE 'A%'
```

---

### Q3. What does `_` represent?

#### Answer

Exactly one character.

Example

```sql
LIKE '_a%'
```

---

### Q4. Can LIKE use multiple wildcards together?

#### Answer

Yes.

Example

```sql
LIKE 'A%t'
```

Starts with A and ends with t.

---

### Q5. Which wildcard is used for exactly one character?

#### Answer

The underscore (`_`) wildcard.

---

# Commands Covered

```sql
LIKE
WHERE
%
_
SELECT
```

---

# SQL Query Execution Order

```text
1. FROM students
2. WHERE name LIKE 'N%'
3. SELECT *
4. Display Result
```

---

# Summary

- `LIKE` is used for pattern matching.
- `%` matches zero or more characters.
- `_` matches exactly one character.
- `LIKE` is commonly used with `WHERE`.
- It is ideal for searching names, cities, emails, products, and other text values.
- `LIKE` is more flexible than the `=` operator.
