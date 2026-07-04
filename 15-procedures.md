# Procedures

A procedure is a block of SQL code that performs a series of operations — like inserting, updating, deleting, or selecting data — and is stored in the database.

Think of it like a _function in programming_ — once defined, you can call it again and again without rewriting the logic.

### Why even use procedures?

- **Reusability:** Write once, use many times.
- **Security:** Logic is stored in DB, no need to give direct access to all tables.
- **Faster execution:** Compiled and stored on the DB server.
- **Encapsulation:** Hide complex logic in one callable block.
- **Multi-step operations:** Perform multiple queries like insert + update + log creation on one procedure.

----

### How do you even create a procedure?

Syntax for creating a new procedure,

```sql
CREATE PROCEDURE procedure_name(param_1 datatype, param_2 datatype)
LANGUAGE plpgsql
AS $$
BEGIN
    -- SQL logic here
END;
$$;
```

Syntax for executing the procedure,

```sql
CALL procedure_name(arg_1, arg_2);
```

----

**Q:** Create a procedure for adding new product in database.

**Solution:**

For creating a procedure,

```sql
CREATE PROCEDURE ADD_PRODUCT(
    P_NAME VARCHAR,
    P_SKU CHAR(8),
    P_PRICE NUMERIC,
    P_QTY INT,
    P_CATEGORY TEXT
)
LANGUAGE plpgsql
AS $$
BEGIN
    INSERT INTO PRODUCT(NAME, SKU_CODE, PRICE, STOCK_QUANTITY, CATEGORY)
    VALUES (P_NAME, P_SKU, P_PRICE, P_QTY, P_CATEGORY);

    RAISE NOTICE 'Product added successfully!';
END;
$$;
```

For calling a procedure,

```sql
CALL ADD_PRODUCT('Bottle', 'BO124252', 234.00, 50, 'Fitness');
```

