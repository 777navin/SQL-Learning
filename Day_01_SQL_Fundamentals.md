# SQL Learning Journey

## What is SQL?

SQL (Structured Query Language) is the standard language used to communicate with relational databases. It helps users store, retrieve, manage, and manipulate data efficiently.

SQL is a declarative language, which means you tell the database what data you need, and the database decides how to retrieve it.

### Advanced Definition

SQL is a domain-specific declarative programming language designed for managing, querying, and manipulating data stored in Relational Database Management Systems (RDBMS).

---

# History of SQL

- In 1970, Edgar F. Codd at IBM introduced the Relational Model.
- SQL was initially called SEQUEL (Structured English Query Language).
- Later, the name was shortened to SQL.
- SQL became the standard language for relational databases.

---

# Why SQL Was Introduced

Before SQL and DBMS, organizations used traditional file systems to store information.

### Problems with Traditional File Systems

1. Data Redundancy
2. Data Inconsistency
3. Difficult Data Access
4. Slow Retrieval Process
5. Limited Multi-User Access
6. No Proper Backup and Recovery
7. Poor Data Management

SQL and DBMS were introduced to solve these problems.

---

# What is Data?

Data refers to raw and unorganized facts and figures.

Examples:

- Numbers
- Names
- Text
- Images
- Dates
- Symbols

Raw data can be processed and analyzed to generate meaningful information.

---

# What is a Database?

A Database is an organized collection of structured data that is stored electronically and can be accessed, managed, and updated efficiently.

### Example

Library = Database

Books = Data

A library stores thousands of books in an organized manner. Similarly, a database stores information in an organized format.

---

# What is DBMS?

DBMS (Database Management System) is software that allows users to create, manage, store, retrieve, and manipulate data within databases.

### Examples of DBMS

- MySQL
- PostgreSQL
- Oracle Database
- Microsoft SQL Server
- SQLite
- IBM Db2

---

# Relationship Between SQL, DBMS, and Database

Client Application
        │
        ▼
       SQL
        │
        ▼
       DBMS
        │
        ▼
    Database
Explanation
SQL is the language.
DBMS is the software.
Database is where the data is stored.
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

SQL acts as a communication bridge between users and the database.

Important Note

SQL is NOT a database.

SQL is only a language used to communicate with a Database Management System (DBMS).

CRUD Operations

CRUD represents the four basic operations performed on data.

Operation	Description
Create	Add new records
Read	Retrieve records
Update	Modify records
Delete	Remove records
Types of DBMS
1. Hierarchical DBMS

Data is organized in a tree-like structure.

Example
Company
 ├── HR
 ├── Finance
 └── IT
2. Network DBMS

Data is connected through multiple relationships.

A record can have multiple parent records.

3. Relational DBMS (RDBMS)

Data is stored in tables consisting of rows and columns.

Examples:

MySQL
PostgreSQL
Oracle
SQL Server
4. Cloud Databases

Databases hosted on cloud platforms.

Examples:

Amazon RDS
Google Cloud SQL
Azure SQL Database
5. NoSQL Databases

Designed for unstructured and semi-structured data.

Examples:

MongoDB
Cassandra
Redis
Components of a DBMS

A DBMS requires the following components:

1. Hardware

Physical devices such as servers, storage drives, and networking equipment.

2. Software

DBMS software that manages databases.

3. Data

Actual information stored in the database.

4. Procedures

Instructions and rules for using the database system.

5. Database Access Language

Languages used to communicate with databases, such as SQL.

6. Users

People who interact with the database.

Examples:

Database Administrator (DBA)
Developers
End Users
Relational Model

The Relational Model stores data in the form of relations (tables).

Each relation contains:

Rows

Rows are called Tuples.

Each row represents a single record.

Columns

Columns are called Attributes.

Each column represents a property of the data.

Example
Student_ID	Name	Age
101	John	20
102	Emma	21

Here:

Rows = Tuples
Columns = Attributes

The Relational Model is based on:

Relational Algebra
Relational Calculus
SQL Command Categories

SQL commands are divided into five major categories.

DDL (Data Definition Language)

Used to define and manage database structures.

Commands:

CREATE
ALTER
DROP
TRUNCATE
RENAME
DML (Data Manipulation Language)

Used to modify data stored in tables.

Commands:

INSERT
UPDATE
DELETE
DQL (Data Query Language)

Used to retrieve data.

Commands:

SELECT
DCL (Data Control Language)

Used to control user permissions.

Commands:

GRANT
REVOKE
TCL (Transaction Control Language)

Used to manage database transactions.

Commands:

COMMIT
ROLLBACK
SAVEPOINT
Database vs DBMS
Database	DBMS
Collection of data	Software used to manage data
Stores information	Manages information
Passive component	Active component
Example: Student Database	Example: MySQL
Key Interview Questions
What is SQL?

SQL is a standard language used to communicate with relational databases.

Is SQL a Programming Language?

SQL is a declarative and domain-specific language.

What is DBMS?

DBMS is software used to create, manage, and manipulate databases.

What is RDBMS?

RDBMS is a DBMS that stores data in tables using the relational model.

Difference Between Database and DBMS?

A database stores data, while a DBMS manages that data.

What are CRUD Operations?

Create, Read, Update, and Delete.

What are Tuples and Attributes?
Tuple = Row
Attribute = Column
Name the Types of DBMS.
Hierarchical DBMS
Network DBMS
Relational DBMS
Cloud Database
NoSQL Database
Summary
SQL stands for Structured Query Language.
SQL is used to communicate with databases.
SQL is a declarative language.
Database stores data.
DBMS manages databases.
RDBMS stores data in tables.
Rows are called Tuples.
Columns are called Attributes.
CRUD operations are Create, Read, Update, and Delete.
SQL commands are categorized into DDL, DML, DQL, DCL, and TCL.
SQL is a language, not a database.
