# Case

Case is a conditional expression in SQL that works like an if-else or switch statement.

It lets you return different values based on different conditions - all within a single query.

Why do we use case?

- To create custom columns on the fly
- To categorize data based on certain logic
- To replace values conditionally
- To handle null or missing values gracefully
- To simplify complex logic inside `SELECT` queries

Syntax of CASE in SQL:

```sql
SELECT
    column_1,
    CASE
        WHEN condition_1 THEN result_1
        WHEN condition_2 THEN result_2
        ...
        ELSE default_result
    END AS new_column_name
FROM table_name;
```

----

**Q:** Write a query to implement case, where:\
if the price is above 1000 → categorize it as expensive
if the price is between 500 and 1000 → categorize it as moderate
and, if the price is below 500 → categorize it as cheap

```sql
SELECT NAME, PRICE,
    CASE
        WHEN (PRICE > 1000) THEN 'Expensive'
        WHEN (PRICE BETWEEN 500 AND 1000) THEN 'Moderate'
        ELSE 'Cheap'
    END AS PRICE_CATEGORY
FROM PRODUCT;
```

----

**Q:** Write a query to add a column 'Price_Category' into a already existing table 'Product' with 20 records, where:\
if the price is above 1000 → categorize it as expensive,\
if the price is between 500 and 1000 → categorize it as moderate,\
and, if the price is below 500 → categorize it as cheap.

```sql
UPDATE PRODUCT
SET PRICE_CATEGORY = CASE
    WHEN (PRICE > 1000) THEN 'Expensive'
    WHEN (PRICE BETWEEN 500 AND 1000) THEN 'Moderate'
    ELSE 'Cheap'
END;
```

This way, we also updated the existing recordsof the table.

----

**Q:** Write a query to display name, stock quantity and stock level. Where the column stock level should categorize the stock into high, medium, and low.\
If quantity is more than 100 → high stock,\
if quantity is between 30 to 100 → medium stock,\
if quantity is less than 30 → low stock.

```sql
UPDATE PRODUCT,
SET STOCK_LEVEL = CASE
    WHEN (STOCK_QUANTITY > 100) THEN 'High stock'
    WHEN (STOCK_QUANTITY BETWEEN 30 AND 100) THEN 'Medium stock'
    ELSE 'Low stock'
END;
```

----

**Q:** Write a query to display the name and stock availabilty status when if the stock is available shows 'in stock' else 'out of stock'.

```sql
SELECT NAME,
CASE WHEN IS_AVAIL THEN 'In stock'
ELSE 'Out of stock'
END AS AVAILABILITY_STATUS
FROM PRODUCT;
```

