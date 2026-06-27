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

----

### `SUM()` function

`SUM()` function takes arguments, and returns the sum of them. It takes column name as a function argument.

For example, you want to know the total amount you are giving to your employees as salary.

```sql
SELECT SUM(SALARY) FROM EMPLOYEES;
```

----

### `AVG()` function

`AVG()` function takes column name as its function arguments, and returns the average values of them.

For example, you want to know what is the average salary of an employee.

```sql
SELECT AVG(SALARY) FROM EMPLOYEES;
```

----

### `MIN()` function

`MIN()` function takes a column name as its function arguments, and returns the minimum values from it.

For example, you want to know minimum salary that an employee is getting.

```sql
SELECT MIN(SALARY) FROM EMPLOYEES;
```

----

### `MAX()` function

`MAX()` function takes a column name as its function arguments, and returns the maximum value from it.

For example, you want to know the maximum salary that an employee is getting.

```sql
SELECT MAX(SALARY) FROM EMPLOYEES;
```

----

