# Alter Table

So far, we've been working with existing data - inserting it, writing it, filtering it, analyzing it.

But now what if you want to:

- Change the column name from "NAME" TO "PRODUCT_NAME".
- Add a new column for brand.
- Remove a constraint, change a data type, rename a table.

### Use cases of alter

1. Add new columns
2. Remove columns
3. Rename columns
4. Change data types
5. Set or remove default values
6. Add or remove constraints
7. Rename the table

----

### Add a new column

All the rows will have the null values now be aware of that. For that you can have a default value.

```sql
ALTER TABLE STUDENTS
ADD COLUMN EMAIL VARCHAR(100);
```

Used to add new column into the table, also remember that, for the records that were added to the table before this new column, will have null values.

----

### Remove a column

```sql
ALTER TABLE STUDENTS
DROP COLUMN EMAIL;
```

This is used to entirely delete a column that you don't want.

----

### Renaming a column

Used to rename a column to something new.

Example, here we are changing the 'name' column to 'student_name'.

```sql
ALTER TABLE STUDENTS
RENAME COLUMN NAME TO STUDENT_NAME;
```

----

### Change data type of a column

Used to change the data type of a column, for example, here 'age' was _big int_, so we changed it to _small int_.

```sql
ALTER TABLE STUDENTS
ALTER COLUMN AGE TYPE SMALLINT;
```

