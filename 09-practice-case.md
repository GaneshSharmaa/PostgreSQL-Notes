# Questions on Cases

**Q1:** Display the product name, price, and a new column called Price_Level using these rules:\
Price < 500 → Cheap,\
Price between 500 and 2000 → Moderate,\
Price > 2000 → Expensive.

```sql
SELECT NAME, PRICE,
CASE
    WHEN (PRICE > 2000) THEN 'Expensive'
    WHEN (PRICE BETWEEN 500 AND 2000) THEN 'Moderate'
    ELSE 'Cheap'
END AS PRICE_LEVEL
FROM PRODUCT;
```

----

**Q2:** Display:\
Out of Stock → STOCK_QUANTITY = 0,\
Low Stock → STOCK_QUANTITY <= 20
In Stock → Otherwise

Show:

```sql
NAME | STOCK_QUANTITY | STOCK_STATUS
```

```sql
SELECT NAME, STOCK_QUATITY,
CASE
    WHEN STOCK_QUATITY = 0 THEN 'Out of stock'
    WHEN STOCK_QUATITY <= 20 THEN 'Low stock'
    ELSE 'In stock'
END AS STOCK_STATUS
FROM PRODUCT;
```

----

**Q3:** Write a query to display:

- Available
- Unavailable

instead of displaying 't' and 'f',

Show:

```
NAME | IS_AVAIL | STATUS
```

```sql
SELECT
    NAME, IS_AVAIL,
    CASE
        WHEN IS_AVAIL THEN 'Available'
        ELSE 'Unavailable'
    END AS STATUS
FROM PRODUCT;
```

----

**Q4:** Write a query to create a column called DISCOUNT.

Rules:

Price ≥ 5000 → 20% Discount\
Price between 2000 and 4999 → 10% Discount\
Otherwise → No Discount

```sql
ALTER TABLE PRODUCT
ADD COLUMN DISCOUNT SMALLINT;

UPDATE PRODUCT
SET DISCOUNT = CASE
    WHEN PRICE >= 5000 THEN 20
    WHEN PRICE BETWEEN 2000 AND 4999 THEN 10
    ELSE 0
END;
```

**Q5:** Write a query to assign each product to a warehouse zone.

Electronics & Wearables → Zone A\
Furniture & Bags → Zone B\
Everything else → Zone C

Display:

```
NAME | CATEGORY | WAREHOUSE_ZONE
```

```sql
SELECT
    NAME, CATEGORY,
    CASE
        WHEN CATEGORY = 'Electronics' THEN 'Zone A'
        WHEN CATEGORY = 'Wearables' THEN 'Zone A'
        WHEN CATEGORY = 'Furniture' THEN 'Zone B'
        WHEN CATEGORY = 'Bags' THEN 'Zone B'
        ELSE 'Zone C'
    END AS WAREHOUSE_ZONE
FROM PRODUCT;
```

----

**Q6:** Write a query to display all products, but sort them in this order:

Expensive\
Moderate\
Cheap

Hint: Use `CASE` inside `ORDER BY`.

```sql
SELECT *
FROM PRODUCT
ORDER BY
CASE
    WHEN PRICE_CATEGORY = 'Expensive' THEN 1
    WHEN PRICE_CATEGORY = 'Moderate' THEN 2
    ELSE 3
END;
```

----

**Q7:** Write a query to display without updating the table, display a column called NEW_PRICE.

Rules:

Electronics → Increase price by 10%\
Furniture → Increase by 5%\
Others → No change

Output:

```
NAME | PRICE | NEW_PRICE
```

```sql
SELECT NAME, PRICE AS OLD_PRICE,
CASE
    WHEN CATEGORY = 'Electronics' THEN PRICE * 1.1
    WHEN CATEGORY = 'Furniture' THEN PRICE * 1.05
    ELSE PRICE
END AS NEW_PRICE
FROM PRODUCT;
```

----

**Q8:** Write a query to create a column called CATEGORY_TYPE.

Rules:

Electronics, Accessories, Wearables → Technology\
Furniture, Bags → Home\
Kitchen, Fitness → Lifestyle\
Everything else → Other

```sql
ALTER TABLE PRODUCT
ADD COLUMN CATEGORY_TYPE;

UPDATE PRODUCT
SET CATEGORY_TYPE = CASE
    WHEN CATEGORY = 'Electronics' THEN 'Technology'
    WHEN CATEGORY = 'Accessories' THEN 'Technology'
    WHEN CATEGORY = 'Wearables' THEN 'Technology'
    WHEN CATEGORY = 'Furniture' THEN 'Home'
    WHEN CATEGORY = 'Bags' THEN 'Home'
    WHEN CATEGORY = 'Kitchen' THEN 'Lifestyle'
    WHEN CATEGORY = 'Fitness' THEN 'Lifestyle'
    ELSE 'Other'
END;
```

----

**Q9:** Write query to create a column called SHIPPING_PRIORITY.

Rules:

Price > 5000 and available → High\
Price between 1000 and 5000 → Medium\
Otherwise → Low

```sql
ALTER TABLE PRODUCT
ADD COLUMN SHIPPING_PRIORITY;

UPDATE PRODUCT
SET SHIPPING_PRIORITY = CASE
    WHEN PRICE > 5000 AND IS_AVAIL THEN 'High'
    WHEN PRICE BETWEEN 1000 AND 5000 THEN 'Medium'
    ELSE 'Low'
END;
```

----

**Q10:** Write a query to display NAME, PRICE, STOCK_QUANTITY, INVENTORY_VALUE, VALUE_CATEGORY.

Where

```
INVENTORY_VALUE = PRICE × STOCK_QUANTITY
```

Then use another CASE:

Value > 100000 → High Value\
Value between 50000 and 100000 → Medium Value\
Otherwise → Low Value

This combines arithmetic with CASE.

```sql
SELECT
    NAME, PRICE, STOCK_QUANTITY, PRICE * STOCK_QUANTITY AS INVENTORY_VALUE,
    CASE
        WHEN PRICE * STOCK_QUANTITY > 100000 THEN 'High value'
        WHEN PRICE * STOCK_QUANTITY BETWEEN 50000 AND 100000 THEN 'Medium value'
        ELSE 'Low value'
    END AS VALUE_CATEGORY
FROM PRODUCT;
```

