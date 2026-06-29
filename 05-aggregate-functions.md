# Aggregate Functions

Aggregate functions are used to summarize data.

Instead of looking at every single row, we use these functions to get overall insights, like:

- How many records are there?
- What's the total price?
- What's the average stock?
- What's the max/min value in a column?

Some of the basic aggregation functions are:

| Aggregate function | Description          | Used for                     |
| ----               |----                  | ----                         |
| `COUNT()`          | Count number of rows | Total number of products     |
| `SUM()`            | Add numeric values   | Total stock in a category    |
| `AVG()`            | Calculate average    | Average price of accessories |
| `MIN()`            | Find smallest value  | Cheapest product             |
| `MAX()`            | Find highest value   | Most expensive product       |

**Q:** Write a query to display the total count of records in the table.

```sql
SELECT COUNT(*) FROM PRODUCT;
```

**Q:** Write a query to display the total number of products that are less than 500 price.

```sql
SELECT COUNT(*) FROM PRODUCT
WHERE PRICE < 500;
```

**Q:** Write a query to display the total sum of the stock quantity of items belonging to the 'Furniture' category.

```sql
SELECT SUM(STOCK_QUANTITY) FROM PRODUCT
WHERE CATEGORY = 'Furniture';
```

**Q:** Write a query to display the average price of the items belonging to the 'Stationery' category.

`ROUND()` is used to round-off the values to desired precision.

```sql
SELECT ROUND(AVG(PRICE), 2) FROM PRODUCT
WHERE CATEGORY = 'Stationery';
```

**Q:** Write a query to display the minimum price of the item belonging to the 'Electronics' category.

```sql
SELECT MIN(PRICE) FROM PRODUCT
WHERE CATEGORY = 'Electronics';
```

**Q:** Write a query to display the maximum price of the item belonging to the 'Electronics' category.

```sql
SELECT MAX(PRICE) FROM PRODUCT
WHERE CATEGORY = 'Electronics';
```

-----

Now, that we've learned about _clauses_, _operators_, and _aggregation functions_ now, let's practise some questions.

**Q:** Write a query to display the name and price of the cheapest product in the entire table.

**Q:** Write a query to display the average price of products that belong to the 'Home & Kitchen' or 'Fitness' category.

**Q:** Write a query to show product names and stock quantity where the product is available, stock is more than 50, and price is not equal to 299.

**Q:** Write a query to display the most expensive product in each category (name and price).

**Q:** Write a query to show all unique categories in uppercase, sorted in descending order.
