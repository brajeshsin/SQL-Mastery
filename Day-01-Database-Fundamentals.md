
# Day 01 --- Database Fundamentals

## Learning Objectives

By the end of this lesson, you should understand:

-   What is Data?
-   What is Information?
-   What is a Database?
-   Why do we need Databases?
-   File System vs Database
-   What is DBMS?
-   What is RDBMS?
-   What is SQL?
-   What is SQL Server?
-   SQL vs SQL Server
-   Basic Database Objects
-   Basic Database Architecture
-   Common Interview Questions

------------------------------------------------------------------------

# 1. What is Data?

**Data is a collection of raw facts, values, or observations that may
not have meaningful context by themselves.**

### Example

``` text
Brajesh
26
Noida
28000
```

These are raw values, so they are considered data.

### Real-World Example

In an e-commerce application, the following are examples of data:

``` text
Product Name
Product Price
Customer Name
Customer Email
Order Date
Payment Amount
```

------------------------------------------------------------------------

# 2. What is Information?

**Information is processed, organized, and meaningful data.**

### Example

Raw data:

``` text
Brajesh
26
Noida
28000
```

Processed information:

``` text
Name   : Brajesh
Age    : 26
City   : Noida
Salary : 28000
```

### Remember

``` text
Raw Data
    ↓
Processing / Organization
    ↓
Information
```

------------------------------------------------------------------------

# 3. What is a Database?

A **database is an organized collection of data that allows applications
to store, retrieve, update, and manage data efficiently.**

### Example

A library application may have:

``` text
LibraryDB
│
├── Books
├── Authors
├── Members
├── Categories
├── BookIssues
└── BookReturns
```

All these related data structures can be part of the same database.

------------------------------------------------------------------------

# 4. Why Do We Need a Database?

Modern applications can generate millions or even billions of records.

A database helps us with:

-   Data storage
-   Fast data retrieval
-   Data modification
-   Data organization
-   Data security
-   Data integrity
-   Relationships between data
-   Transactions
-   Concurrency
-   Backup and recovery
-   Performance optimization

### Real-World Example

A banking application may need to manage:

``` text
Customers
Accounts
Transactions
Loans
Payments
Branches
```

Managing this amount of related data using ordinary files would become
difficult and unreliable.

------------------------------------------------------------------------

# 5. File System vs Database

Before databases became widely used, applications commonly stored data
in files.

Example:

``` text
users.txt
orders.txt
payments.txt
```

As applications became larger, several problems appeared.

## Problems with File Systems

### 1. Data Duplication

The same customer information may exist in multiple files.

### 2. Difficult Searching

Finding specific records in large files can be inefficient.

### 3. Data Integrity Problems

It becomes difficult to ensure that data is always valid and consistent.

### 4. Concurrency Problems

Multiple users accessing and modifying the same data can cause
conflicts.

### 5. Security Problems

Fine-grained access control is difficult to implement using simple
files.

### 6. Transaction Problems

Operations involving multiple files may not be safely handled as a
single transaction.

## File System vs Database

  -----------------------------------------------------------------------
  File System                         Database
  ----------------------------------- -----------------------------------
  Suitable for simple data storage    Suitable for structured application
                                      data

  Searching can be difficult          Powerful query capabilities

  More duplication                    Better control over redundancy

  Limited relationships               Relationships between data

  Limited concurrency control         Concurrency control

  Limited transaction support         Transaction support

  Basic security                      Advanced security mechanisms

  Difficult data integrity management Constraints and integrity rules
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# 6. What is DBMS?

**DBMS stands for Database Management System.**

A DBMS is software used to create, store, retrieve, update, and manage
databases.

### Examples

``` text
Microsoft Access
SQLite
dBase
```

A DBMS acts as a layer between applications and stored data.

``` text
Application
     ↓
    DBMS
     ↓
   Database
```

------------------------------------------------------------------------

# 7. What is RDBMS?

**RDBMS stands for Relational Database Management System.**

An RDBMS organizes data primarily into **tables** and allows
relationships to be established between related data.

### Example

``` text
Customers
----------------
CustomerId
Name
Email

Orders
----------------
OrderId
CustomerId
OrderDate
Amount
```

`CustomerId` can be used to connect customers with their orders.

### Common RDBMS Examples

-   Microsoft SQL Server
-   MySQL
-   PostgreSQL
-   Oracle Database
-   MariaDB

------------------------------------------------------------------------

# 8. DBMS vs RDBMS

  -----------------------------------------------------------------------
  DBMS                                RDBMS
  ----------------------------------- -----------------------------------
  General database management system  Relational database management
                                      system

  May use different data storage      Primarily uses relational tables
  models                              

  Relational features are not its     Relationships are a core concept
  defining requirement                

  Can be suitable for simpler systems Commonly used for structured
                                      enterprise applications

  Example: SQLite can be used as a    Examples: SQL Server, PostgreSQL,
  lightweight database system         Oracle
  -----------------------------------------------------------------------

> **Note:** The exact DBMS/RDBMS classification can vary by product and
> historical terminology. In interviews, focus on the relational model,
> tables, keys, constraints, and relationships.

------------------------------------------------------------------------

# 9. What is SQL?

**SQL stands for Structured Query Language.**

SQL is a language used to interact with relational databases.

We can use SQL to:

-   Create database structures
-   Insert data
-   Retrieve data
-   Update data
-   Delete data
-   Control access
-   Manage transactions

### Example

``` sql
SELECT *
FROM Employees;
```

This query retrieves data from the `Employees` table.

------------------------------------------------------------------------

# 10. SQL is Declarative

SQL is primarily a **declarative language**.

We usually specify **what result we want**, rather than describing every
step the database engine must perform.

### Example

``` sql
SELECT Name
FROM Employees
WHERE Salary > 50000;
```

We specify the required result.

The database engine decides how to execute the query.

------------------------------------------------------------------------

# 11. What is SQL Server?

**SQL Server is Microsoft's relational database management system
(RDBMS).**

SQL Server provides features for:

-   Database management
-   Data storage
-   Query execution
-   Transactions
-   Security
-   Indexing
-   Backup and recovery
-   Stored procedures
-   Functions
-   Views
-   Triggers
-   Performance optimization

SQL Server uses **T-SQL (Transact-SQL)**, Microsoft's extension of SQL.

------------------------------------------------------------------------

# 12. SQL vs SQL Server

This is an important interview distinction.

``` text
SQL
↓
Language

SQL Server
↓
Microsoft's RDBMS
```

### Example

``` sql
SELECT *
FROM Users;
```

The above is a SQL/T-SQL query.

SQL Server is the database management system that can execute it.

### Interview Answer

> SQL is a language used to interact with relational databases, whereas
> SQL Server is Microsoft's relational database management system that
> stores and manages databases and executes SQL queries.

------------------------------------------------------------------------

# 13. Basic Database Objects

A SQL Server database can contain different types of objects.

## Table

Stores structured data.

``` text
Employees
-----------------------
Id | Name | Department
```

## View

A saved query that presents data as a virtual table.

## Stored Procedure

A reusable collection of SQL statements.

## Function

Reusable logic that returns a value or table depending on its type.

## Trigger

Logic that executes automatically in response to specific database
events.

## Index

A data structure used to improve data retrieval performance.

## Constraint

Rules that help maintain data integrity.

Examples:

``` text
PRIMARY KEY
FOREIGN KEY
UNIQUE
NOT NULL
CHECK
DEFAULT
```

These objects will be studied in detail in later phases.

------------------------------------------------------------------------

# 14. Basic Database Architecture

In a typical backend application:

``` text
Frontend
   ↓
Backend API
   ↓
ORM / SQL Queries
   ↓
SQL Server
   ↓
Database
```

For an ASP.NET Core application:

``` text
React / Next.js
       ↓
ASP.NET Core Web API
       ↓
Entity Framework Core / T-SQL
       ↓
SQL Server
       ↓
Database
```

This is an important connection between SQL and backend development.

------------------------------------------------------------------------

# 15. Real-World Example --- Library Management System

Suppose we are designing a library system.

The application may need to manage:

``` text
Books
Authors
Members
Categories
Book Issues
Book Returns
Publishers
```

The database could look conceptually like:

``` text
LibraryDB
│
├── Books
├── Authors
├── Members
├── Categories
├── BookIssues
├── BookReturns
└── Publishers
```

Later, we will learn how to convert this requirement into:

``` text
Entities
    ↓
Tables
    ↓
Columns
    ↓
Keys
    ↓
Relationships
    ↓
Constraints
```

------------------------------------------------------------------------

# 16. Common Mistakes

### Mistake 1: SQL and SQL Server are the same

Incorrect.

``` text
SQL        = Language
SQL Server = RDBMS
```

### Mistake 2: A database is the same as a table

Incorrect.

A database can contain multiple tables and other database objects.

``` text
Database
├── Table
├── Table
├── View
├── Procedure
└── Index
```

### Mistake 3: SQL is only used to retrieve data

Incorrect.

SQL can also be used for creating structures, inserting, updating,
deleting, controlling access, and working with transactions.

------------------------------------------------------------------------

# 17. Interview Questions & Answers

## Q1. What is data?

**Answer:**

Data is a collection of raw facts, values, or observations that may not
have meaningful context by themselves.

------------------------------------------------------------------------

## Q2. What is information?

**Answer:**

Information is processed, organized, and meaningful data.

------------------------------------------------------------------------

## Q3. What is a database?

**Answer:**

A database is an organized collection of data that allows applications
to store, retrieve, update, and manage data efficiently.

------------------------------------------------------------------------

## Q4. Why do we need databases?

**Answer:**

Databases allow us to efficiently store and manage large amounts of data
while providing features such as querying, security, data integrity,
transactions, concurrency, and backup and recovery.

------------------------------------------------------------------------

## Q5. What is DBMS?

**Answer:**

DBMS stands for Database Management System. It is software used to
create, store, retrieve, update, and manage databases.

------------------------------------------------------------------------

## Q6. What is RDBMS?

**Answer:**

RDBMS stands for Relational Database Management System. It organizes
data into related tables and supports relationships and relational
constraints.

------------------------------------------------------------------------

## Q7. Give examples of RDBMS.

**Answer:**

Common examples include:

-   SQL Server
-   MySQL
-   PostgreSQL
-   Oracle
-   MariaDB

------------------------------------------------------------------------

## Q8. What is SQL?

**Answer:**

SQL stands for Structured Query Language. It is used to interact with
relational databases for querying and manipulating data and defining
database structures.

------------------------------------------------------------------------

## Q9. Is SQL a programming language?

**Answer:**

SQL is primarily a declarative database language rather than a
general-purpose programming language. It describes what data or result
is required, while the database engine determines how to execute the
request.

------------------------------------------------------------------------

## Q10. What is SQL Server?

**Answer:**

SQL Server is Microsoft's relational database management system used to
store, manage, query, secure, and process relational data.

------------------------------------------------------------------------

## Q11. What is the difference between SQL and SQL Server?

**Answer:**

SQL is a language used to interact with relational databases, while SQL
Server is Microsoft's RDBMS that manages databases and executes SQL
queries.

------------------------------------------------------------------------

## Q12. What is the difference between a database and a table?

**Answer:**

A database is a collection of related data and database objects, while a
table is one database object used to store data in rows and columns.

------------------------------------------------------------------------

## Q13. What is a relational database?

**Answer:**

A relational database stores data in tables and represents relationships
between related data using keys and constraints.

------------------------------------------------------------------------

## Q14. Why is a database preferred over simple files for large applications?

**Answer:**

Databases provide efficient querying, indexing, transactions,
concurrency control, security, data integrity, relationships, and backup
and recovery capabilities.

------------------------------------------------------------------------

## Q15. Can multiple applications access the same database?

**Answer:**

Yes. Multiple applications can access the same database, provided they
have appropriate permissions and the database system handles concurrency
and transactions correctly.

------------------------------------------------------------------------

# 18. Practice Questions

Answer these without looking at the notes:

1.  What is the difference between data and information?
2.  What is a database?
3.  Why is a database better than a simple file system for large
    applications?
4.  What does DBMS stand for?
5.  What does RDBMS stand for?
6.  Give five examples of RDBMS.
7.  What is SQL?
8.  What is SQL Server?
9.  What is the difference between SQL and SQL Server?
10. Name five common database objects.
11. What is a relational database?
12. Why are relationships important in a database?

------------------------------------------------------------------------

# 19. Assignment

## Part A --- Theory

Explain in your own words:

1.  Data
2.  Information
3.  Database
4.  DBMS
5.  RDBMS
6.  SQL
7.  SQL Server

## Part B --- Real-World Observation

Identify 5 applications you use regularly.

For each application, identify possible data that could be stored in its
database.

Example:

  Application   Possible Data
  ------------- -----------------------------------
  E-commerce    Users, Products, Orders, Payments
  Banking       Customers, Accounts, Transactions
  Library       Books, Members, Issues, Returns

------------------------------------------------------------------------

# 20. Mini Database Design Exercise

## Library Management System

Identify the entities required for a library system.

Think about:

-   Books
-   Authors
-   Members
-   Categories
-   Publishers
-   Book Issues
-   Book Returns

### Your Task

Do not create SQL tables yet.

First identify:

1.  Entities
2.  What information each entity should contain
3.  Which entities may be related

Example:

``` text
Book
- Book Name
- ISBN
- Publication Year
```

We will convert this into a proper relational database design in later
lessons.

------------------------------------------------------------------------

# 21. Key Takeaways

``` text
Data
    ↓
Raw facts and values

Information
    ↓
Processed and meaningful data

Database
    ↓
Organized collection of data

DBMS
    ↓
Software that manages databases

RDBMS
    ↓
Database management system based on the relational model

SQL
    ↓
Language used to interact with relational databases

SQL Server
    ↓
Microsoft's RDBMS
```

### Golden Interview Statement

> **SQL is the language, SQL Server is Microsoft's RDBMS, and a database
> is an organized collection of data managed by a database management
> system.**

------------------------------------------------------------------------

# Day 1 Status

-   [x] Database Fundamentals
-   [x] Data vs Information
-   [x] Database
-   [x] File System vs Database
-   [x] DBMS
-   [x] RDBMS
-   [x] SQL
-   [x] SQL Server
-   [x] SQL vs SQL Server
-   [x] Database Objects
-   [x] Database Architecture
-   [x] Interview Questions
-   [x] Practice Questions
-   [x] Assignment
-   [x] Mini Design Exercise
-   [x] Key Takeaways

------------------------------------------------------------------------

## Next

**Day 02 --- Tables, Rows, Columns, Records & Data Types**
