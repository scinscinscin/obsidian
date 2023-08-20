## Numerical datatypes
`INT[(width)] [UNSIGNED] [ZEROFILL]`
 - stores integers in the signed 32 bit range
 - if `UNSIGNED` is specified then it stores it in the positive 32 bit range
 - `width` - max value of 255
	 - has no effect on what is stored
	 - basically the minimum width of the integer when formatted
 - `ZEROFILL` - left-pad the values with zeros up to the specified length
	 - when used, it automatically adds `UNSIGNED` in the declaration since it only makes sense when used with positive numbers

`DECIMAL[(width[,decimals])] [UNSIGNED] [ZEROFILL]`
 - `width` ALSO contains `decimals`. `DECIMAL(4, 2)` can store between -99.99 and 99.99
 - if you try to store a value outside this range, it will be stored as the closes value int he allowed range
 - width is optional and the default is 10 when omitted, and a max `width` of 255
 - the max value of `decimals` should be two less than the value of width
	 - when `decimals` is not included, a value of zero is assumed
 - also aliased as types `DEC`, `NUMERIC` and `FIXED`

Smaller types require less storage space, disk and memory and speeds retrieval from disk
`BOOLEAN` - same as `TINYINT(1)`, and takes up one byte of storage
 - can also use `CHAR(0)` to achieve the same thing with 1 byte of storage
`TINYINT[(width)] [UNSIGNED] [ZEROFILL]`
 - stores values in the range of -128 to 127 and 0 to 255 when `UNSIGNED` 
 - requires one byte of storage
`SMALLINT[(width)] [UNSIGNED] [ZEROFILL]`
 - stores values in the range of -32768 and 32767 and 0 to 65535 when signed
 - requires two bytes of storage
`MEDIUMINT[(width)] [UNSIGNED] [ZEROFILL]`
 - -8388608 and 8388607 and 0 to 16777215 when signed
 - requires three bytes of storage
`BIGINT[(width)] [UNSIGNED] [ZEROFILL]`
 - 8 bytes of storage space
 - 64 bit signed and unsigned spaces

`FLOAT[(width, decimals) || (precision)] [UNSIGNED] [ZEROFILL]`
 - stores floating-point numbers
 - first syntax allows for an optional decimals and optional display width
 - second syntax allows for precision that controls the accuracy of the approximation measured in bits
	 - without parameters it stores 4 byte single precision floating point values
	 - precision values of between 25-33 make it behave as a `DOUBLE`

`DOUBLE[(width, decimals)] [UNSIGNED] [ZEROFILL]`
 - floating-point numbers
 - normal, eight-byte, double-precision floating point values
 - synonymous with `REAL` and `DOUBLE PRECISION`
 
## Date and time types
`DATE` - stores a date in the format of `YYYY-MM-DD`
 - must be input as year, month, and day triples
`TIME` - stores a time in the format `HHH:MM:SS`
 - must be inputted in the order of days `HH:MM:SS`
 - max value of `838:59:59`
`TIMESTAMP` - date and time pair in ISO8601 format
 - if you assign NULL to it, the `TIMESTAMP` column in a table can be automatically updated to the current date and time when the row is inserted or updated
 - developer selected `TIMESTAMP` column can be automatically updated when a row is inserted or updated
	 - if you have other `TIMESTAMP` columns in the table, set the ones that precede to have a constant default of 0
	 - automatically updating column - add a `DEFAULT CURRENT_TIMESTAMP` to the end of the column declaration
	 - automatically updating column when the row is updated - add `ON UPDATE CURRENT_TIMESTAMP`
	 - set column to the current time in creation or modification, then you can add `DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP`
 `YEAR[(digits)]`
 - stores either a two digit or 4 digit year
 - `digits` defaults to four when not provided
 `DATETIME` - `TIMESTAMP` but without the automatic update features

## String types
`CHAR[(width)]` - fixed length string of length `width`
 - when width is not provided, char(1) is assumed, max length of width is 255
 - all trailing spaces are ignored when retrieving and displaying values
	 - " " and "  " are the same string, and you can not use them as primary keys
	 - "leading space" and " leading space" are not the same thing
	 - should use `BLOB` or `TEXT` type if this behavior is unwanted
`VARCHAR(width)`
 - variable length strings up to a maximum width (max value of `width` parameter is 65535 characters)
 - incurs two bytes of overhead to store the string length
`BLOB` - common for storing large data up to 65535 bytes in length
 - data is treated as binary and no character set is assumed.
 - comparisons are case-sensitive, no trailing space removal behavior
`TEXT` - large string data objects
 - stores a variable amount of data up to 65535 bytes in length
 - identical as blob but has a default character set
 - case insensitive in comparisons

## Enum types
 - enumeration of string values
	 - compact way of storing values from a list of predefined values
	 - MySQL warns you if you try to store values that are not included in the list
 - `ENUM("value1", "value2")`
	 - has a maximum of 65535 values
	 - what's stored in the database is the integer representation
	 - can contain null unless you set `NOT NULL` when creating the table

## SET types
`SET('value1', "another_value")`
 - a set of string values, can be set to 0 or more values from the list up to a maximum of 64 different values
 - stored in the database as an integer representation
 - useful for storing a selection of choices from a list, such as user preferences

## Keys and Indexes
 - `PRIMARY KEY` clause declared in the `CREATE TABLE` statement
	 - uniquely identifies each row in a table
	 - creates a new file on disk that stores information about where the data on each row is stored called an index.
		 - speeds up searches that use the primary key
		 - mysql creates a structure that allows it to find rows that matches the primary key extremely quick. You can see this using the `SHOW INDEX FROM database_name;` command
			 - cardinality - the number of unique values for the index
	 - must be declared as `NOT NULL` since they must have a value for the row to be valid
 - can create other indexes in the table so that other searches on other columns can be fast and to avoid sequential scans
	 - `KEY artist_name (artist_name)`
		 - the column to index is in the parenthesis
	 - can add indexes after the table has been created
	 - can build an index on more than one column
		 - `KEY names (firstname, secondname, surname)`
		 - can use the `names` index for fast searching using combinations of the three name columns. `WHERE firstname="Thing" AND secondname = "Bruh" AND surname="Hamilton"`
		 - you can also use it when indexing using `firstname` only or `firstname` AND `secondname`
			 - basically in the order that they are defined in the parenthesis
			 - the leftmost column listed in the KEY must be in the query
			 - the query must contain no OR clauses for columns that aren't indexed
		 - indexes cost space on disk and need to be updated when data changes
		 - only add an index that will be used frequently, can always add indexes afterward
		 - list the column with the highest number of dupes at the left of the KEY clause to minimize index size
		 - the smaller the index, the faster it is
			 - you can use a prefix of the values of a column to create an index
				 - `KEY names (firstname(3), secondname(3), surname(10))`
				 - first three characters for firstname and secondname and 10 characters for surname