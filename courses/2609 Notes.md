Database
 - all data is stored in tables, made up of cols and rows
 - Each table has one or more columns, each col has a datatype, and each row has a value for each column
 - The data is structured in a particular way. A single item of data is stored in a name field
	 - A complete set of fields makes up a record, the key contains data unique to that record.
	 - All the records on one entity are stored in a table, and one or more tables then make up the database file

JDBC - Java Database Connectivity
 - The API that manages connecting to a database, issuing queries and commands, and handling result sets obtained form the database
 - Released as part of JDK1.1 in 1997, one of the first components developed for the Java persistence layer
 - Available under `java.sql.*` and `javax.sql.*`
	 - `java.sql.*` provides the API for accessing and processing data stored in a data source
	 - `javax.sql.*` is the extensions used for the Java EE requirements
 - the JDBC api allows to connect to multiple database sources under a single interface
	 - You only need to change the database driver and how you establish the connection when changing from different databases
 - Steps
	 - Import Packages - `import java.sql.*;`
	 - Load Driver - `Class.forName("org.apache.derby.jdbc.ClientDriver");`
	 - Establish Connection 
		 - `Connection con = DriverManager.getConnection(connectionString, databaseName, password);`
		 - Example connection string: `jdbc:derby://localhost:1527/FriendsDB`
			 - the RDBMS to be used is part of the protocol
			 - take note of the port where the RDBMS is running
			 - and also the URI is the name of the database to connect to
	 - Create and execute statement
		 - `Statement stmt = con.createStatement();`
		 - Can also use the PreparedStatement interface which precompiles SQL statements
	 - Retrieve results
		 - `ResultSet rs = stmt.executeQuery("SELECT * FROM PERSON_INFO");`
	 - Close connection
		 - `rs.close(); stmt.close(); con.close();`
 - Difference between Statement and PreparedStatement
	 - Statement
		 - used for executing a static SQL statement in java JDBC
		 - cannot accept parameters at runtime
		 - is slower since it's building the query every time it's run
	 - PreparedStatement
		 - used for executing a pre-compiled sql statement
		 - can be executed repeatedly with different with different parameters, therefore it's faster since it doesn't have to build the entire query every time it's run

Model View Controller
- Most webapps use the MVC design pattern where they separate the application logic from the user interface when designing software.
- Has 3 layers
	- Model - represents the business layer of the application as classes, the User table has a User class
	- view - Defines the representation of the application (Web / Desktop)
	- Controller - Manages the flow of data in the application
- HTTP response codes - indicate whether an HTTP request has been successfully completed
- sendRedirect vs RequestDispatcher
	- `sendRedirect()` - a method of HttpServletResponse
		- request is redirected to client and it will process the new URL
		- Client can see on which page it has been redirected since it's done in the client side
	- `RequestDispatcher`
		- Can be accessed from HttpServletRequest
		- Internally forwards the request to another servlet or JSP page
		- The client doesn't know which page is processed internally, since processing is done in the server side

# MVC
 - the separation of concerns
	 - separates the application logic from the user object, making the application logic be reusable
 - the model - represents the business layer of the application
 - view - defines the representation of the application
	 - is the html or the swing
 - controller - manages the flow of the application
	 - is the servlet in web
	 - controls what happens with the data