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

