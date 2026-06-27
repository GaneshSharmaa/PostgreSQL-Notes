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

### Some commands for PostgreSQL

Cheat sheet of the main PostgreSQL commands (both psql slash commands and SQL commands) since literally all commands would be massive.

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

### Common SQL commands in PostgreSQL:

Database/schema:

1. CREATE DATABASE
2. DROP DATABASE
3. CREATE SCHEMA
4. DROP SCHEMA

Table/object definition (DDL):

1. CREATE TABLE
2. ALTER TABLE
3. DROP TABLE
4. TRUNCATE TABLE
5. CREATE INDEX
6. DROP INDEX
7. CREATE VIEW
8. DROP VIEW

Data operations (DML):

1. SELECT
2. INSERT
3. UPDATE
4. DELETE
5. MERGE
6. RETURNING (used with INSERT/UPDATE/DELETE)

Permissions/security (DCL):

1. GRANT
2. REVOKE
3. CREATE ROLE
4. ALTER ROLE
5. DROP ROLE

Transactions (TCL):

1. BEGIN
2. COMMIT
3. ROLLBACK
4. SAVEPOINT
5. RELEASE SAVEPOINT
