### `ORDER BY` clause

`ORDER BY` clause is used for sorting the data as per the condition is provided.

For example, sorting the table according to the first name in alphabetical order.

```sql
SELECT * FROM EMPLOYEES ORDER BY F_NAME;
```

This is for sorting according to the ascending ordder (A-Z).

If you want to sort it according to the descending order (Z-A).

```sql
SELECT * FROM EMPLOYEES ORDER BY F_NAME DESC;
```

----

### Setting the limit to number of records to display

By using `LIMIT` keyword you can limit the number of records that will be displayed.

For example, you want to see only 3 employees from the department IT.

```sql
SELECT * FROM EMPLOYEES
WHERE DEPT = 'IT' LIMIT 3;
```

----

### `LIKE` operator

`LIKE` operator is used for finding the pattern among the column data. Unlike `=` operator the `LIKE` operator doesn't need exact match.

For example, finding names that start with letter 'A'

```sql
SELECT * FROM EMPLOYEES
WHERE F_NAME LIKE 'A%';
```

Here, we used 'A' which tells that pick something that starts with letter 'A' and the `%` after that tell us that, it could be of any length.

One more example, finding records where the first name should end with letter 'A'.

```sql
SELECT * FROM EMPLOYEES
WHERE F_NAME LIKE '%A';
```

Another example, where we want to find out the names that have letter 'I' in between.

```sql
SELECT * FROM EMPLOYEES
WHERE F_NAME LIKE '%I%';
```

----

### More common patterns

For example, you want to find out departments that are of two character length.

```sql
SELECT * FROM EMPLOYEES
WHERE DEPT LIKE '__';
```

Here, the two `_` sign means that there is one character at that place. It could also be used for specifying the position.

For example

```sql
SELECT * FROM EMPLOYEES
WHERE F_NAME LIKE '_I%';
```

