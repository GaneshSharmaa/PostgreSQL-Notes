# String Functions

_String functions_ in PostgreSQL are used to manipulate text data — like names, categories, SKUs, etc.

They help you:

- Clean text
- Extract parts of string
- Convert cases
- Replace or remove characters

### `UPPER()`, `LOWER()`, and `LENGTH()` functions

**Q:** Write a query to display the name in uppercase.

```sql
SELECT UPPER(NAME) FROM PRODUCT;
```

**Q:** Write a query to display the name in lowercase.

```sql
SELECT LOWER(NAME) FROM PRODUCT;
```

**Q:** Write a query to display the length of the name.

```sql
SELECT NAME, LENGTH(NAME) AS STRING_LENGTH FROM PRODUCT;
```

### Substring function — `SUBSTR(TEXT, LOCATION, LENGTH)`

**Q:** Write a query to extract the word 'brother' from the text 'brother in arms'.

- Indexing in SQL starts from 1, and not 0.

```sql
SELECT SUBSTR('brother in arms', 1, 7);
```

**Q:** Write a query to extract the word 'arms' from the text 'brother in arms'.

```sql
SELECT SUBSTR('brother in arms', 12, 4);
```

**Q:** Write a query to display the only alphabetic characters from the alphanumeric SKU code.

```sql
SELECT SUBSTR(SKU_CODE, 1, 2) FROM PRODUCT;
```

**Q:** Write a query to display the only numeric characters from the alphanumeric SKU code.

```sql
SELECT SUBSTR(SKU_CODE, 3, 6) FROM PRODUCT;
```

- Also, if you want to extract sub-strings then we can do using `LEFT()` and `RIGHT()` function, and as name suggest they work from left to right and right to left, respectively.

```sql
SELECT LEFT('HELLO WORLD!', 5);
```

```sql
SELECT RIGHT('HELLO WORLD!', 7);
```

