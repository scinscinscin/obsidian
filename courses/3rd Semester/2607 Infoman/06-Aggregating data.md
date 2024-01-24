- discovering how many rows there are on a table
- how many rows in a table share a property
- finding averages
- finding the maximum or minimum values of rows that meet some condition

**`DISTINCT` clause**
 - post-processing filter that allows you to remove duplicates
 - picking examples from the output of a query
 `SELECT DISTINCT artist_nanme FROM artist INNER JOIN album USING (artist_id);`
  - returns the artists who have made albums and reports one example from each artist
  - applies to the query output and removes rows that have identical values in the columns selected for output in the query

**`GROUP BY` clause**
 - sorts data into groups for the purpose of aggregation
	 - tells us how to put rows together into groups
 - occurs earlier in the query process than `ORDER BY`
`SELECT artist_name, COUNT(artist_name) FROM artist INNER JOIN album USING (artist_id) GROUP BY artist_name;`
- create an inner join between the `artist` and `album` tables using the `artist_id` as a common key between them, select the `artist_name` and `COUNT(artist_name)` as the columns and group the returned query based on the artist's name
	- results in rows for artists with the same name form a cluster, the distinct name forms one group
	- once the rows are grouped, they are treated in the rest of the query as they are one row
		- this is why the `SELECT` statement's results is one row per group
		- `COUNT()` tells us the properties of the group, in this case the number of rows that form each group

**Aggregate functions**
 - explore the properties of aggregated rows
 - `AVG()` - returns the mean of the values in the specified column for all rows in a group
 - `MAX()` - maximum value from rows in a group
	 - warmest day in a month when rows are grouped by months
 - `MIN()` - minimum value of rows in a group
	 - youngest student in a class when rows are grouped by class
 - `STD()` or `STDDEV()` - return standard deviation of values from rows in a group
 - `SUM()` - return the sum of values in a group

**`HAVING` clause**
 - a where clause for aggregated data
 - deciding how to form each group or cluster
 - must contain an expression or column that's listed in the `SELECT` clause