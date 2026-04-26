# Group By Clause

The `GROUP BY` statement is used in SQL to arrange identical data into groups.

This clause follows the `WHERE` clause in a `SELECT` statement and precedes the `ORDER BY` clause.

It is most often used with aggregate functions to generate summary reports from the database.

Basic syntax:

```sql
SELECT column_name1 AGGREGATE_FUNCTION(column_name2) FROM table_name
WHERE condition GROUP BY column_name1 ORDER BY column_name1;
```

**Key Concepts**

1. **Grouping:** It combines rows that have the same values in specified columns into a single summary row.

2. **Aggregation:** It allows you to perform a calculation on each group using an aggregate function.

For example, total number of employees in each department.

```sql
SELECT DEPT, COUNT(*) FROM EMPLOYEES
GROUP BY DEPT;
```
