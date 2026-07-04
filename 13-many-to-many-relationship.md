# Many-to-many Relationship

In many-to-many relationship

- One row in **Table A** can be linked to many rows in **Table B**.
- And, one row in **Table B** can be linked to many rows in **Table A**.

A many-to-many (M:N) relationship exists when **one record in Table A can be related to many records in Table B**, and **one record in Table B can also be related to many records in Table A**.

Since relational databases cannot represent this relationship directly, we create a **_junction table_** (also called a bridge table or association table) that stores the relationship between the two tables.

----

### Example

A student can enroll in many courses.\
Same way, a course can have many students.

**Students table**

| student_id | student_name |
| ----       | ----         |
| 1          | Ganesh       |
| 2          | Khushi       |
| 3          | Shubh        |

**Courses table**

| course_id | course_name             |
| ----      | ----                    |
| 101       | Python                  |
| 102       | Artificial Intelligence |
| 103       | Machine Learning        |
| 104       | Deep Learning           |

**Student_Courses (junction table)**

| student_id | course_id |
| ----       | ----      |
| 1          | 101       |
| 1          | 102       |
| 2          | 104       |
| 3          | 101       |
| 2          | 103       |
| 2          | 101       |

----

### How'd you create the table, for many-to-many relationship?

```sql
CREATE TABLE STUDENTS (
    STUDENT_ID INT PRIMARY KEY,
    STUDENT_NAME VARCHAR(40)
);

CREATE TABLE COURSES (
    COURSE_ID INT PRIMARY KEY,
    COURSE_NAME VARCHAR(40)
);

CREATE TABLE STUDENT_COURSES (
    STUDENT_ID INT,
    COURSE_ID INT,

    PRIMARY KEY (STUDENT_ID, COURSE_ID),
    FOREIGN KEY (STUDENT_ID) REFERENCES STUDENTS(STUDENT_ID),
    FOREIGN KEY (COURSE_ID) REFERENCES COURSES(COURSE_ID)
);
```

Here in the `student_courses` junction table, there are two primary keys, and this is called as composite primary key.

The composite primary key (student_id, course_id) ensures that the same student cannot be enrolled in the same course more than once.

----

### Questions

**Q1:** Show the list of students with the courses they are enrolled in.

```sql
SELECT S.STUDENT_NAME, C.COURSE_NAME
FROM STUDENT_COURSES SC
JOIN STUDENTS S ON SC.STUDENT_ID = S.STUDENT_ID
JOIN COURSES C ON SC.COURSE_ID = C.COURSE_ID;
```

**Q2:** Find all the courses taken by the student named 'Shubh'.

```sql
SELECT S.STUDENT_NAME, C.COURSE_NAME
FROM STUDENT_COURSES SC
JOIN STUDENTS S ON SC.STUDENT_ID = S.STUDENT_ID
JOIN COURSES C ON SC.COURSE_ID = C.COURSE_ID
WHERE S.STUDENT_NAME = 'Shubh';
```

