# One-to-One Relationship

**Q:** You want to create two tables `student` and `student_profile`, with one-to-one relation between them.

**Solution:**

For parent table `student`.

```sql
CREATE TABLE student (
    student_id SERIAL PRIMARY KEY,
    name VARCHAR(50) NOT NULL
);
```

For child table `student_profile`.

```sql
CREATE TABLE student_profile (
    student_id INT PRIMARY KEY,
    address TEXT,
    age SMALLINT,
    phone CHAR(10),

    FOREIGN KEY (student_id)
        REFERENCES student(student_id)
);
```

For retrieving the information.

```sql
SELECT
    s.student_id,
    s.name,
    sp.address,
    sp.age,
    sp.phone
FROM student s
JOIN student_profile sp
ON s.student_id = sp.student_id;
```

