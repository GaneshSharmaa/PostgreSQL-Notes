# Clauses

By using clause you can provide conditions in the query.

- Where
- Distinct
- Order by
- Limit
- Like

### WHERE clause:

Where clause could be used for giving conditions, to make a validating condition check.\
Example:

```sql
SELECT * FROM EMPLOYEES
WHERE EMP_NAME = 'ARJUN';
```

### Using operators — `OR` operator

`OR` operator is used for having two conditions, either of them could be `True`.

Even, if only one condition is `True` it will be `True`.

Example:

```sql
SELECT * FROM EMPLOYEES
WHERE DEPT = 'HR' OR SALARY > 50000;
```

This means that the result table will have _employees_ with both conditions being `True` as well as anyone condtion being `True`.

### Using operators — `AND` operator

`AND` operator is used for having two conditions, and it will return the result table that have both of them `True`.

Here, both the conditions need to be `True`.

Example:

```sql
SELECT * FROM EMPLOYEES
WHERE DEPT = 'HR' AND SALARY = 45000;
```

This means that if anyone of the condition is `True` then it return the result table that have either both conditions to be `True` or anyone of them to be `True`.

### Relational Operators

We have various relational operators:

| Operator | Meaning                  |
| ----     | ----                     |
| <        | Less than                |
| >        | Greater than             |
| <=       | Less than or equal to    |
| >=       | Greater than or equal to |
| =        | Equal to                 |
| !=       | Not equal to             |

### `IN` and `NOT IN` Operator

If you want to find employees who work in IT, HR, Finance, then you can use the `OR` operator, but there's another method in which you can use `IN` operator.

For example:

```sql
SELECT * FROM EMPLOYEES
WHERE DEPT IN ('IT', 'HR', 'FINANCE');
```

For example:

```sql
SELECT * FROM EMPLOYEES
WHERE DEPT NOT IN ('IT', 'HR', 'FINANCE');
```

### `BETWEEN` Operator

For example, you want to find employees whose salary is more than 40000 and less than 65000.

For example:

```sql
SELECT * FROM EMPLOYEES
WHERE SALARY BETWEEN 40000 AND 65000;
```

Here, the `BETWEEN` clause includes both the lower value as well as the upper value.

