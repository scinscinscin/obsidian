---
tags:
  - reviewer
course: ICS2607 - Information Management
period: Prelim
assessment: Long Exam 3 and 4
---

**Data types**
 - define what kind of value a column can hold
	 - integer data / character data / monetary data / datetime data
# **Data definition language**
 - `CREATE DATABASE [name_of_database];`
	 - `SHOW DATABASES;` - show the current database
	 - `USE [name_of_database];` - to select the database created
	 - `DROP DATABASE database_name;` - delete the database
 - `CREATE TABLE` - create a new table in the user's schema
	 - `SHOW TABLES;` - show the tables in the current database
	 ```sql
		 CREATE TABLE table_name(
			 column_name datatype(size) constraint_name,
		 );
	```
	 -  `ALTER TABLE` - modify a table definition
		 - add / modify / delete attributes or constraints
		 - How to add a column in a table
			 - `ALTER TABLE table_name ADD column_name datatype;`
		 - How to remove a column in a table
			 - `ALTER TABLE table_name DROP COLUMN column_name;`
		 - Change the data type of a column in a table
			 - `ALTER TABLE table_name MODIFY COLUMN column_name datatype;`
		 - How to add a primary key to a table
			 - `ALTER TABLE table_name ADD PRIMARY KEY(column_name);`
		 - How to add a foreign key to a table
			 - `ALTER TABLE table_name ADD FOREIGN KEY(column_name) REFERENCES table_name2;`
	 - `CREATE TABLE AS` creates a new table based on a query in the user's database
		 - create a new table from existing information
		 - ``CREATE TABLE new_table AS (SELECT * FROM old_table);``
	 - `DROP TABLE table_name;` - permanently delete a table
 - `CREATE INDEX` - create an index for a table
 - `DROP INDEX` - permanently delete an index

## **Relations**
 - Stored relations -> tables
	 - also called base relations and base table
 - Temporary results -> result sets
 - Virtual relations -> **views**
	 - a view is a virtual relation on the result set of a select statement
	 - contains rows and columns, just like a real table
	 - can contain fields from one or more real tables in the database
	 - `CREATE VIEW` - create a dynamic subset of rows and columns from one or more tables
		 - We can also distinguish between attributes by giving them a different name
	```sql
	CREATE VIEW view_name AS SELECT column_list FROM table_name WHERE condition_list;
	CREATE VIEW view_name (column1, column2) AS SELECT col1, col2 FROM table_name WHERE condition_list;
	```
	 - **Querying views**
		 - A view can be used inside another query or inside another view to present exactly the data that we want to the user
		 - `SELECT model FROM blue_cars WHERE year=1989;` is the same as `SELECT model FROM cars WHERE color='blue' AND year=1989;`
	 - **Modifying views**
		 - modifying the underlying tables that make up the view
		 - Inserting into a view
			 - is possible but would leave the columns not present in the view as NULL
			 - `INSERT INTO blue_cars (model, year) VALUES ('my_car', 1990);` would create a new row but the `color` attribute would be NULL
				 - To solve, create the view also containing `color` in the column list, and when inserting, also include `blue` as the color
				 - `INSERT INTO blue_cars (color, model, year) VALUES ('blue', 'my_car', 1990);`
		 - Deleting and Updating from a view - works intuitively, any row matched with the `WHERE` clause is updated / deleted in the underlying table
	 - `DROP VIEW view_name;` - permanently delete a view
		 - does not affect any rows of the underlying relation / table
	
## **Constraints**
 - Used to specify rules for the data in a table
 - if there is a violation between the constraint and data action, the action is aborted
 - can be specified when the table is created, or using the ALTER TABLE statement
 - `NOT NULL` - ensure that a column will not have null values
 - `UNIQUE` - ensure that a column will not have duplicate values
	 - a UNIQUE column can still be null, although only 1 row can be null
 - `PRIMARY KEY` - define a primary key for the table
	 - A combination of **NOT NULL** and **UNIQUE**
	 - A column / combination of two columns have a unique identity which helps to find a record in the table more easily
 - `FOREIGN KEY` - define a foreign key for the table
	 - Ensures the referential integrity of the data in one table to match values in another table
 - `DEFAULT` - define a default value when none is given
	 - Specifies a default value for the column
 - `CHECK` - validate the data in an attribute
	 - Ensure the value in a column meets a specific condition

#  **Data manipulation language**
 - Commands
	 - `INSERT` - insert rows into a table
		 ```sql
		 INSERT INTO table_name (col_name, col_name2) VALUES ('value1', 'value2');
		```
	 - `INSERT SELECT` - insert rows from one table to another table that already exists
		 - the table must already exist, and will error if it doesn't
		 - **SQL allows you to copy the contents of selected table columns so that the data doesn't need to be re-entered manually, but column characteristics must match**
		 ```sql
		 INSERT INTO target_table (target_columns) SELECT source_columns FROM source_table;
		```
	 - `SELECT` - select attributes from rows in one or more tables or views
		 - `GROUP BY` - group selected rows based on on one or more attributes
			 - groups rows into smaller collections, the aggregate function will then summarize the data within each smaller collection
			 - `HAVING` - restricts the selection of grouped rows based on a condition
				 - basically a `WHERE` for a `GROUP BY`
				 - `SELECT Email FROM Person GROUP BY Email HAVING COUNT(Email) > 1;`
					 - List emails that are duplicated in the Person table
		 - `ORDER BY` - orders the selected rows based on one or more attributes
		 ```sql
		 SELECT list, of, columns FROM table_name WHERE condition AND condition2 ORDER BY column1 ASC;
		```
	 - `SELECT INTO` - copy the contents of the selected table into a new table
		 - **creates a new table if it doesn't exist already**
		 - Copy all rows and columns from `old_table` to `new_table`
			 - `SELECT * INTO new_table FROM old_table;`
		 - Copy all rows and columns from `old_table` to `new_table` in another database
			 - `SELECT * INTO new_table IN 'another_database' FROM old_table;`
		 - Copy only a few columns into the new table
			 - `SELECT columnlist INTO new_table FROM old_table;`
		 - Copy only a group of rows into the new table
			 - `SELECT * INTO new_table FROM old_table WHERE condition;`
		 - Copy data from more than one table into the new table
		 ```sql
		 SELECT c.name, o.id INTO CustomerOrders FROM customers AS c LEFT JOIN orders o ON c.customer_id=o.customer_id;
		```
	 - `WHERE` - restricts the selection of rows based on a condition
	 - `UPDATE` - modify an attribute's values in one or more table's rows
	 ```sql
		 UPDATE table_name SET columnname=new_value WHERE condition AND condition;
	```
	 - `DELETE` - delete one or more rows from a table
		 - `DELETE FROM table_name WHERE condition_list;`
 - Operators 
	 - `=, <, >, <=, >=, <>, !=` - used in conditional expressions
	 - `AND, OR, NOT` - used to join multiple conditional expressions together
	 - `BETWEEN` - check whether an attribute is within a range
	 - `IS NULL` - check whether an attribute is NULL
	 - `LIKE` - check whether an attribute matches a given string pattern
		 - *is basically regex* where the `*` matches multiple characters and `_` matches a single character
		 - `J*` - matches John and Jabol
	 - `IN` - checks whether an attribute value matches any value within a value list
		 - `SELECT * FROM Customers WHERE Country IN ('Germany', 'France', 'UK');`
	 - `ALL` - compares an attribute against all values in a list
		 - `SELECT * FROM Teachers WHERE age > ALL (SELECT age FROM Students);`
			 - get all teachers whose age is greater than the age of all students
	 - `ANY` - like ALL but returns true for a match with just once student
	 - `EXISTS` - check whether a subquery returns any rows
	 - `DISTINCT` - Limit values to unique values
		 - `SELECT DISTINCT column_name FROM table_name;`
	 - `TOP` - limit the number of values selected
		 - `SELECT TOP 3 * FROM Customers;`
		 - `SELECT * FROM Customers LIMIT 3;`
 - Aggregations
	 - `COUNT` - return the number of rows with non-null values for a given column
		 - `SELECT COUNT(column_name) AS cnt FROM table_name WHERE condition;`
	 - `MIN` - returns the minimum attribute value found in a given column
	 - `MAX` - returns the maximum attribute value found in a given column
	 - `SUM` - returns the sum of all values for a given column
	 - `AVG` - returns the average of all values for a given col

# SQL Aliases
 - makes the output more readable
 - An alias is an alternative name given to a column or table in any SQL statement
	 - can temporarily rename a table or a column name to make them more readable
		 - `SELECT column_name AS c FROM table_name;`
		 - `SELECT column_name FROM table_name AS t;`
	 - Useful when dealing with dealing with multiple tables in a single query as it can make them shorter
	 - Used with aggregation functions since by default they take the name of the column
 - An alias is sometimes necessary when JOINing two tables, ie, if they have the same column names
 - Example
	 - `SELECT name, CONCAT(city, postal_code, country) AS address FROM customers;`
		 - The column name would be `CONCAT(city, postal_code, country)` without the alias
# SQL Join
 - Used to combine rows from two or more tables based on a common field between them
 - `INNER JOIN` - returns all rows when there is atleast one match in both tables
	 - Cannot contain null
 - `LEFT JOIN` - returns all rows from the left table and the matched rows from the right table
	 - Can contain null in the right side for rows in the left table that do not match with a row on the right side
	```sql
	-- List the firstName, lastName, city and state of each person
	-- and show null if they don't have an address in the Address table
	SELECT firstName, lastName, city, state FROM Person LEFT JOIN Address ON Person.personId = Address.personId;


	-- List all customers who haven't made orders
	-- We use LEFT JOIN to list all customers with any orders, then filter by those who haven't made any.
	SELECT c.name AS Customers FROM Customers c LEFT JOIN Orders o ON c.id = o.customerId WHERE o.id IS NULL;
	```

 - `RIGHT JOIN` - return all rows from the right table and the matched rows from the left table
 - `FULL JOIN / FULL OUTER JOIN` - returns all rows when there is a match in one of the tables
	 - Can contain null in both sides
	 - DOES NOT exist in MySQL
 - `UNION` operator
	 - used to combine the result-set of two or more select statements
	 - the `SELECT`s used in the UNION must have the same number of columns, and similar datatypes, they must also have the same column order
		 - the column names of the result set of a UNION is equal the column names in the first select statement in the UNION
	 - selects only distinct values by default. To allow duplicates, use `UNION ALL`.
	```sql
	SELECT City, Country FROM Customers WHERE name LIKE 'L%' 
	UNION ALL 
	SELECT City, Country FROM Suppliers WHERE name LIKE 'J%';
	```

# SQL Subqueries
 - An inner query is a query inside another SQL query
 - used to return data that will be used in the main query as a condition to further restrict the data to be retrieved
 - can be used with the SELECT, INSERT, UPDATE, and DELETE statements, and with operators
	 - usually added within the WHERE clause of another SQL select statement
	 - is executed before its parent query
 - Guidelines
	 - A subquery **must be enclosed in parentheses** and can be named by adding an identifier after the parenthesis
		 - CANNOT be implemented as soon as a SELECT keyword is called
	 - A subquery must be placed on the right side of their comparison operator
	 - They cannot manipulate their results
	 - Use single row operators with single row subqueries
 - Example:
```sql
-- List all employees that earn more than their manager
SELECT name AS Employee FROM employee e WHERE e.managerId IS NOT NULL AND
	-- get the salary of their manager in the subquery
    (SELECT salary FROM employee e_1 WHERE e_1.id = e.managerId) < e.salary;
```