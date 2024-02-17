# GUIs
`java.awt`
 - Abstract Window Toolkit
 - allows us to create GUI objects like buttons, frames, textareas, etc.
 - First generation - AWT
 - Second generation - Swing
 - Third generation - JavaFX

`javax.swing`
 - part of Java Foundation Classes that is used to make window-based applications
 - built on top of AWT, but platform independent and lightweight components
 - supports pluggable look and feel, more powerful components, follows MVC
 - JAR
	 - a package file format used to group Java classes into one file for distribution
	 - similar to a ZIP file
	 - can be accessed and used in different operating system
	 - without manifest file
		 - `jar cvf File.jar *`
		 - `java -cp File.jar fullyQualifiedMainMethodClass`
	 - with manifest file
		 - `jar cvfm File.jar manif.txt *`
			 - where `manif.txt` looks like `Main-Class: package.class.with.main.method\n`
		 - `java -jar File.jar`


**Classes**
- Frame
	- a top level window with a border and title bar
	- uses BorderLayout as default layout manager
	- has resizable corners
- Panel
	- a type of container that provides a space
	- cannot be launched by itself, needs to exist inside another container
- Layout managers
	- used to position your Components inside your Containers
	- you can nest containers to customize your layout managers
	- AWT
		- FlowLayout
			- arranges components in a directional flow
			- used to arrange buttons in a panel, arranging them horizontally until no more buttons fit on the same line
		- BorderLayout
		- GridLayout
			- Lays out container's components in a rectangular grid
			- Container is divided into equal sized rectangles, and one component is placed inside each triangle
			- all components are equally sized on resize
		- CardLayout
		- GridBagLayout
	- Swing
		- BoxLayout
		- SpringLayout

**Events**
- are objects that describe what happens
- may be a button click, a mouse pass-over, or a shortcut or any interaction to a GUI component

Event Sources
 - are GUI components in which the user invoked an interaction
 - has methods that allow you to register event listeners with them
	 - When an event happens to the source, the source sends a notification of that event to all listener objects that were registered for that event
 - all data about the event is encapsulated in an event object, deriving from the class `java.util.EventObject`
 - Different sources can produce different kinds of events
 - allows us to register listener objects and send them event objects
 
 Event handlers
  - a method that is invoked every time an event is called
  - where you code the behaviour you want to do every time an event occurs

Event handling techniques
 - Event delegation model
	 - delegate the event handler to a different class, producing a loosely coupled GUI and Event handler package
 - Use of listeners
	 - listener are interfaces, once you implement an interface, you are required to override all methods in the interface
 - Use of adapter classes
	 - are partial implementations of the listener classes
	 - not all listener classes have an adapter class, only ones that contain two or more methods
 - Use inner classes
	 - for tightly coupled components, you declare the interface / adapter class inside the class they are going to be used in
 - Use of anonymous classes
	 - used to create objects on the fly that are anonymous, do not have any handler or object references
	 - you can access and execute their corresponding event handler, after which they are destroyed
	 - used where you want to have an efficient runtime
	 - create an adapter class object on the fly
 - Use of lambda expression
	 - allows you to pass unnamed functions as parameters to methods, simplifying anonymous class
	 - `b.addActionListener(e -> System.out.println("Handled by Lambda Expr"))`

# Database
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

# MVC
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
