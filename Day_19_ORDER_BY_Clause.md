# Day 19: ORDER BY Clause in SQL

## Introduction

The **ORDER BY** clause is used to **sort the result set** returned by a `SELECT` query.

By default, SQL returns rows in **ascending (ASC)** order. If you want the data in reverse order, use **DESC (Descending)**.

The `ORDER BY` clause makes your output more readable and organized. It is commonly used in reports, dashboards, and applications where data needs to be displayed alphabetically or numerically.

---

# Why Do We Use ORDER BY?

Suppose a table contains hundreds or thousands of records.

Without sorting:

- Data appears in random order.
- Finding highest marks becomes difficult.
- Finding latest records is harder.
- Reports look unorganized.

Using `ORDER BY` solves this problem by arranging the records according to one or more columns.

---

# Database Setup Used

## Create Database

```sql
CREATE DATABASE student_db;
```

## Use Database

```sql
USE student_db;
```

## Create Table

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

## Insert Data

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

## Output

| id | name | age | city | course | marks |
|----|------|-----|--------|---------|-------|
|101|Rahul|21|Pune|BCA|85|
|102|Navin|22|Pune|BCA|90|
|103|Dikshi|21|Mumbai|BTech|95|
|104|Amit|23|Delhi|BCA|70|
|105|Priya|22|Mumbai|BCom|88|
|106|Rohit|20|Pune|BTech|76|
|107|Sneha|21|Delhi|BCA|92|
|108|Neha|22|Mumbai|BCom|80|

---

# Syntax

## Ascending Order

```sql
SELECT column_name
FROM table_name
ORDER BY column_name;
```

or

```sql
SELECT column_name
FROM table_name
ORDER BY column_name ASC;
```

---

## Descending Order

```sql
SELECT column_name
FROM table_name
ORDER BY column_name DESC;
```

---

# Example 1 : Sort Students by Marks (Ascending)

## Query

```sql
SELECT *
FROM students
ORDER BY marks;
```

## Output

|Name|Marks|
|----|-----|
|Amit|70|
|Rohit|76|
|Neha|80|
|Rahul|85|
|Priya|88|
|Navin|90|
|Sneha|92|
|Dikshi|95|

### Explanation

Since no order is mentioned, SQL automatically uses **ASC**.

Smallest marks appear first.

---

# Example 2 : Sort Students by Marks (Descending)

## Query

```sql
SELECT *
FROM students
ORDER BY marks DESC;
```

## Output

|Name|Marks|
|----|-----|
|Dikshi|95|
|Sneha|92|
|Navin|90|
|Priya|88|
|Rahul|85|
|Neha|80|
|Rohit|76|
|Amit|70|

### Explanation

Using **DESC** sorts values from highest to lowest.

---

# Example 3 : Sort by Name Alphabetically

## Query

```sql
SELECT *
FROM students
ORDER BY name;
```

## Output

|Name|
|----|
|Amit|
|Dikshi|
|Navin|
|Neha|
|Priya|
|Rahul|
|Rohit|
|Sneha|

### Explanation

Text values are sorted alphabetically from A to Z.

---

# Example 4 : Sort by Age (Highest First)

## Query

```sql
SELECT *
FROM students
ORDER BY age DESC;
```

## Output

|Name|Age|
|----|---|
|Amit|23|
|Navin|22|
|Priya|22|
|Neha|22|
|Rahul|21|
|Sneha|21|
|Dikshi|21|
|Rohit|20|

### Explanation

Older students appear before younger students.

---

# Example 5 : Sort Using Multiple Columns

## Query

```sql
SELECT *
FROM students
ORDER BY city ASC, marks DESC;
```

## Output

|City|Name|Marks|
|----|----|-----|
|Delhi|Sneha|92|
|Delhi|Amit|70|
|Mumbai|Dikshi|95|
|Mumbai|Priya|88|
|Mumbai|Neha|80|
|Pune|Navin|90|
|Pune|Rahul|85|
|Pune|Rohit|76|

### Explanation

SQL first sorts by **city**.

If two students belong to the same city, it sorts them by **marks (DESC)**.

---

# Example 6 : ORDER BY Column Position

## Query

```sql
SELECT id,name,marks
FROM students
ORDER BY 3 DESC;
```

### Output

Rows are sorted using the third selected column (**marks**).

### Explanation

Here,

```
1 → id
2 → name
3 → marks
```

So SQL sorts by marks.

Although valid, using column names is recommended for better readability.

---

# Example 7 : ORDER BY with WHERE

## Query

```sql
SELECT *
FROM students
WHERE city='Pune'
ORDER BY marks DESC;
```

## Output

|Name|City|Marks|
|----|----|-----|
|Navin|Pune|90|
|Rahul|Pune|85|
|Rohit|Pune|76|

### Explanation

First SQL filters Pune students.

Then it sorts them by marks.

---

# Example 8 : ORDER BY with LIMIT

## Query

```sql
SELECT *
FROM students
ORDER BY marks DESC
LIMIT 3;
```

## Output

|Name|Marks|
|----|-----|
|Dikshi|95|
|Sneha|92|
|Navin|90|

### Explanation

Returns the top 3 students based on marks.

---

# ORDER BY with Different Data Types

|Data Type|Sorting|
|----------|-------|
|Numbers|Smallest → Largest|
|Text|Alphabetical|
|Date|Oldest → Newest|
|NULL Values|Depends on SQL Database|

---

# Important Notes

- `ORDER BY` is always written after `WHERE`.
- `ASC` is the default sorting order.
- `DESC` sorts in reverse order.
- Multiple columns can be sorted together.
- Sorting large datasets may reduce query performance.
- Use indexes for faster sorting on large tables.
- `ORDER BY` works with numbers, text, dates, and expressions.
- Can be combined with `LIMIT`, `GROUP BY`, `HAVING`, and `WHERE`.

---

# Common Errors

## Error 1

### Wrong

```sql
SELECT *
ORDER BY marks
FROM students;
```

### Correct

```sql
SELECT *
FROM students
ORDER BY marks;
```

### Reason

`ORDER BY` must come after the `FROM` clause.

---

## Error 2

### Wrong

```sql
SELECT *
FROM students
ORDER marks;
```

### Correct

```sql
SELECT *
FROM students
ORDER BY marks;
```

### Reason

Always write the keyword `BY`.

---

## Error 3

### Wrong

```sql
SELECT *
FROM students
ORDER BY salary;
```

### Correct

```sql
SELECT *
FROM students
ORDER BY marks;
```

### Reason

The column must exist in the table.

---

# Execution Order

Although we write:

```sql
SELECT *
FROM students
WHERE city='Pune'
ORDER BY marks DESC;
```

SQL executes it internally as:

```text
1. FROM
2. WHERE
3. SELECT
4. ORDER BY
```

---

# Real-World Examples

### Highest Salary Employees

```sql
SELECT *
FROM employees
ORDER BY salary DESC;
```

---

### Latest Orders

```sql
SELECT *
FROM orders
ORDER BY order_date DESC;
```

---

### Products A-Z

```sql
SELECT *
FROM products
ORDER BY product_name;
```

---

### Cheapest Products

```sql
SELECT *
FROM products
ORDER BY price;
```

---

# Interview Questions

## Q1. What is ORDER BY?

### Answer

It is used to sort records returned by a SELECT statement.

---

## Q2. What is the default sorting order?

### Answer

Ascending (ASC).

---

## Q3. What is the difference between ASC and DESC?

### Answer

ASC sorts from smallest to largest or A-Z.

DESC sorts from largest to smallest or Z-A.

---

## Q4. Can ORDER BY sort multiple columns?

### Answer

Yes.

Example:

```sql
ORDER BY city ASC, marks DESC;
```

---

## Q5. Can ORDER BY be used without WHERE?

### Answer

Yes.

WHERE is optional.

---

## Commands Covered

```sql
ORDER BY

ORDER BY ASC

ORDER BY DESC

ORDER BY column1,column2

ORDER BY with WHERE

ORDER BY with LIMIT

ORDER BY using Column Position
```

---

# Summary

- `ORDER BY` sorts query results.
- Default sorting is **Ascending (ASC)**.
- Use **DESC** for reverse order.
- Can sort numbers, text, dates, and multiple columns.
- Often used with `WHERE`, `LIMIT`, and `GROUP BY`.
- Makes reports easier to read and analyze.
- Essential SQL clause used in almost every real-world project.
