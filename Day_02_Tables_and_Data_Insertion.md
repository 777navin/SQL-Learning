Day 2 - Tables & Data Insertion
What is a Table?

A table is a collection of related data organized into rows and columns inside a database.

Row (Record): Individual entry
Column (Field/Attribute): Type of information

Example:

ID	Name	City
101	Navin	Pune
102	Rahul	Mumbai
Create Table
Syntax
CREATE TABLE table_name (
    column1 datatype(size),
    column2 datatype(size),
    column3 datatype(size)
);
Example
CREATE TABLE Student (
    id INT,
    name VARCHAR(100)
);
Another Example
CREATE TABLE Student (
    name VARCHAR(100),
    age INT
);
Create Table If Not Exists
CREATE TABLE IF NOT EXISTS Student (
    id INT,
    name VARCHAR(100)
);
Copy Structure/Data Into New Table
Syntax
CREATE TABLE new_table AS
SELECT column1, column2
FROM existing_table;
Example
CREATE TABLE Student_Backup AS
SELECT *
FROM Student;
Show All Tables
SHOW TABLES;
Verify Table Structure
Describe Table

Displays columns, data types, null values, keys, etc.

DESCRIBE Student;

OR

DESC Student;
Example Table
CREATE TABLE Students (
    id INT,
    name VARCHAR(100),
    city VARCHAR(50)
);
Insert Data Into Table
Method 1: Insert Specific Columns
Syntax
INSERT INTO table_name(column1, column2)
VALUES(value1, value2);
Example
INSERT INTO Students(id, name)
VALUES(101, 'Rahul');
INSERT INTO Students(id, name)
VALUES(102, 'Ram');
INSERT INTO Students(id, name)
VALUES(103, 'Sham');
Important Note

When column names are specified:

INSERT INTO Students(id, name)
VALUES(101, 'Navin');

Only those mentioned columns are mandatory.

Insert Data Into All Columns
Syntax
INSERT INTO table_name
VALUES(value1, value2, value3);
Example
INSERT INTO Students
VALUES(101, 'Navin', 'Pune');

⚠️ Values must be provided in the same order as the table columns.

Insert Data Into Specific Columns
INSERT INTO Students(id, name)
VALUES(102, 'Navin');
Insert Multiple Rows At Once
Syntax
INSERT INTO table_name(col1, col2, col3)
VALUES
(value1, value2, value3),
(value4, value5, value6),
(value7, value8, value9);
Example
INSERT INTO Students(id, name, city)
VALUES
(101, 'Rahul', 'Pune'),
(102, 'Ram', 'Mumbai'),
(103, 'Sham', 'Delhi');
Insert Data From One Table To Another
Insert All Columns
Syntax
INSERT INTO target_table
SELECT *
FROM source_table;
Example
INSERT INTO Students_Backup
SELECT *
FROM Students;
Insert Specific Columns
Syntax
INSERT INTO target_table(col1, col2)
SELECT col1, col2
FROM source_table;
Example
INSERT INTO Student_New(name, age)
SELECT name, age
FROM Students;
Insert Rows Based on Condition
Syntax
INSERT INTO target_table
SELECT *
FROM source_table
WHERE condition;
Example
INSERT INTO Students
SELECT *
FROM Old_Students
WHERE age > 20;
Commands Covered
CREATE TABLE
CREATE TABLE IF NOT EXISTS
CREATE TABLE AS SELECT
SHOW TABLES
DESCRIBE
DESC
INSERT INTO
INSERT INTO ... VALUES
INSERT MULTIPLE ROWS
INSERT INTO ... SELECT
