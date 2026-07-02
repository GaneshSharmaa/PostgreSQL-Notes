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

