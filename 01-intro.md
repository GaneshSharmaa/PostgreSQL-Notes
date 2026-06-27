# SQL Database

### What is Database?

A **database** is simply a collection of organized data that can be easily accessed, managed, and updated.

Think of it like a digital version of a well-organized notebook, where each page has information written in a structured way so that you can search, update, and retrieve it easily.

In more technical terms:

- It **stores data** electronically.
- The data is organized in **tables** (like Excel sheets with rows and columns).
- You can *query* the data using a language (usually SQL) to read, insert, update, or delete the data.
- The database system ensures **consistency**, **reliability**, and **security** of the data.

Example, let's say you're building an app to store information about students:

| Student_ID | Name   | Age | Grade |
| ---        | ---    | --- | ---   |
| 1          | Akarsh | 20  | A     |
| 2          | Anjali | 21  | B     |
| 3          | Raj    | 22  | A     |

This table is stored inside a database, and you can ask the database.

- Show me all students with grade A.
- Add a new student.
- Update Anjali's age.
- Delete Raj's record.

----

### What is RDBMS?

RDBMS stands for Relational Database Management System.

Relational → Data is organized into tables (which are related to each other)

Database → A collection of structured data.

Management System → Software that allows you to create, read, update, and delete data (using SQL).

An RDBMS is software that helps you store data in tables, relate them to each other, and perform operations on them using SQL.

Key features of RDBMS:

1. Data is stored in tables (relations)
    - Each table has rows and columns (like an Excel sheet).
2. Relationships between tables
    - Example
        - You have a Students table
        - You have a Courses table
        - You can link them with an Enrollments table.

Examples of RDBMS:

- PostgreSQL
- MySQL
- SQLite
- Oracle Database
- SQL Server

----

### Why PostgreSQL?

- Open source
- Most feature-rich and powerful
- Supports complex queries, joins, CTEs, window functions
- ACID compliant
- Highly extensible (you can add your own data types, operators, etc.)
- Support for NoSQL features also (JSONB, hstore)
- Used for enterprise-grade applications

----

### What is Important in this Databases?

**Database:**

- A _database_ is like a big container that stores all your data.
- Inside 1 PostgreSQL server, you can create multiple databases.
- Each database is isolated — data in one database is not mixed with another.

**Schema**

- Inside a database, you can organize objects using _schemas_.
- Think of a schema as a folder — it helps organize your tables, views, functions, etc.
- By default, every PostgreSQL database has a schema called public.

**Tables**

- A _table_ is the main place where data is stored.
- Think of a table like an _Excel sheet_ — rows and columns.
- Each table has:
    - columns → define the type of data (name, age, salary)
    - rows → each record (one person, one product, one order)

----

### Connecting to PostgreSQL

```bash
psql -U postgres
```

where, `postgres` is the admin/username.

----

### Creating a new database

For creating a new database, on terminal after connecting to the database, you can type:

```sql
CREATE DATABASE new_db;
```

Also, if you're using **_pgadmin_** then you can write `CREATE new_db`.

----

### Deleting a database

For deleting a database, on terminal you can write query like:

```sql
DROP DATABASE new_db;
```

----

### Basic Commands

In PostgreSQL, \d is a psql meta-command that means describe.

What it shows:

1. `\d` with no argument: lists tables, views, sequences, and indexes.
2. `\d table_name`: shows that table’s columns, types, indexes, constraints.
3. It is like a quick schema inspection command inside the psql terminal.

Most useful psql slash commands:

1. `\l`: list databases
2. `\c dbname`: connect to a database
3. `\dt`: list tables
4. `\dv`: list views
5. `\ds`: list sequences
6. `\di`: list indexes
7. `\dn`: list schemas
8. `\d object_name`: describe table/view/index/etc.
9. `\d+`: more detailed description
10. `\df`: list functions
11. `\du`: list roles/users
12. `\x`: expanded output on/off
13. `\timing`: query timing on/off
14. `\i file.sql`: run SQL file
15. `\o file.txt`: send output to file
16. `\conninfo`: show current connection info
17. `\password`: change user password
18. `\q`: quit psql
19. `\?`: help for slash commands
20. `\h`: help for SQL command syntax

----

### CRUD Operations

**Connecting to a database**

```sql
\c new_db;
```

**Creating a table into a database**

We're creating a new table `students` in the database `new_db`.

```sql
CREATE TABLE students(
    student_id INT UNIQUE,
    name CHAR(50),
    age INT,
    grade CHAR(1)
)
```

Here, you're creating the table and making 4 columns — `student_id`, `name`, `age`, and `grade`, and after that you specifically mention their data types.

**Inserting data into the table**

```sql
INSERT INTO students(name, age, grade)
VALUES ('Ganesh', 22, 'A'),
       ('Simran', 21, 'A'),
       ('Samira', 22, 'B');
```

**Reading the table**

```sql
SELECT * FROM students;
```

This will display all the columns of your data.

And, if you want to only display a specific column then, you can provide the name of that column.

```sql
SELECT name FROM students;
```

Now, this query will only display the column '_name_'.

**Updating the values**

Let's say we want to update the age of _Simran_ to 23.

```sql
UPDATE students
SET age = 23
WHERE name = 'Simran';
```

**Deleting the values**

Let's say we want to delete the record of _Kailash_, then:

```sql
DELETE FROM STUDENTS
WHERE NAME = 'Kailash';
```

**Deleting table**

If you want to delete a table, then:

```sql
DROP TABLE NUMBERS;
```

----

### WHERE Clause

`WHERE` clause is used to filter rows according to the condition provided.

For example, displaying people who are more than age of 25:

```sql
SELECT * FROM STUDENTS
WHERE AGE > 25;
```

