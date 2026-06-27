# Tables

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
