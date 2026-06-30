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

### `CONCAT()` and `CONCAT_WS()` function

- `CONCAT()` concatenates two strings, while `CONCAT_WS()` concatenates two string with separator in between.

**Q:** Write a query to display the concatenated names and categories.

```sql
SELECT CONCAT(NAME, CATEGORY) FROM PRODUCT;
```

**Q:** Write a query to display the contenated names and categories with a space in between.

```sql
SELECT CONCAT(NAME, ' ', CATEGORY) FROM PRODUCT;
```

- Now, if you want to concatenate multiple entities, so instead of always adding separator in string, we can use `CONCAT_WS()` method, in which we first pass in the separator.

```sql
SELECT CONCAT_WS('-', NAME, CATEGORY, SKU_CODE) FROM PRODUCT;
```

### `TRIM()` and `REPLACE()` functions

- `TRIM()`, this function will remove all the spaces from the string.
- `REPLACE()` this function will replace any thing you want.

```sql
SELECT TRIM('   HELLO   ');
```

- Syntax: `REPLACE(STRING, OLD_STRING, NEW_STRING)`

```sql
SELECT NAME, REPLACE(SKU_CODE, LEFT(SKU_CODE, 2), 'GG') FROM PRODUCT;
```

**Q:** Write a query to replace the spaces in the name, with a hyphen.

```sql
SELECT REPLACE(NAME, ' ', '-') FROM PRODUCT;
```

