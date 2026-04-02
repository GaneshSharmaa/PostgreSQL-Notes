# PostgreSQL Notes

### How to run PostgreSQL by using Docker

First, go to the official _Docker Image_ page of **_PostgreSQL_**, there pull the image and then make a _Docker Container_ of that image.

Following are the environment variables that you'll need to specify:

1. Container name
2. Host port
3. Host path
4. Container path
5. POSTGRES_PASSWORD
6. POSTGRES_USER
7. POSTGRES_DB

Always, make sure that the folder you specify in `host path` is empty or else the Docker container won't run.\
And, `host path` and `container path` isn't mandatory, but it is always a best practice to add them, because this prevent the data to wiped off when you delete the container, or use an another image for accessing the container (upgrade to a new version).

After the container is made so to access the _PostgreSQL_ run this command in terminal:

```bash
docker exec -it postgre-db psql -U postgre-ganesh -d postgre-db
```

The first, `postgre-db` is the _container name_, `-U` represents _username_ which is `postgre-ganesh` and `-d` represent _database name_ which is `postgre-db`.

----

All the statements should end with a semi-colon, this tell that the statement ended.

### To view all the databases:
```sql
SELECT DATNAME FROM PG_DATABASE;
```

Another method in command line:
```bash
\l
```

### To view all the tables in a database:
```bash
\dt
```

### To create a new database:

```sql
CREATE DATABASE DB_NAME;
```

### To change the database:
```sql
\c postgre-db;
```

`postgre-db` is the name of the database, that I want to change to.

### To delete a database:
```sql
DROP DATABASE postgres;
```

`postgres` is the name of the database, that I want to delete.

----

### CRUD Operation

CRUD is simply short for create, read, update, and delete.

----

### Table

A table is a collection of related data held in a table format within a database.

### Creating a new table:

```sql
CREATE TABLE person(
    ID INT,
    NAME VARCHAR(100),
    AGE INT CHECK(AGE BETWEEN 1 AND 100),
    CITY VARCHAR(100),
    SALARY NUMERIC,
    JOB VARCHAR(100)
)
```

### Adding data to the table:

```sql
INSERT INTO PERSON(ID, NAME, AGE, CITY, SALARY, JOB)
VALUES(101, 'RAJU', 24, 'DELHI', 80000, 'JUNIOR SWE'),
      (102, 'PRIYA', 34, 'MUMBAI', 67000, 'HAIR STYLIST'),
      (103, 'ESHA', 45, 'BENGALURU', 40000, 'TEACHER'),
      (104, 'JAY', 32, 'NOIDA', 95000, 'CHARTED ACCOUNTANT');
```

You don't need to write the column name in the table name, if you're passing the values in sequence and they're also equal to the columns.

```sql
INSERT INTO PERSON
VALUES(101, 'RAJU', 24, 'DELHI', 80000, 'JUNIOR SWE'),
      (102, 'PRIYA', 34, 'MUMBAI', 67000, 'HAIR STYLIST');
```

Since, you're always passing the values in sequence and values being equal to the columns.

### Reading the data from the table:

```sql
SELECT * FROM PERSON;
```

### Reading only one column from the table:

```sql
SELECT NAME FROM PERSON;
```

### Reading multiple columns from the table:

```sql
SELECT NAME, AGE, CITY FROM PERSON;
```

### Updating the data in the table:

Let's say Manoj shifted to Surat from Ahemdabad.

```sql
UPDATE PERSON
SET CITY = 'SURAT'
WHERE ID = 110;
```

### Deleting the data from the table:

```sql
DELETE FROM PERSON
WHERE NAME = 'RAJU';
```

----

### Datatypes

An attribute that specifies the type of data in a column of our database table.

Most widely used datatypes are:

| Datatype | How they're specified            |
| ----     | ----                             |
| Numeric  | `INT` `DOUBLE` `FLOAT` `DECIMAL` |
| String   | `VARCHAR`                        |
| Date     | `DATE`                           |
| Boolean  | `BOOLEAN`                        |

----

### Constraints

A constraint in PostgreSQL is a rule applied to a column.

**Primary key**
- The PRIMARY KEY constraint uniquely identifies each record in a table.
- Primary keys must contain UNIQUE values, and cannot contain NULL values.
- A table can have only ONE primary key.

Following are some constraints that we mostly use:

- NOT NULL
- Default
- Serial
- Unique


**NOT NULL constraint:**

```sql
CREATE TABLE CUSTOMERS(
      ID INT NOT NULL,
      NAME VARCHAR(100) NOT NULL
);
```

**DEFAULT values constraint:**

```sql
CREATE TABLE CUSTOMERS(
      ACC_NO INT PRIMARY KEY,
      NAME VARCHAR(100) NOT NULL,
      ACC_TYPE VARCHAR(50) NOT NULL DEFAULT 'SAVINGS'
);
```

You can provide multiple constraints in one line.\
Look at the `ACC_TYPE` where we have datatype `VARCHAR(50)` which means this takes characters of 50 length, and then it has multiple constraints `NOT NULL`, `DEFAULT` which says that the column cannot be null, and if nothing is provided then it will by default put the value `SAVINGS`.

**SERIAL constraint:**

Serial constraint means that the value keeps on getting auto-incremented everytime you give a new entry.\
It is auto-increment constraint.

```sql
CREATE TABLE EMPLOYEES(
      ID SERIAL PRIMARY KEY,
      FIRSTNAME VARCHAR(50),
      LASTNAME VARCHAR(50)
);
```

