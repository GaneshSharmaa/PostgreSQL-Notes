# String Functions

String functions are used to manipulate and process text data (character values).

String functions help in data cleaning, formatting, and transformation.

Widely used in data analysis, reporting, and backend systems.

----

### Some of the common string functions are

- `CONCAT`, `CONCAT_WS`
- `SUBSTR`
- `LEFT`, `RIGHT`
- `LENGTH`
- `UPPER`, `LOWER`
- `TRIM`, `LTRIM`, `RTRIM`
- `REPLACE`
- `POSITION`
- `STRING_AGG`

----

### `CONCAT()` function

Syntax

```sql
CONCAT(FIRST_COL, SECOND_COL)
```

OR

```sql
CONCAT(FIRST_WORD, SECOND_WORD)
```

For example, you want to see the full name of an employees using their first name and last name.

```sql
SELECT CONCAT(F_NAME, L_NAME) AS FULL_NAME FROM EMPLOYEES;
```

----

### `CONCAT_WS()` function

Syntax

```sql
CONCAT_WS('SEP', FIRST_COL, SECOND_COL);
```

`CONCAT()` joins everything without any _separator_ between them.

In order to have a _separator_ between each column or word, you can use `CONCAT_WS()` function to add a separator.

For example, when you want to concatenate first name and last name of employees to get their full name

```sql
SELECT CONCAT_WS(' ', F_NAME, L_NAME) AS FULL_NAME FROM EMPLOYEES;
```

Here, in this function the first _argument_ will always be a _separator_, and it could be anything, a space ` `, a dash `-`, or even a colon `:`, or something else.

----

### `SUBSTR()` OR `SUBSTRING()` function

Syntax

```sql
SUBSTRING('ORIGINAL_STRING', START_POS, LENGTH);
```

Where, `START_POS` is starting position, and it starts from 1 (not with 0, like in programming languages).

And `LENGTH` is the number of characters to extract from a string.

`SUBSTR()` function is used to extract a part (substring) of a string starting from a specified position.

And the first argument will always be the _original string_.

For example, you want to extract first 3 letters from the word `LAPTOP`

```sql
SELECT SUBSTR('LAPTOP', 1, 3);
```

----

### `REPLACE()` function

`REPLACE()` function is used replace all occurrences of a specified substring within a string with another substring.

Syntax

```sql
REPLACE(STR, FROM_STR, TO_STR)
```

Where, `STR` is the original text, `FROM_STR` is the part of the string to replaced, and `TO_STR` is the new value to replace with.

For example, in string `'Hello World'`, replace `'World'` with new string `'SQL'`.

```sql
REPLACE('HELLO WORLD', 'WORLD', 'SQL')
```

For example, in `EMPLOYEES` table, you want to replace `'IT'` with `'TECH'`.

```sql
SELECT REPLACE(DEPT, 'IT', 'TECH');
```

----

### `REVERSE()` function

`REVERSE()` function is used to reverse the order of the characters in a string.

Syntax

```sql
REPLACE('STRING')
```

----

### `LENGTH()` function

`LENGTH()` function is used to find out the length of the string.

Syntax

```sql
SELECT LENGTH('HELLO WORLD');
```

For example, you want to find the length of the string `'ENTREPRENEUR'`.

```sql
SELECT LENGTH('ENTREPRENEUR');
```

For example, you want to find out the employees who's first name has more than 5 characters.

```sql
SELECT * FROM EMPLOYEES
WHERE LENGTH(F_NAME) > 5;
```

----

