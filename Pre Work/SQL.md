# INTRO TO SQL

## Concepts

SQL, or Structured Query Language, is a language designed to allow both technical and non-technical users query, manipulate, and transform data from a relational database.

## Relational databases

A relational database represents a collection of related (two-dimensional) tables. Each of the tables are similar to an Excel spreadsheet, with a fixed number of named columns (the attributes or properties of the table) and any number of rows of data.

## SELECT statement

this is a query. A query is a statement which declares what data we are looking for , where to find it in the database, and optionally, how to transform it before it is returned.

**How its written :**

    "SELECT 'x' FROM 'y';"

where x is the data im looking for and y is where to go look for it.

## QUERIES WITH CONSTRAINTS (Pt. 1)

In order to filter certain results from being returned, we need to use a **WHERE** clause in the query. The clause is applied to each row of data by checking specific column values to determine whether it should be included in the results or not.

**How its written :**

    SELECT * FROM tablename _WHERE_ x > y;

This will return all records that have value greater than y on their respective field called "x.

| Operator | Condition | SQL Example|
| --- | --- | --- |
| =, !=, < <=, >, >= | Standard numerical operators| col_name != 4|
| BETWEEN … AND …| Number is within range of two values (inclusive)|col_name BETWEEN 1.5 AND 10.5|
|NOT BETWEEN … AND …|Number is not within range of two values (inclusive)|col_name NOT BETWEEN 1 AND 10|
|IN (…)|Number exists in a list|col_name IN (2, 4, 6)|
|NOT IN (…)|Number does not exist in a list|col_name NOT IN (1, 3, 5)|

## QUERIES WITH CONSTRAINTS (Pt. 2)

When writing WHERE clauses with columns containing text data, SQL supports a number of useful operators to do things like case-insensitive string comparison and wildcard pattern matching.

|Operator|Condition|Example|
| --- | --- | --- |
|=|Case sensitive exact string comparison (notice the single equals)|col_name = "abc"|
|!= or <>|Case sensitive exact string inequality comparison|col_name != "abcd"|
|LIKE|Case insensitive exact string comparison|col_name LIKE "ABC"|
|NOT LIKE|Case insensitive exact string inequality comparison|col_name NOT LIKE "ABCD"|
|NOT LIKE|Case insensitive exact string inequality comparison|col_name NOT LIKE "ABCD"|
|%|Used anywhere in a string to match a sequence of zero or more characters (only with LIKE or NOT LIKE)|col_name LIKE "%AT%"(matches "AT", "ATTIC", "CAT" or even "BATS")|
|_|Used anywhere in a string to match a single character (only with LIKE or NOT LIKE)|col_name LIKE "AN_"(matches "AND", but not "AN")|
|IN (…)|String exists in a list|col_name IN ("A", "B", "C")|
|NOT IN (…)|String does not exist in a list|col_name NOT IN ("D", "E", "F")|

#### NOTE

while most database implementations are quite efficient when using these operators, full-text search is best left to dedicated libraries like Apache Lucene or Sphinx. These libraries are designed specifically to do full text search, and as a result are more efficient and can support a wider variety of search features including internationalization and advanced queries.

## LESSON 4

### Filtering and sorting Query results

SQL provides a convenient way to discard rows that have a duplicate column value by using the DISTINCT keyword.

**How its written :**

    "SELECT DISTINCT FROM tablename _WHERE_ x > y;"

SQL provides a way to sort your results by a given column in ascending or descending order using the ORDER BY clause.

**How its written :**

    "SELECT *

    FROM tablename

    WHERE condition(s)

    ORDER BY column ASC/DESC;"

Another clause which is commonly used with the **ORDER** BY clause are the **LIMIT** and **OFFSET** clauses, which are a useful optimization to indicate to the database the subset of the results you care about.
The **LIMIT** will reduce the number of rows to return, and the optional **OFFSET** will specify where to begin counting the number rows from.

**How its written :**

    "SELECT *

    FROM tablename

    WHERE condition(s)

    ORDER BY column ASC/DESC

    LIMIT num_limit OFFSET num_offset;"

## LESSON 5

### Multi-table queries with JOINs

Tables that share information about a single entity need to have a primary key that identifies that entity uniquely across the database. One common primary key type is an auto-incrementing integer (because they are space efficient), but it can also be a string, hashed value, so long as it is unique.

Using the JOIN clause in a query, we can combine row data across two separate tables using this unique key. The first of the joins that we will introduce is the INNER JOIN.

**How its written :**
    "SELECT *

    FROM tablename

    INNER JOIN tablename2

    ON tablename.id = tablename2.id

    WHERE condition(s)

    ORDER BY column, … ASC/DESC

    LIMIT num_limit OFFSET num_offset;"

## LESSON 6

### OUTER JOINs

If the two tables have asymmetric data, which can easily happen when data is entered in different stages, then we would have to use a LEFT JOIN, RIGHT JOIN or FULL JOIN instead to ensure that the data you need is not left out of the results.

    "SELECT *

    FROM tablename

    INNER/LEFT/RIGHT/FULL JOIN tablename2

    ON tablename.id = tablename2.matching_id

    WHERE condition(s)

    ORDER BY column, … ASC/DESC

    LIMIT num_limit OFFSET num_offset;"

Like the INNER JOIN these three new joins have to specify which column to join the data on.
When joining table A to table B, a LEFT JOIN simply includes rows from A regardless of whether a matching row is found in B. The RIGHT JOIN is the same, but reversed, keeping rows in B regardless of whether a match is found in A. Finally, a FULL JOIN simply means that rows from both tables are kept, regardless of whether a matching row exists in the other table.

## LESSON 7

### A short note on NULLs

    "SELECT column, another_column, …
    FROM mytable
    WHERE column IS/IS NOT NULL
    AND/OR another_condition
    AND/OR …;"

An alternative to NULL values in your database is to have data-type appropriate default values, like 0 for numerical data, empty strings for text data, etc. But if your database needs to store incomplete data, then NULL values can be appropriate if the default values will skew later analysis (for example, when taking averages of numerical data).

## LESSON 8

### Queries with expressions

In addition to querying and referencing raw column data with SQL, you can also use expressions to write more complex logic on column values in a query. These expressions can use mathematical and string functions along with basic arithmetic to transform values when the query is executed, as shown in this physics example.

### **Example query with expressions**

    SELECT particle_speed / 2.0 AS half_particle_speed

    FROM physics_data

    WHERE ABS(particle_position) * 10.0 > 500;

### **Select query with expression aliases**

    SELECT col_expression AS expr_description, …

    FROM mytable;

### **Example query with both column and table name aliases**

    SELECT column AS better_column_name, …

    FROM a_long_widgets_table_name AS mywidgets

    INNER JOIN widget_sales

    ON mywidgets.id = widget_sales.widget_id;

## Queries with aggregates (Pt. 1)

SQL also supports the use of aggregate expressions (or functions) that allow you to summarize information about a group of rows of data.

### Select query with aggregate functions over all rows

    SELECT AGG_FUNC(column_or_expression) AS aggregate_description, …

    FROM mytable

    WHERE constraint_expression;

### Common aggregate functions

|Function|Description|
| --- | --- |
|COUNT(*), COUNT(column)|A common function used to counts the number of rows in the group if no column name is specified. Otherwise, count the number of rows in the group with non-NULL values in the specified column.|
|MIN(column)|Finds the smallest numerical value in the specified column for all rows in the group.|
|MAX(column)|Finds the largest numerical value in the specified column for all rows in the group.|
|AVG(column)|Finds the average numerical value in the specified column for all rows in the group.|
|SUM(column)|Finds the sum of all numerical values in the specified column for the rows in the group.|

### Select query with aggregate functions over groups

    SELECT AGG_FUNC(column_or_expression) AS aggregate_description, …

    FROM mytable

    WHERE constraint_expression

    GROUP BY column;

The GROUP BY clause works by grouping rows that have the same value in the column specified.

## LESSON 10

### Queries with aggregates (Pt. 2)

One thing that you might have noticed is that if the GROUP BY clause is executed after the WHERE clause (which filters the rows which are to be grouped), then how exactly do we filter the grouped rows?

Luckily, SQL allows us to do this by adding an additional HAVING clause which is used specifically with the GROUP BY clause to allow us to filter grouped rows from the result set.

### Select query with HAVING constraint

    SELECT group_by_column, AGG_FUNC(column_expression) AS aggregate_result_alias, …

    FROM mytable

    WHERE condition

    GROUP BY column

    HAVING group_condition;

The **HAVING** clause constraints are written the same way as the **WHERE** clause constraints, and are applied to the grouped rows.

If you aren't using the **GROUP BY** clause, a simple **WHERE** clause will suffice.

## LESSON 11

### Order of execution of a Query

### Complete SELECT query

    SELECT DISTINCT column, AGG_FUNC(column_or_expression), …
    FROM mytable
    JOIN another_table
    ON mytable.column = another_table.column
    WHERE constraint_expression
    GROUP BY column
    HAVING constraint_expression
    ORDER BY column ASC/DESC
    LIMIT count OFFSET COUNT;

### Query order of execution

1. FROM and JOINs
2. WHERE
3. GROUP BY
4. HAVING
5. SELECT
6. DISTINCT
7. ORDER BY
8. LIMIT / OFFSET

## LESSON 12

### Inserting rows

### What is a Schema?

the database schema is what describes the structure of each table, and the datatypes that each column of the table can contain.

### Insert statement with values for all columns

    INSERT INTO mytable

    VALUES (value_or_expr, another_value_or_expr, …),

    (value_or_expr_2, another_value_or_expr_2, …),

    …;

### Insert statement with specific columns

    INSERT INTO mytable

    (column, another_column, …)

    VALUES (value_or_expr, another_value_or_expr, …),

    (value_or_expr_2, another_value_or_expr_2, …),

    …;

### Example Insert statement with expressions

    INSERT INTO boxoffice

    (movie_id, rating, sales_in_millions)

    VALUES (1, 9.9, 283742034 / 1000000);

## LESSON 13

### Updating rows

### Update statement with values

    UPDATE mytable

    SET column = value_or_expr,

    other_column = another_value_or_expr,…

    WHERE condition;

## LESSON 14

### Deleting rows

### Delete statement with condition

    DELETE FROM mytable

    WHERE condition;

## LESSON 15

### Creating tables

### Create table statement w/ optional table constraint and default value

    CREATE TABLE IF NOT EXISTS mytable (

    column DataType TableConstraint DEFAULT default_value,

    another_column DataType TableConstraint DEFAULT default_value,…

    );

### Table data types

|Data type|Description|
| --- | --- |
|INTEGER, BOOLEAN|The integer datatypes can store whole integer values like the count of a number or an age. In some implementations, the boolean value is just represented as an integer value of just 0 or 1.|
|FLOAT, DOUBLE, REAL|The floating point datatypes can store more precise numerical data like measurements or fractional values. Different types can be used depending on the floating point precision required for that value.|
|CHARACTER(num_chars), VARCHAR(num_chars), TEXT|The text based datatypes can store strings and text in all sorts of locales. The distinction between the various types generally amount to underlaying efficiency of the database when working with these columns.          Both the CHARACTER and VARCHAR (variable character) types are specified with the max number of characters that they can store (longer values may be truncated), so can be more efficient to store and query with big tables.|
|DATE, DATETIME|SQL can also store date and time stamps to keep track of time series and event data. They can be tricky to work with especially when manipulating data across timezones.|
|BLOB|Finally, SQL can store binary data in blobs right in the database. These values are often opaque to the database, so you usually have to store them with the right metadata to requery them.|

### Table constraints

|Constraint|Description|
| --- | --- |
|PRIMARY KEY|This means that the values in this column are unique, and each value can be used to identify a single row in this table.|
|AUTOINCREMENT|For integer values, this means that the value is automatically filled in and incremented with each row insertion. Not supported in all databases.|
|UNIQUE|This means that the values in this column have to be unique, so you can't insert another row with the same value in this column as another row in the table. Differs from the **PRIMARY KEY** in that it doesn't have to be a key for a row in the table.|
|NOT NULL|This means that the inserted value can not be **NULL**.|
|CHECK (expression)|This allows you to run a more complex expression to test whether the values inserted are valid. For example, you can check that values are positive, or greater than a specific size, or start with a certain prefix, etc.|
|FOREIGN KEY|This is a consistency check which ensures that each value in this column corresponds to another value in a column in another table.For example, if there are two tables, one listing all Employees by ID, and another listing their payroll information, the **FOREIGN KEY** can ensure that every row in the payroll table corresponds to a valid employee in the master Employee list.|

### Movies table schema

    CREATE TABLE movies (

    id INTEGER PRIMARY KEY,

    title TEXT,

    director TEXT,

    year INTEGER,

    length_minutes INTEGER

    );

## LESSON 16

## Altering tables

### Altering table to add new column(s)

    ALTER TABLE mytable

    ADD column DataType OptionalTableConstraint 
    
    DEFAULT default_value;

### Altering table to remove column(s)

    ALTER TABLE mytable
    DROP column_to_be_deleted;

### Altering table name

ALTER TABLE mytable

RENAME TO new_table_name;

## LESSON 17

### Dropping tables

### Drop table statement

    DROP TABLE IF EXISTS mytable;

