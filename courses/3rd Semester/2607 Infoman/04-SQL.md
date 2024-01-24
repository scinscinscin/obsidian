 - only database language in widespread use
 - MySQL supports many features but also includes non standard features that give more control over the db server

`USE database_name;` - load a database and select it as the active
 - `SELECT DATABASE();` - verify which database is active
 - `SHOW DATABASES:` - list the databases that you can access
	 - can use a `LIKE` clause to pattern match the name of the database
 - `SHOW TABLES;` - explore what tables make up the selected database
 - `SHOW COLUMNS FROM table_name;` - explore what columns make up a table
	 - alternatively can pick `DESC table_name;`
	 - shows the field_name, variable type, if it's nullable, whether it's a primary / foreign key, the default
 - `SHOW CREATE TABLE table_name;` - see the statement used to create a table

## SELECT statement
 - most basic form reads the data in all rows and columns of a table
	 - `SELECT * FROM table_name;`
 - you can list ethe columns you want, separated by commas which is useful when combined with alias in advance queries
 - you can avoid using the use command by specifying the database alongside the table (can be used with all queries)
	 - `SELECT * FROM database_name.table_name;`
 - `WHERE` clause - choose which rows are returned form a SELECT statement based on a condition
	 - `SELECT * FROM artist WHERE artist_name = "some_name";`
	 - `SELECT artist_name FROM artist WHERE artist_id < 5;`
		 - equals operator, greater than, gte, less than, lt, and not equal
	 - `LIKE` operator - find matches that being with a prefix, contain a string, or end in a suffix. pattern matching strings.
		- `WHERE album_name LIKE "Retro%"`
		- only used with strings, must meet the pattern in the string that follows
		- if you want to match one wildcard character then you can use the underscore character
			- `LIKE "R__ %"` - a 3 letter word beginning with R then a space then any string
	- Combine two or more conditions using Boolean Operators `AND`, `OR`, `NOT`, `XOR`
		- `WHERE condition_one AND condition_two;`
			- the and operator restricts the results to those rows that meet both conditions
		- OR operator - used to find rows that matches at least one of several conditions
		- You can combine `AND` and `OR` - make the precedence clear using parenthesis
			- `WHERE condition_one OR (condition_two AND condition_three);`
			- makes evaluation order clear
		- NOT operator - negates a Boolean statement
			- NOT operators should follow a parenthesis containing the expression that they wish to negate since the precedence is hard to follow otherwise
- `ORDER_BY` clause - control how the result is displayed
	- sorting has no effect on what rows are returned but the order they are returned
	- clause indicates that sorting is required, followed by the column that should be used as the sort key
		- `ORDER BY time, track_name`
		- sorts by the output from the track table by ascending track_length and breaks ties in track_length by using the track_name alphabetically
		- you can add `DESC` after a column name to signify that it should be sorted in descending order. Same goes for `ASC`
	- multiple columns in an order by clause when you're sorting people's names
	- MySQL ignores the case of characters when using `ORDER BY`. if you want to sort to behave like ASCII, then you need to add `BINARY` after `ORDER BY`
	- Sorting is done depending on the column type
		- you can force it to behave differently using the CAST function
			- `ORDER BY CAST(time AS CHAR)`
				- AS BINARY - sort as binary
				- AS SIGNED - signed integer
				- AS UNSIGNED - unsigned integer
				- AS CHAR - as character string
				- AS DATE - as date
				- AS DATETIME - sort as a date and time
				- AS TIME - sort as time
- `LIMIT` clause - limit the number of rows returned from a SELECT statement
	- restricts the output, saving the cost of buffering, communicating and displaying the reset of the tracks
	- return a fixed number of rows beginning anywhere in the result set
		- `LIMIT 5,5` - five rows but the first is displayed to be the sixth row of the answer set. The 2nd parameter dictates how many to return. If you want to return everything after a certain point you can use a large integer. `LIMIT 150, 9999`
		- `LIMIT 10 OFFSET 5`

### Aliases
 - provide a shorthand way of expressing a column / table / function name
 - write shorter queries / express queries more clearly
 - use one table in two or more ways in a single query
 - access data more easily from programs
 - use special types of nested queries

**Column Aliases**
 - cannot be used in a WHERE clause
 - at most 255 characters in length
`SELECT artist_name AS name FROM artist;`
artist_name is aliased as name
 - improving the expression of your queries, and reducing the number of characters you need to type
 - the new name might be more useful to the users
`SELECT CONCAT(artist_name, " recorded ", album_name) AS recording FROM artist INNER JOIN album USING (artist_id);`
 - join `artist` and `album` using `artist_id` and create a new table with a column called `recording` that formatted using the `CONCAT()` function

**Table Aliases**
 - alias table names instead of column names
 `SELECT al.artist_id FROM album AS al INNER JOIN artist AS ar USING (artist_id) WHERE al.album_name = "name_of_album"`
  - aliases `artist` table as `ar` and `album` as `al`
  - inner joins them using the `artist_id` column
  - selects the columns to return using the aliased table names


### Joining Two Tables
**`INNER JOIN` - has two table names beside it**
 - `USING` - indicates which columns hold the relationship between the two tables
	 - `artist INNER JOIN album USING (artist_id)`
	 - the column that holds the relationship between the tables is artist_id, there is a column with this name in both the `artist` and `album` name
	 - for each artist_id in the artist table, the server finds all the entries in the album table that have this value of artist_id and forms a new temporary table from these two sets
	 - this syntax only works when two tables share a column with the same name that you can use in the join condition
	 - the result rows shown are those where the join column match between the tables
		 - rows from one table that don't have a match in the other table are ignored. 
	 - any column that you specify must be unambiguous (specify using `table_name.column_name`)
	 - MySQL will permit you to omit the `USING` clause but you shouldn't do it because the results won't make sense *(they return a cartesian product)*
	 - the columns following the USING clause must be surrounded by parenthesis
 - Alternative syntaxes
	 - `SELECT artist_name, album_name FROM artist INNER JOIN album ON artist.artist_id = album.artist.id;`
		 - replaces the `USING` clause and the columns that follows explicitly refer to the table name when selecting columns
	 - `SELECT artist_name, album_name FROM artist, album WHERE artist.artist_id = album.artist_id;`

`UNION` statement
 - allows you to combine the outputs of more than one `SELECT` statement to give a consolidated result set
 - useful when you want to produce a single list from more than one source / create lists from a single source that are difficult to express in a single query
 - the output is labeled with the names of the columns or expressions from the first query (can use column aliases to change this)
 - queries should output the same number of columns and will throw an error if they have different numbers of columns
 - matching columns should have the same type
 - results returned are unique (there is an implicit `DISTINCT` operation)
	 - can use `UNION ALL` to show duplicates
 - `ORDER BY` clauses in subqueries without a `LIMIT` clause are not parsed out of efficiency
	 - they should be placed in the overall query to ensure they run

`LEFT JOIN`
 - each row in the left table is processed, with the matching data from the second table if it exists and NULL values if there is no matching data in the second table
 - `SELECT track_name, played FROM track LEFT JOIN played USING (artist_id, album_id, track_id) ORDER BY played DESC`
	 - will return the name of all tracks and the time they were played, ordered descending with NULL values being at the bottom
	 - the left table is the driving table and drives the process
 - can use the `USING` or `ON` clauses that `INNER JOIN`s can use

### Nested Queries
 - a way of merging data but is slower than a join
`SELECT track_name FROM track INNER JOIN played USING (artist_id, album_id, track_id) WHERE played = (SELECT MAX(played) FROM played);`
 - merge tracks with played based on the following IDs but filter for the track that's most latestly played, returning the track_name only
**ANY** - when used in a filter, at least one of the results of the subquery has to match the filter
 - `SELECT * from engineer WHERE years > ANY (SELECT years FROM producer)`
	 - select engineer whose years is larger than the smallest years of producer
 - also aliased as `SOME`
 - provides power in expressing nested queries
**ALL** - returns values that satisfy ALL the conditions
 - `SELECT * FROM engineer WHERE years > ALL (SELECT years FROM producer)`
	 - returns all engineers that are older than all producers
 - if it's false for any value, it's false
 - it's only true if it's true for all values
 - if the table in the subquery is empty, the result is always true

`SELECT produder_name, years FROM producer WHERE (producer_name, years) IN (SELECT engineer_name, years FROM engineer)`
 - create a subtable in the `SELECT engineer_name, years FROM engineer` query that contains the `engineer_name, years` for each row
 - group the `producer_name` and `years` columns in the producer table and check if they exist in the created subtable using the `IN` keyword
	 - referred to as row subquery syntax

**Correlated subquery**
 - a table is used in the outer query is referenced in the subquery
 - often used alongside the IN statement, almost always used with `EXISTS` and `NOT EXISTS` clauses
 - `EXISTS` returns true if there is at least one row in the subquery
	 - `NOT EXISTS` does the opposite
	 - `SELECT artist_name FROM artists WHERE EXISTS (SELECT * FROM album WHERE album_name = artist_name);`
	 - tables listed in the outer query is legally allowed to be access in the subquery
		 - the current value of artist_name can be accessed inside the subquery

**FROM clause**
`SELECT producer_name, months FROM (SELECT producer_name, years * 12 AS months FROM producer) AS prod;`
 - the subquery generates a table containing the `producer_name` and `months` column which was derived from the years by multiplying it by 12
 - the outer query returns the same thing
 - the derived table must have an alias, which in this case is `prod`
	 - mysql complains if you omit the alias

If you want to save values that are returned from queries, you should use user variables
`SELECT @artist:=artist_name FROM artist WHERE artist_id = 1;`
 - creates a user variable called artist and is denoted as a user variable using the @ character
 - the value is assigned using the := operator
 - can be accessed using @artist
`SELECT @counter:=0, @age:=23;`
 - defines two rows at once

## INSERT statement
 - two types
	 - adding data in batches
		 - giving mysql all the data you want to insert in one statement helps it optimize the insertion process
		 - `INSERT INTO shuffle (artist_id, album_id, track_id) SELECT artist_id, album_id, track_id FROM track ORDER BY RAND() LIMIT 10;`
			 - select 10 random entries from track by ordering them randomly and insert them into shuffle
			 - `RAND()` - returns a pseudorandom number in the range of 0-1
	 - adding data as you use the server
		 - `INSERT INTO database_name VALUES (values here...);`
			 - need to remember the column order
			 - need to provide a value for each column
			 - if you change the table structure, you need to change the insert statements
		 - `INSERT INTO album (artist_id, album_id, album_name) VALUES (7, 2, "some_name_here");`
			 - readable and flexible, need to know the column names beforehand
			 - omitted columns will be set to default values beforehand
				 - defaults can cause duplicated rows 
		 - `INSERT into tableName SET columnName = columnKey, anotherColumnName = anotherColumnValue;`
 - `MAX()` - aggregate function, tells the maximum value of the column supplied as the parameter. `SELECT MAX(artist_id) FROM artist;`
 - can use **`AUTO_INCREMENT`** shortcut to automatically assign the next available identifier
	- creates a unique identifier for a row without running a `SELECT` query
	- `artist_id SMALLINT(5) NOT NULL AUTO_INCREMENT`
		- can add it at the end of a column definition to make it autoincrement when provided a null value
		- `INSERT INTO artist VALUES (NULL, "some prop");`
		- `NOT NULL` is required
		- you can insert negative values if the column was not defined as unsigned
		- requirements
			- there can only be one auto increment column
			- the column must not have a default value and it must be indexed

## DELETE statement
 - remove one or more rows from a database (does not remove the table itself)
 - simple use is to remove all rows in a table
	 - `DELETE FROM table_name;`
 - to remove one or more rows, but not all rows, need to filter using a `WHERE` clause
	 - `DELETE FROM table_name WHERE condition;`
 - we can delete everything from multiple tables in a single DELETE statement
 - you can use `ORDER BY` and `LIMIT` with delete
	 - limit the number of rows deleted
	 - `DELETE FROM table_name ORDER BY column_name LIMIT number;`
 - remove all rows with `TRUNCATE TABLE table_name;`
 - deleting multiple rows at once
	 - `DELETE track, album FROM artist, album, track WHERE artist_name = "artist_name" artist.artist_id = album.artist_id AND...;`
		 - Delete from some tables (track, album) using another table (artist) as the driving table

## UPDATE statement
 - used to change data
 - simplest form is to change all the rows int he table
	 - `UPDATE artist SET artist_name = UPPER(artist_name);`
		 - `UPPER()` is a mysql function that returns the uppercased version of the text passed as the parameter
		 - You can set to NULL to return the column back to its default value

## Replacing data
 - delete an existing row using it's primary key and insert a new replacement using the same primary key
 - update a row using its primary key, replacing some or all of the values except the primary key
 - `REPLACE` statement
	 - you can't `INSERT` a new row if there is an existing row int he table with the same primary key but you can with a `REPLACE` query
	 - `REPLACE artist VALUES (2, "artist_2_new_name_here");`
		 - 2 rows were affected, the old row was deleted and the new row was inserted
		 - `REPLACE INTO artist VALUES (2, "artist_2_new_name_here");`
		 - `REPLACE INTO artist (artist_id, artist_name) VALUES (2, "artist_2_new_name_here");`
		 - `REPLACE artist (artist_id, artist_name) VALUES (2, "artist_2_new_name_here");`
		 - has the same syntaxes as `INSERT`
		 - can also do bulk replacements like insert
	 - doesn't make sense if the table has no unique identifier

## Creating and using databases
`CREATE DATABASE database_name;`
 - msyql creates a new directory under the data directory for the new database and stores a file called db.opt that lists the database options
 - you can add `IF NOT EXISTS` after `CREATE DATABASE` and `database_name` to avoid database already exists errors.

## Managing tables
**Creating a new table**
- you can add `type` parameter before the semicolon to specify the table type that you want to use
- `CREATE TABLE new_table_name LIKE old_table_name;`
	- Creates a new table with the same column types and properties from an old table
- `CREATE TABLE new_table_name SELECT * from artist`
	- Creates a new table with the same column types and properties **and data** from an old table
	```sql
		// you can also add IF NOT EXISTS before the table name
		CREATE TABLE table_name(
			// a list of one or more columns to add to the table
			column_name PROPERTIES,
			PRIMARY KEY (column_name_chosen_as_primary_key)
		);
	```
**Syntax for defining database columns**
```
column_name type [NOT NULL | NULL] [DEFAULT <value>]
type - defines how and what is stored in the column
NOT NULL - a row isn't valud without a value for the column
NULL / omit - a row can exist without a value for the column
DEFAULT <value> - populates the column when you don't provide data
                - value must be a constant except if the column is a TIMESTAMP
                - can be used with not null
```
**Column comments** - add a comment to a column, displayed when you use the `SHOW CREATE TABLE` command
**Foreign key constraints** - check whether the data in one or more columns matches data in another table
**Create temporary tables**
 - `CREATE TEMPORARY TABLE` statement
 - will automatically be dropped when the monitor connection is closed
`AUTO_INCREMENT` - starting value
