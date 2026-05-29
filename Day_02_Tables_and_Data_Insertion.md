DAY 2 - TABLES & INSERT OPERATIONS

=================================================
WHAT IS A TABLE?
=================================================

A Table is a collection of related data organized in rows and columns
within a database.

Row    -> Individual Record
Column -> Attribute / Field

Example:

+-----+--------+--------+
| ID  | Name   | City   |
+-----+--------+--------+
| 101 | Navin  | Pune   |
| 102 | Rahul  | Mumbai |
+-----+--------+--------+

=================================================
CREATE TABLE
=================================================

Syntax:

CREATE TABLE table_name (
    column1 datatype(size),
    column2 datatype(size),
    column3 datatype(size)
);

Example:

CREATE TABLE Student (
    id INT,
    name VARCHAR(100)
);

Example:

CREATE TABLE Student (
    name VARCHAR(100),
    age INT
);

=================================================
CREATE TABLE IF NOT EXISTS
=================================================

Syntax:

CREATE TABLE IF NOT EXISTS Student (
    id INT,
    name VARCHAR(100)
);

=================================================
CREATE TABLE AS SELECT
(Copy Existing Table)
=================================================

Syntax:

CREATE TABLE new_table AS
SELECT column1, column2
FROM existing_table;

Example:

CREATE TABLE Student_Backup AS
SELECT *
FROM Student;

=================================================
SHOW ALL TABLES
=================================================

SHOW TABLES;

=================================================
DESCRIBE TABLE
=================================================

Used to print table structure.

Syntax:

DESCRIBE table_name;

OR

DESC table_name;

Example:

DESCRIBE Student;

DESC Student;

=================================================
EXAMPLE TABLE
=================================================

CREATE TABLE Students (
    id INT,
    name VARCHAR(100),
    city VARCHAR(50)
);

=================================================
INSERT DATA INTO TABLE
=================================================

Method 1: Insert Specific Columns

Syntax:

INSERT INTO table_name(column1, column2)
VALUES(value1, value2);

Example:

INSERT INTO Students(id, name)
VALUES(101, 'Rahul');

INSERT INTO Students(id, name)
VALUES(102, 'Ram');

INSERT INTO Students(id, name)
VALUES(103, 'Sham');

-------------------------------------------------

Important:

When column names are specified:

INSERT INTO Students(id, name)
VALUES(101, 'Navin');

Only mentioned columns are compulsory.

=================================================
INSERT INTO ALL COLUMNS
=================================================

Syntax:

INSERT INTO table_name
VALUES(value1, value2, value3);

Example:

INSERT INTO Students
VALUES(101, 'Navin', 'Pune');

Note:
Values must follow the same order as table columns.

=================================================
INSERT INTO SPECIFIC COLUMNS
=================================================

Syntax:

INSERT INTO Students(id, name)
VALUES(102, 'Navin');

=================================================
INSERT MULTIPLE ROWS
=================================================

Syntax:

INSERT INTO table_name(col1, col2, col3)
VALUES
(value1, value2, value3),
(value4, value5, value6),
(value7, value8, value9);

Example:

INSERT INTO Students(id, name, city)
VALUES
(101, 'Rahul', 'Pune'),
(102, 'Ram', 'Mumbai'),
(103, 'Sham', 'Delhi');

=================================================
INSERT DATA FROM ONE TABLE TO ANOTHER
=================================================

Used to copy data from one table into another table.

-------------------------------------------------
1. INSERT ALL COLUMNS
-------------------------------------------------

Syntax:

INSERT INTO target_table
SELECT *
FROM source_table;

Example:

INSERT INTO Students_Backup
SELECT *
FROM Students;

-------------------------------------------------
2. INSERT SPECIFIC COLUMNS
-------------------------------------------------

Syntax:

INSERT INTO target_table(col1, col2)
SELECT col1, col2
FROM source_table;

Example:

INSERT INTO Student_New(name, age)
SELECT name, age
FROM Students;

-------------------------------------------------
3. INSERT ROWS USING CONDITION
-------------------------------------------------

Syntax:

INSERT INTO target_table
SELECT *
FROM source_table
WHERE condition;

Example:

INSERT INTO Students
SELECT *
FROM Old_Students
WHERE age > 20;

=================================================
COMMANDS COVERED
=================================================

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

=================================================
END OF DAY 2
TABLES & INSERT OPERATIONS
=================================================
