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
SELECT NAME, SUBJECT, MARKS
FROM STUDENT S
JOIN MARKS M
    ON S.STUDENT_ID = M.STUDENT_ID;
```

2. Show marks for only 'Divya Bharathi' in all subjects.

```sql
SELECT NAME, SUBJECT, MARKS
FROM STUDENT S
JOIN MARKS M
    ON S.STUDENT_ID = M.STUDENT_ID
WHERE NAME = 'Divya Bharathi';
```

3. Show only those subjects where marks are above 80.

```sql
SELECT NAME, SUBJECT, MARKS
FROM STUDENT S
JOIN MARKS M
    ON S.STUDENT_ID = M.STUDENT_ID
WHERE MARKS > 80;
```

4. Sort all student's subject marks in descending order of marks.

```sql
SELECT NAME, SUBJECT, MARKS
FROM STUDENT S
JOIN MARKS M
    ON S.STUDENT_ID = M.STUDENT_ID
ORDER BY MARKS DESC;
```

5. Show each student's average marks.

```sql
SELECT NAME, ROUND(AVG(MARKS), 2)
FROM STUDENT S
JOIN MARKS M
    ON S.STUDENT_ID = M.STUDENT_ID
GROUP BY NAME;
```

----

### Some more questions:

**Q1:** Show each order along with the product name and price.

```sql
SELECT O.ORDER_ID, O.CUSTOMER_NAME, P.PRODUCT_NAME, P.PRICE
FROM PRODUCTS P
INNER JOIN ORDERS O
    ON O.PRODUCT_ID = P.PRODUCT_ID;
```

**Q2:** Show all products even if they were never ordered.

```sql
SELECT O.ORDER_ID, O.CUSTOMER_NAME, P.PRODUCT_NAME, P.PRICE
FROM PRODUCTS P
LEFT JOIN ORDERS O
    ON O.PRODUCT_ID = P.PRODUCT_ID;
```

**Q3:** Show orders for only 'Electronics' category.

```sql
SELECT O.ORDER_ID, O.CUSTOMER_NAME, P.PRODUCT_NAME, P.CATEGORY, P.PRICE
FROM PRODUCTS P
JOIN ORDERS O ON O.PRODUCT_ID = P.PRODUCT_ID
WHERE P.CATEGORY = 'Electronics';
```

**Q4:** List all orders sorted by product price (high to low).

```sql
SELECT O.ORDER_ID, P.PRODUCT_NAME, P.PRICE
FROM ORDERS O
JOIN PRODUCTS P ON O.PRODUCT_ID = P.PRODUCT_ID
ORDER BY P.PRICE DESC;
```

**Q5:** Show number of orders placed for each product.

```sql
SELECT P.PRODUCT_NAME, COUNT(O.ORDER_ID)
FROM ORDERS O
RIGHT JOIN PRODUCTS P ON O.PRODUCT_ID = P.PRODUCT_ID
GROUP BY P.PRODUCT_NAME;
```

**Q6:** Show total revenue earned per product.

```sql
SELECT P.PRODUCT_NAME, SUM(P.PRICE * O.QUANTITY)
FROM ORDERS O
JOIN PRODUCTS P ON O.PRODUCT_ID = P.PRODUCT_ID
GROUP BY P.PRODUCT_NAME;
```

**Q7:** Show products where total order revenue > 2000.

**Q8:** Show unique customers who ordered 'Fitness' products.

