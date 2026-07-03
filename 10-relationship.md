# Relationships

In a relational database, data is stored across multiple tables, and these tables are connected through relationships.

Instead of repeating the same data again and again in one huge table, we split it into smaller, meaningful tables and connect them using _keys_ (_primary_ and _foreign keys_).

Types of relationships:

1. One-to-one (1:1)
2. One-to-many (1:N) (most common)
3. Many-to-many (M:N)

----

### One-to-one (1:1) relationship

One record in Table A is related to exactly one record in Table B, and vice versa.

**Example:** User ↔ Passport\
A user has only one passport. And, a passport belongs to one user.

```
Users                Passports
+----+--------+      +-------------+---------+
| ID | Name   |      | Passport_ID | User_ID |
+----+--------+      +-------------+---------+
| 1  | Ganesh | ---->| P101        | 1       |
| 2  | Simran | ---->| P102        | 2       |
+----+--------+      +-------------+---------+
```

----

### One-to-many (1:M) relationship

One record in Table A can be related to many records in Table B. Each record in Table B belongs to only one record in Table A.

**Example:** Customer → Orders\
One customer can place many orders. Each order belongs to one customer.

```
Customers             Orders

Ganesh  -------------> Order #101
        -------------> Order #102
        -------------> Order #103

Simran --------------> Order #104
```

```
Customers           Orders
+----+--------+     +----------+---------+
| ID | Name   |     | Order_ID | User_ID |
+----+--------+     +----------+---------+
| 1  | Ganesh |     | 101      | 1       |
| 2  | Simran |     | 102      | 1       |
+----+--------+     | 103      | 1       |
                    | 104      | 2       |
                    +----------+---------+
```

----

### Many-to-many (M:N) relationship

Many records in Table A can relate to many records in Table B.

This cannot be implemented directly.

You need a junction table (also called a bridge or association table).

A direct foreign key won't work because:
- A student needs multiple course IDs.
- A course needs multiple student IDs.

**Example:** Students ↔ Courses\
One student can enroll in many courses. One course can have many students.

```
Students          Courses

Ganesh --------\
                \
                 ---> Python
                /
Simran --------/

Ganesh --------\
                ---> SQL
Rahul ---------/
```

```
Students
+----+--------+
| ID | Name   |
+----+--------+
| 1  | Ganesh |
| 2  | Simran |
| 3  | Rahul  |
+----+--------+

Courses
+----+----------+
| ID | Name     |
+----+----------+
| 1  | Python   |
| 2  | SQL      |
+----+----------+

Enrollments
+------------+-----------+
| Student_ID | Course_ID |
+------------+-----------+
| 1          | 1         |
| 1          | 2         |
| 2          | 1         |
| 3          | 2         |
+------------+-----------+
```

----

### Joins

`JOIN` is used to combine rows from two or more tables based on a related column, usually a primary key in one table and a foreign key in another.

Think of `JOIN` as a bridge between two tables that lets you query them together.

----

### Types of JOINs

| Join type | Description |
| ---- | ---- |
| `INNER JOIN` | Returns only matching rows in both tables |
| `LEFT JOIN` | Returns all rows from the left table, even if there's no match in the right table. |
| `RIGHT JOIN` | Returns all rows from the right table, even if there's no match in the left table. |
| `FULL JOIN` | Returns all rows from both tables, fills NULL for missing matches. |
| `CROSS JOIN` | Returns cartesian product (every combination). |

----

### Inner join

```sql
SELECT columns
FROM table_1 t1
JOIN table_2 t2
    ON t1.common_col = t2.common_col;
```

----

### Left join

Returns everything from the left table, plus matching rows from the right.

```sql
SELECT columns
FROM table_1 t1
LEFT JOIN table_2 t2
    ON t1.common_col = t2.common_col;
```

----

### Right join

Returns everything from the right table, plus matching rows from the left.

```sql
SELECT columns
FROM table_1 t1
RIGHT JOIN table_2 t2
    ON t1.common_col = t2.common_col;
```

----

### Full join

Returns everything from both tables.

```sql
SELECT
    t1.col_1,
    t1.col_2,
    m.col_1,
    m.col_2
FROM table_1 t1
FULL JOIN table_2 t2
    on t1.col_1 = t2.col_2;
```

----

### Cross join

Returns every possible combination of rows.

```sql
SELECT *
FROM table_1
CROSS JOIN table_2;
```

