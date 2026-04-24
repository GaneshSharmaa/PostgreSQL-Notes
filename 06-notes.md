# Aggregate Functions

First, let's just understand where do we need to use aggregate functions.

So, in order to find the answers to these questions,

- How to find total number of employees?
- Employee with maximum salary.
- Average salary of employees.

These are the questions where you need to aggregate the whole data to get the information.

In aggregate function there are some functions

- `COUNT()`
- `SUM()`
- `AVG()`
- `MIN()`
- `MAX()`

----

### `COUNT()` function

`COUNT()` function also takes function arguments, it is generally advised to pass the primary key, because it does not have any duplicate and null values.

You can also pass `*` which say take everything as the function argument.

For example, you want to know total number of employees

```sql
SELECT COUNT(*) FROM EMPLOYEES;
```

OR

```sql
SELECT COUNT(EMP_ID) FROM EMPLOYEES;
```

Another example, you want to know how the number of employees who have salary higher than 50000.

```sql
SELECT COUNT(*) FROM EMPLOYEES
WHERE SALARY > 50000;
```
