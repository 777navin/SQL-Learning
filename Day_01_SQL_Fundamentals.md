# Day 1: SQL Fundamentals

## Introduction

SQL (Structured Query Language) is the standard language used to communicate with relational databases. It is used to store, retrieve, manage, and manipulate data efficiently. SQL is a declarative language, meaning users specify what data they need, and the database system determines how to retrieve it.

This topic also covers the basics of Databases, DBMS, RDBMS, SQL History, CRUD Operations, Types of DBMS, and the Relational Model.

---

## Syntax

```sql
-- SQL is used to communicate with databases

SELECT * FROM table_name;
```

---

## Example

```sql
SELECT 'Hello SQL';
```

---

## Output

```text
Hello SQL
```

The query returns a simple string value.

---

## Important Notes

* SQL stands for Structured Query Language.
* SQL is a declarative language.
* SQL is not a database; it is a language used to communicate with databases.
* SQL was originally called SEQUEL.
* Edgar F. Codd introduced the Relational Model in 1970.
* SQL works mainly with Relational Database Management Systems (RDBMS).
* Rows are called Tuples.
* Columns are called Attributes.

---

## Common Errors

### Error 1

Confusing SQL with DBMS.

**Wrong Understanding**

```text
SQL = Database
```

**Correct Understanding**

```text
SQL = Language
DBMS = Software
Database = Data Storage
```

### Error 2

Confusing Database and DBMS.

**Database**

Stores data.

**DBMS**

Manages databases and provides access to data.

---

## Interview Questions

### Q1. What is SQL?

SQL (Structured Query Language) is a standard language used to communicate with relational databases for storing, retrieving, updating, and managing data.

### Q2. Is SQL a Programming Language?

SQL is a domain-specific declarative language designed for database operations.

### Q3. What was SQL originally called?

SQL was originally called SEQUEL (Structured English Query Language).

### Q4. Who introduced the Relational Model?

Edgar F. Codd introduced the Relational Model at IBM in 1970.

### Q5. What is a Database?

A database is an organized collection of structured data.

### Q6. What is DBMS?

A Database Management System (DBMS) is software used to create, manage, store, and retrieve data from databases.

### Q7. What is RDBMS?

An RDBMS (Relational Database Management System) stores data in tables consisting of rows and columns.

### Q8. What are CRUD Operations?

CRUD stands for:

* Create
* Read
* Update
* Delete

### Q9. What are Tuples and Attributes?

* Tuple = Row
* Attribute = Column

### Q10. Name some popular DBMS software.

* MySQL
* PostgreSQL
* Oracle Database
* Microsoft SQL Server
* SQLite
* IBM Db2

---

## Commands Covered

No major SQL commands were covered in this topic.

Only introductory syntax:

```sql
SELECT 'Hello SQL';
```

---

## Summary

In this lesson, we learned the fundamentals of SQL, including its history, purpose, CRUD operations, databases, DBMS, RDBMS, types of DBMS, relational model concepts, and the role of SQL as a language for communicating with databases. This forms the foundation for all future SQL topics.
