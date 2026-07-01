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

----

### Set/Changing the default value of a column

For example, you want to set the default value for the column 'age' to 18.

```sql
ALTER TABLE STUDENTS
ALTER COLUMN AGE SET DEFAULT 18;
```

----

### Removing a default value

For example, you want to remove the default value from the column 'age'.

```sql
ALTER TABLE STUDENTS
ALTER COLUMN AGE DROP DEFAULT;
```

----

### Adding a constraint

In order to add a constraint, you have to also give a name to it. For example, here we added a constraint to the 'age' column, so it would also require a constraint name 'age_check'.

We don't to add the constraint name, while initializing a table, because it get done automatically. But, while adding a constraint after initializing a table then you have to do it.

For example, add a constraint to the 'age' column for age should be greater than or equal to 0.

```sql
ALTER TABLE STUDENTS
ADD CONSTRAINT AGE_CHECK CHECK (AGE >= 0);
```

