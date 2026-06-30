# Day 16: INSERT(), LEFT(), RIGHT(), REPEAT() & TRIM() Functions

## Introduction

MySQL provides several useful string functions for inserting text,
extracting characters, repeating strings, and removing unwanted spaces.
These functions are commonly used while formatting and manipulating text
data.

------------------------------------------------------------------------

## Database Setup Used

### Create Database

``` sql
CREATE DATABASE student_db;
```

### Use Database

``` sql
USE student_db;
```

### Create Table

``` sql
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

``` sql
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

------------------------------------------------------------------------

## View Data

``` sql
SELECT * FROM students;
```

### Output

``` text
101 Rahul 21 Pune    BCA   85
102 Navin 22 Pune    BCA   90
103 Dikshi21 Mumbai  BTech 95
104 Amit  23 Delhi   BCA   70
105 Priya 22 Mumbai  BCom  88
106 Rohit 20 Pune    BTech 76
107 Sneha 21 Delhi   BCA   92
108 Neha  22 Mumbai  BCom  80
```

------------------------------------------------------------------------

## Syntax

``` sql
INSERT(str,pos,len,new_string);

LEFT(str,length);

RIGHT(str,length);

REPEAT(str,count);

TRIM(str);
```

------------------------------------------------------------------------

## Example 1

### Query

``` sql
SELECT INSERT('Hello Wassup',6,0,'Raju ');
```

### Output

``` text
Hello Raju Wassup
```

### Explanation

Inserts the text `Raju` starting from position 6 without deleting any
characters.

------------------------------------------------------------------------

## Example 2

### Query

``` sql
SELECT LEFT('Abcdefghij',3);
SELECT RIGHT('Abcdefghij',4);
```

### Output

``` text
LEFT  : Abc
RIGHT : ghij
```

### Explanation

`LEFT()` returns characters from the beginning, while `RIGHT()` returns
characters from the end.

------------------------------------------------------------------------

## Example 3

### Query

``` sql
SELECT REPEAT('o',5);
SELECT TRIM('   Alright!   ');
```

### Output

``` text
ooooo
Alright!
```

### Explanation

`REPEAT()` repeats a string the specified number of times. `TRIM()`
removes leading and trailing spaces.

------------------------------------------------------------------------

## Important Notes

-   `INSERT()` does not modify table data unless used in an UPDATE
    statement.
-   Positions in `INSERT()` start from 1.
-   `LEFT()` and `RIGHT()` return the whole string if the requested
    length exceeds the string length.
-   `TRIM()` removes only leading and trailing spaces.

------------------------------------------------------------------------

## Common Errors

### Error 1

#### Wrong

``` sql
SELECT LEFT('Hello');
```

#### Correct

``` sql
SELECT LEFT('Hello',2);
```

#### Reason

`LEFT()` requires the number of characters to return.

------------------------------------------------------------------------

### Error 2

#### Wrong

``` sql
SELECT REPEAT('Hi');
```

#### Correct

``` sql
SELECT REPEAT('Hi',3);
```

#### Reason

`REPEAT()` requires the repetition count.

------------------------------------------------------------------------

## Interview Questions

### Q1. What is the difference between LEFT() and RIGHT()?

#### Answer

`LEFT()` returns characters from the beginning, while `RIGHT()` returns
characters from the end.

------------------------------------------------------------------------

### Q2. Does TRIM() remove spaces inside a string?

#### Answer

No. It removes only leading and trailing spaces.

------------------------------------------------------------------------

### Q3. What does INSERT() do?

#### Answer

It inserts a string into another string at a specified position and can
optionally replace characters.

------------------------------------------------------------------------

## Commands Covered

``` sql
INSERT()
LEFT()
RIGHT()
REPEAT()
TRIM()
```

------------------------------------------------------------------------

## SQL Query Execution Order (If Applicable)

``` text
1. Evaluate the function.
2. Process the string.
3. Return the resulting value.
```

------------------------------------------------------------------------

## Summary

-   INSERT() inserts text into a string.
-   LEFT() extracts characters from the left.
-   RIGHT() extracts characters from the right.
-   REPEAT() repeats a string.
-   TRIM() removes leading and trailing spaces.
