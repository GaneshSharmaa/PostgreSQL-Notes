# Data Types

Until now, there are some problems that we encounter, they re:

- Columns could have null values
- The values can be repeated, which needs to be unique
- Wrong data type values

Therefore, we came up with something else, constraints and data types.

----

### Data types

If we talk about SQL we have multiple datatypes these include:

1. Numeric data types
2. Character/string data types
3. Boolean data types
4. Date and time data types

### Numeric data types

| Data type                          | Description                           | Example        |
| ---                                | ---                                   | ---            |
| `SMALLINT`                         | 2 bytes integer (-32,768 to 32,768)   | `age SMALLINT` |
| `INTEGER` / `INT`                  | 4 bytes integer (-2B to 2B)           | `quantity INT` |
| `BIGINT`                           | 8 bytes integer                       | `views BIGINT` |
| `DECIMAL(p, s)` / `NUMERIC(p, s)`  | Exact precision                       | `price NUMERIC(8, 2)` |
| `REAL`                             | 4-byte floating point                 | `rating REAL`  |
| `DOUBLE PRECISION`                 | 8-byte floating point                 | `accuracy DOUBLE PRECISION` |
| `SERIAL`                           | auto-increment integer                | `id SERIAL PRIMARY KEY` |

Example, let's say we want to create a table

```sql
CREATE TABLE NUMBERS (
    ID SERIAL PRIMARY KEY,
    AGE SMALLINT,
    PRICE NUMERIC(4, 2),
    RATING REAL
);
```

### Character/String data types

| Data type | Description | Example |
| ---       | ---         | ---     |
| `CHAR(n)`   | Fixed-length string (pads with space) | `code CHAR(5)` |
| `VARCHAR(n)`   | Variable-length string (limit n chars) | `email VARCHAR(100)` |
| `TEXT`   | Unlimited-length string | `bio TEXT` |

Example,

```sql
CREATE TABLE STRINGS (
    CODE CHAR(5),
    EMAIL VARCHAR(100),
    BIO TEXT
);
```

### Boolean data types

Boolean data types could have only 3 values → `TRUE`, `FALSE`, and `NULL`.

Example,

```sql
CREATE TABLE SUBSCRIPTIONS (
    USER_ID INT,
    NAME VARCHAR(25),
    AGE SMALLINT,
    IS_SUBSCRIBED BOOLEAN
);
```

### Date & time data types

| Data type     | Description               | Example                |
| ---           | ---                       | ---                    |
| `DATE`        | Only date (2026-06-21)    | `dob DATE`             |
| `TIME`        | Only time (14:30:00)      | `login_time TIME`      |
| `TIMESTAMP`   | Date + time               | `created_at TIMESTAMP` |
| `TIMESTAMPTZ` | Date + time with timezone | `event_at TIMESTAMPTZ` |
| `INTERVAL`    | Time difference           | `duration INTERVAL`    |

Example,

```sql
CREATE TABLE LAUNCH_EVENTS (
    LAUNCH_DATE DATE,
    LAUNCH_TIME TIME,
    LAUNCH_DATE_TIME TIMESTAMP,
    LAUNCH_EVENT TIMESTAMPTZ,
    INTERMISSION INTERVAL
);
```

----

# Constraints

Constraints are the rules that PostgreSQL enforces on the data.

Think of them, as a guardrails at the database level. Even if your application has a bug, database won't allow invalid data.

| Constraints   | Description                    | Example                              |
| ---           | ---                            | ---                                  |
| `PRIMARY KEY` | Uniquely indentifies each row  | `ID SERIAL PRIMARY KEY`              |
| `NOT NULL`    | Column must have a value       | `NAME TEXT NOT NULL`                 |
| `UNIQUE`      | No duplicate values allowed    | `EMAIL VARCHAR(50) UNIQUE`           |
| `DEFAULT`     | Provides default value if none | `CREATED_AT TIMESTAMP DEFAULT NOW()` |
| `CHECK`       | Validates values               | `AGE INT CHECK (AGE > 18)`           |
| `FOREIGN KEY` | Links one table to another     | `USER_ID INT REFERENCE USERS(ID)`    |

`NOT NULL` prevents empty values.

`UNIQUE` prevents duplicate values.

`PRIMARY KEY` is a combination of `UNIQUE` & `NOT NULL`, and only one primary key per table.

`CHECK` validates the condition.

`DEFAULT` provides a value when none is supplied.

`FOREIGN KEY` creates a relationship between tables.

Example, lets say we want to create a table for a hotel management system,

```sql
CREATE TABLE TEST (
    ID INT PRIMARY KEY,
    NAME VARCHAR(25) NOT NULL,
    AGE SMALLINT CHECK (AGE >= 18),
    EMAIL VARCHAR(40) UNIQUE,
    CHECK_IN TIMESTAMP DEFAULT NOW()
);
```

