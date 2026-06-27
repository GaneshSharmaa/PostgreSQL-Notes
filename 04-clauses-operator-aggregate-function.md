# Clauses

_Clauses_ are mainly used for querying the data and are kind of building blocks even you all are using them from the start.

Even, `SELECT` and `FROM` they are too _clauses_.

Some of the main clauses that you should know:

| Clause     | Description                                      |
| ---        | ---                                              |
| `SELECT`   | Choose which columns to display                  |
| `FROM`     | Specify the table                                |
| `WHERE`    | Filter rows based on a condition                 |
| `GROUP BY` | Group rows for aggregation                       |
| `HAVING`   | Filter aggregated groups (used after `GROUP BY`) |
| `ORDER BY` | Sort the result in ascending or descending order |
| `LIMIT`    | Limit the number of rows returned                |
| `AS`       | Rename columns or tables temporarily (aliasing)  |
| `DISTINCT` | Return only unique/distinct values               |

Applying all the clauses in the questions directly.

### **Q:** Show the name and price of all products.

**Solution:**

```sql
SELECT NAME, PRICE FROM PRODUCT;
```

### **Q:** Show all products where the category is Electronics.

**Solution:** 

```sql
SELECT * FROM PRODUCT
WHERE CATEGORY = 'Electronics';
```

Here, we used `WHERE` clause, which is used to validate a conditions.

### **Q:** Group products by category. Show each category once.

**Solution:** 

```sql
SELECT CATEGORY FROM PRODUCT
GROUP BY CATEGORY;
```

`GROUP BY` clause groups rows that have same values together so each group can be treated as a single unit, usually for aggregation (`COUNT`, `SUM`, `AVG`, etc.).

### **Q:** Show categories that have more than 1 product. (use after group by).

**Solution:** 

```sql
SELECT CATEGORY, COUNT(*) FROM PRODUCT
GROUP BY CATEGORY
HAVING COUNT(*) > 1;
```

`HAVING` clause is used after `GROUP BY` clause, it is just like `WHERE` clause, but this `HAVING` works on the groups, while `WHERE` works on rows.

Difference between `WHERE` and `HAVING` clause is:

| `WHERE`                        | `HAVING`                   |
| ---                            | ---                        |
| Filters individual rows        | Fillters groups            |
| Executes before `GROUP BY`     | Executes after `GROUP BY`  |
| Cannot use aggregate functions | Can use aggregate function |

### **Q:** Show all products sorted by price in ascending order.

**Solution:**

```sql
SELECT * FROM PRODUCT
ORDER BY PRICE ASC;
```

`ORDER BY` clause is used for sorting the result in ascending or descending order.

### **Q:** Show only the first 3 products from the table.

**Solution:**

```sql
SELECT * FROM PRODUCT
LIMIT 3;
```

`LIMIT` clause is used for limiting the rows returned.

### **Q:** Show product name as 'Item_Name' and price as 'Item_Price'.

**Solution:**

```sql
SELECT NAME AS ITEM_NAME, PRICE AS ITEM_PRICE FROM PRODUCT;
```

### **Q:** Show all the unique categories from the products.

**Solution:**

```sql
SELECT DISTINCT CATEGORY FROM PRODUCT;
```

----

# Clauses with Operators

Until now clauses (like `SELECT`, `FROM`, `WHERE`, etc.) were primarily used to select and view data from the table.

But, we often need more than just selecting, we need to perform some operations on the data from the table.

Operations like:

- Filter products greater than a certain price
- Search names that start with a certain letter
- Count how many products are in each category
- Or even find out the most expensive item per group

That's where _operators_ and _aggregate functions_ come into play.

Some of the basic operators are:

- Comparison operator (=, !=, <, >, <=, >=)
- Range (`BETWEEN`)
- Set (`IN`)
- Pattern (`LIKE`)
- Logical (`AND`, `OR`, `NOT`)

### Comparison operator:

**Q:** Write a query to display the items from 'Electronics' category.

```sql
SELECT * FROM PRODUCT
WHERE CATEGORY = 'Electronics';
```

**Q:** Write a query to display the items not from 'Electronics' category.

```sql
SELECT * FROM PRODUCT
WHERE CATEGORY != 'Electronics';
```

**Q:** Write a query to display the items whose price is greater than 1000.

```sql
SELECT * FROM PRODUCT
WHERE PRICE > 1000;
```

**Q:** Write a query to display the items whose price is lesser than 500.

```sql
SELECT * FROM PRODUCT
WHERE PRICE < 500;
```

**Q:** Write a query to display the items whose price is greater than 300 and lesser than 600.

```sql
SELECT * FROM PRODUCT
WHERE PRICE > 300 AND PRICE < 600;
```

**Q:** Write a query to display items from 'Furniture' category and price greater than 1500.

```sql
SELECT * FROM PRODUCT
WHERE CATEGORY = 'Furniture' AND PRICE > 1500;
```

**Q:** Write a query to display items from category either 'Furniture' or 'Kitchen'.

```sql
SELECT * FROM PRODUCT
WHERE CATEGORY = 'Furniture' OR CATEGORY = 'Kitchen';
```

----

### Range operator (Using `BETWEEN`):

- Note that the `BETWEEN` operator is inclusive that means if you want values between 100 and 500, then it includes 100 and 500 both.

**Q:** Write a query to display the items whose price is in range of 300 to 600.

```sql
SELECT * FROM PRODUCT
WHERE PRICE BETWEEN 300 AND 600;
```

----

### Set operator (`IN`):

- `IN` operator is used when you want to check if a value matches any value in a list.

- Instead of writing multiple `OR` conditions, you can use `IN`.

```sql
SELECT * FROM PRODUCT
WHERE PRODUCT_ID IN (2, 3, 5, 9, 13, 15, 18, 19);
```

----

### Pattern operator (`LIKE`):

- The `LIKE` operator is used for pattern matching in text columns.

- Instead of matching an exact value, it lets you search for text that follows a pattern.

- There are two main wildcards:
    - `%` → Zero or more characters
    - `_` → Exactly one character

**Q:** Write a query to display the SKU code of items starting with 'W'.

```sql
SELECT * FROM PRODUCT
WHERE SKU_CODE LIKE 'W%';
```

