# Datatypes

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
