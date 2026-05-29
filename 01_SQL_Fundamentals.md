# SQL Fundamentals

## What is SQL?

SQL (Structured Query Language) is the standard language used to communicate with relational databases. It allows users to store, retrieve, manage, and manipulate data efficiently.

SQL is a declarative language, meaning that you specify *what* data you want, and the database management system determines *how* to retrieve it.

### Advanced Definition

SQL is a domain-specific declarative programming language designed for managing, querying, and manipulating data stored in Relational Database Management Systems (RDBMS).

---

## History of SQL

- SQL concepts were based on the relational model proposed by Edgar F. Codd at IBM in 1970.
- The first version was known as SEQUEL (Structured English Query Language).
- Later, the name was shortened to SQL.

---

## Why SQL?

Before SQL and modern database systems, organizations relied on traditional file systems.

### Problems with Traditional File Systems

- Data redundancy
- Data inconsistency
- Difficult data access
- Slow retrieval process
- Limited concurrent access
- Poor backup and recovery mechanisms

SQL and DBMS were introduced to overcome these limitations.

---

## CRUD Operations

Most database operations fall into four categories:

| Operation | Description |
|------------|------------|
| Create | Insert new data |
| Read | Retrieve data |
| Update | Modify existing data |
| Delete | Remove data |

---

## What is a Database?

A database is an organized collection of structured data that can be stored, managed, and accessed efficiently.

### Example

A library stores thousands of books.

The books represent the data, while the organized collection of books represents a database.

---

## What is DBMS?

DBMS (Database Management System) is software that helps users create, manage, store, and retrieve data from databases.

### Examples of DBMS

- MySQL
- PostgreSQL
- Oracle Database
- Microsoft SQL Server
- SQLite
- IBM Db2

---

## Relationship Between Client, DBMS, and Database

```text
Client Application
        │
        ▼
      DBMS
        │
        ▼
    Database

The client communicates with the DBMS, and the DBMS interacts with the database.

How SQL Works
Write SQL Query
       │
       ▼
Send Query To Server
       │
       ▼
Execute Query
       │
       ▼
Return Result

SQL acts as a communication language between the user and the DBMS.

Important Note

SQL itself is not a database.

SQL is only the language used to communicate with a Relational Database Management System (RDBMS).

What is Data?

Data refers to raw and unprocessed facts and figures such as:

Numbers
Text
Images
Dates
Symbols

Data can be processed and analyzed to generate meaningful information.

Types of DBMS
1. Hierarchical DBMS

Data is organized in a tree-like structure.

2. Network DBMS

Data is connected using multiple relationships.

3. Relational DBMS (RDBMS)

Data is stored in tables and related through keys.

4. Cloud Database Systems

Databases hosted on cloud infrastructure.

5. NoSQL Databases

Designed for handling large-scale unstructured or semi-structured data.

Components of a DBMS

A DBMS requires the following components:

Hardware
Software
Data
Procedures
Database Access Language
Users
Relational Model

The relational model represents data in the form of relations (tables).

A relation consists of:

Rows (Tuples)
Columns (Attributes)

This model is based on relational algebra and relational calculus.

SQL Command Categories

SQL commands are broadly divided into:

DDL (Data Definition Language)

Used to define database structures.

Examples:

CREATE
ALTER
DROP
TRUNCATE
DML (Data Manipulation Language)

Used to modify data.

Examples:

INSERT
UPDATE
DELETE
DQL (Data Query Language)

Used to retrieve data.

Examples:

SELECT
DCL (Data Control Language)

Used to manage permissions.

Examples:

GRANT
REVOKE
TCL (Transaction Control Language)

Used to manage transactions.

Examples:

COMMIT
ROLLBACK
SAVEPOINT
Key Takeaways
SQL is the standard language for relational databases.
SQL is a declarative language.
SQL communicates with DBMS software.
Databases store organized data.
DBMS manages databases.
RDBMS stores data in tables.
SQL commands are categorized into DDL, DML, DQL, DCL, and TCL.
