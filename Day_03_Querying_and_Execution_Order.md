Day 3 - SQL SELECT Statement & Data Retrieval
📖 Overview

The SELECT statement is the most frequently used SQL command. It is used to retrieve data from one or more tables.

What SELECT Can Do
Retrieve all columns using *
Retrieve specific columns by name
Filter data using WHERE
Sort data using ORDER BY
Limit records using LIMIT
Remove duplicates using DISTINCT
Perform aggregation using COUNT(), AVG(), SUM(), MAX(), MIN()
Group records using GROUP BY
Filter groups using HAVING
1. Select Specific Columns
SELECT column_name1, column_name2
FROM table_name;
Example
SELECT id, name
FROM students;
2. Select All Columns
SELECT *
FROM students;
Examples
SELECT * FROM students;

SELECT id, name
FROM students;

SELECT name, id
FROM students;

Column order can be changed as required.

3. SELECT with WHERE Clause

Used to filter rows based on conditions.

SELECT *
FROM students
WHERE id = 101;
More Examples
SELECT *
FROM students
WHERE id = 102;

SELECT *
FROM students
WHERE id = 103;

SELECT *
FROM students
WHERE name = 'Navin';
4. SELECT with LIMIT

Used to restrict the number of rows returned.

SELECT *
FROM students
LIMIT 2;
Examples
SELECT * FROM students LIMIT 1;
SELECT * FROM students LIMIT 2;
SELECT * FROM students LIMIT 3;
SELECT * FROM students LIMIT 0;
5. ORDER BY (Ascending)

Sort data in ascending order.

SELECT *
FROM students
ORDER BY id ASC;
Examples
SELECT * FROM students ORDER BY name ASC;

SELECT * FROM students ORDER BY city ASC;

SELECT * FROM students ORDER BY id, name ASC;
6. ORDER BY (Descending)

Sort data in descending order.

SELECT *
FROM students
ORDER BY id DESC;
Examples
SELECT * FROM students ORDER BY name DESC;

SELECT * FROM students ORDER BY city, name DESC;
7. DISTINCT

Returns unique values only.

SELECT DISTINCT city
FROM students;
Examples
SELECT DISTINCT name
FROM students;

SELECT DISTINCT id, name
FROM students;

SELECT DISTINCT id, name, city
FROM students;
8. Aggregate Functions
COUNT()
SELECT COUNT(*)
FROM students;
COUNT(Column)
SELECT COUNT(name)
FROM students;
COUNT(DISTINCT)
SELECT COUNT(DISTINCT course)
FROM students;
MAX()
SELECT MAX(marks)
FROM students;
MIN()
SELECT MIN(marks)
FROM students;
AVG()
SELECT AVG(marks)
FROM students;
SUM()
SELECT SUM(marks)
FROM students;
9. GROUP BY

Groups rows having the same values.

Count Students in Each City
SELECT city, COUNT(*) AS student_count
FROM students
GROUP BY city;
Average Marks by Course
SELECT course, AVG(marks)
FROM students
GROUP BY course;
10. HAVING Clause

Filters grouped data.

Cities Having More Than One Student
SELECT city, COUNT(*) AS student_count
FROM students
GROUP BY city
HAVING COUNT(*) > 1;
11. LIKE Operator

Used for pattern matching.

Starts With
SELECT *
FROM students
WHERE name LIKE 'N%';
Ends With
SELECT *
FROM students
WHERE name LIKE '%a';
Contains
SELECT *
FROM students
WHERE name LIKE '%a%';
12. BETWEEN Operator

Used to find values within a range.

SELECT *
FROM students
WHERE marks BETWEEN 80 AND 90;
13. IN Operator

Used as a shortcut for multiple OR conditions.

SELECT *
FROM students
WHERE city IN ('Pune', 'Mumbai');
Sample Database Used
Create Database
CREATE DATABASE student_db;
USE student_db;
Create Table
CREATE TABLE students (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    age INT,
    city VARCHAR(100),
    course VARCHAR(50),
    marks INT
);
Insert Data
INSERT INTO students VALUES
(101,'Rahul',21,'Pune','BCA',85),
(102,'Navin',22,'Pune','BCA',90),
(103,'Dikshi',21,'Mumbai','BTech',95),
(104,'Amit',23,'Delhi','BCA',70),
(105,'Priya',22,'Mumbai','BCom',88),
(106,'Rohit',20,'Pune','BTech',78),
(107,'Sneha',24,'Delhi','BCA',92),
(108,'Neha',22,'Mumbai','BCom',89);
SQL Query Execution Order (Most Important)
SELECT
FROM
WHERE
GROUP BY
HAVING
ORDER BY
LIMIT
Logical Execution Order
FROM
WHERE
GROUP BY
HAVING
SELECT
ORDER BY
LIMIT
📌 Day 3 Topics Covered

✅ SELECT
✅ WHERE
✅ AND / OR
✅ ORDER BY
✅ LIMIT
✅ DISTINCT
✅ LIKE
✅ BETWEEN
✅ IN
✅ Aggregate Functions
✅ GROUP BY
✅ HAVING
✅ SQL Execution Order
