# One-to-Many Relationship

Parent table `student`,

```sql
CREATE TABLE STUDENT (
    STUDENT_ID SERIAL PRIMARY KEY,
    NAME VARCHAR(40)
);
```

Child table `marks`,

```sql
CREATE TABLE MARKS (
    MARK_ID SERIAL PRIMARY KEY,
    STUDENT_ID INT,
    SUBJECT VARCHAR(40),
    MARKS SMALLINT

    FOREIGN KEY (STUDENT_ID)
    REFERENCES STUDENT(STUDENT_ID)
);
```

These `student` and `marks` tables have one-to-many relationship, between them, as one student could have multiple marks, while a single marks belongs to only one student.

Another child table `student_profile`,

```sql
CREATE TABLE STUDENT_PROFILE (
    STUDENT_ID INT PRIMARY KEY,
    ADDRESS TEXT,
    AGE SMALLINT,
    PHONE VARCHAR(10)
);
```

These `student` and `student_profile` have one-to-one relationship between them, as only one student will have one student profile, and vice-versa.

After inserting values into both the tables, now in order to see the records — student_id, name, subject, and marks.

```sql
SELECT
    S.STUDENT_ID,
    S.NAME,
    SP.AGE,
    M.SUBJECT,
    M.MARKS,
    SP.PHONE
FROM STUDENT S
JOIN STUDENT_PROFILE SP
    ON S.STUDENT_ID = SP.STUDENT_ID
JOIN MARKS M
    ON S.STUDENT_ID = M.STUDENT_ID;
```

----

**Q:** Write a query to answer these set of questions:

1. Show each student's name along with their subject and marks.

```sql

```

2. Show marks for only 'Divya Bharathi' in all subjects.

3. Show only those subjects where marks are above 80.

4. Sort all student's subject marks in descending order of marks.

5. Show each student's average marks.

