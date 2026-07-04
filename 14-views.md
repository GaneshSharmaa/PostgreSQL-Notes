# Views

A view is a virtual table based on a SQL query.

It does not store actual data, but shows results when accessed — just like a saved query.

### Why even use **Views**?

- **Simplify complex queries:** Saves a long query and access it like a table.
- **Reuse logic:** No need to rewrite JOINs or filters again and again.
- **Security:** Expose only selected columns instead of giving full access to the table.
- **Abstraction:** Hide table complexity for front-end/dashboard users.
- **Maintainability:** If logic changes, update the view once, changes reflect everywhere.

### How do you even create a **View**?

Syntax,

```sql
CREATE VIEW view_name AS
SELECT col_1, col_2
FROM table_name
WHERE condition;
```

----

**Q:** Create a view for displaying products belonging to the 'Fitness' category.

For creating a view:

```sql
CREATE VIEW FITNESS_PRODUCTS AS
SELECT PRODUCT_ID, NAME, PRICE, CATEGORY, STOCK_QUANTITY
FROM PRODUCT
WHERE CATEGORY = 'Fitness';
```

For viewing that view:

```sql
SELECT * FROM FITNESS_PRODUCTS;
```

**Q:** Create a view for low stock quantity products.

For creating the view:

```sql
CREATE VIEW LOW_STOCK AS
SELECT *
FROM PRODUCT
WHERE STOCK_QUANTITY <= 30;
```

For viewing that view:

```sql
SELECT * FROM LOW_STOCK;
```

----

### Deleting a **View**

If you can create a view, then you can also delete/drop a view too.

Syntax for deleting/dropping a view,

```sql
DROP VIEW view_name;
```

