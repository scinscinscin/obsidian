JDBC
	- is available in the `java.sql` package
	- make a database driver available in the application
```java
// mysql-j-connector version 5 and below uses com.mysql.jdbc.driver
Class.forName("com.mysql.cj.jdbc.Driver");
String url = "jdbc:mysql://localhost:3306/unsent";
Connection connection = DriverManager.getConnection(url, "root", "");
ResultSet result = connection.createStatement().executeQuery("SELECT * FROM posts");
while(result.next()){
	System.out.println(result.getString("body"));
}
```

## Connection pooling
 - create a collection of connection objects and store them in another object that's known as a database connection pool.
 - all connection objects are shared by the users of a webapp
 - on init, create a `ConnectionPool` object that contains multiple `Connection` objects
 - the thread created by the servlet gets a Connection object from the pool, which is used to access the database

## Java Persistence API
 - more of an orm that runs on top of JDBC
 - automatically create database tables based on relationships between business objects
 - convert between objects and rows in a relational database
 - perform joins to satisfy relationships between objects
 - Objects are known as entities and are managed by the entity manager
	 - you code annotations in the class like mikroorm
	 - are just POJOs with annotations, and can still use the classes without JPA

### Configure on how to work with JPA
 - add a jdbc driver for the database
 - add the JPA library that you want to use
	 - EclipseLink and Hibernate are both included
 - add a persistence unit
	 - tells JPA how to connect to a database

### How to apply decorators in EntityClasses
 - Every EntityClass has to be included in the `persistence.xml` file under the persistence unit using the class element.
 - `@Entity` decorator - tells jpa that the class defines an entry that should be stored in a database
 - `@Table(name = table_name_here)` - overrides the default table name
	 - default - same name for the table in the database as in the name of the class
 - `@Id` - the following field is a primary key for the entity
 - `@GeneratedValue` - tells JPA to automatically generate values for the primary key
	- has a strategy attribute to determine which to use
 - `@Column(name = column_name_here)` - override the default column name, the default is the name of the fields in the class
 - **Relations**
	 - `@ManyToOne` - many of the current class can be assigned to one of the remote class
	 - `@OneToMany` - fanout
		 - `fetch` - determines when the JPA loads the many entities
			 - defaults to lazy loading - empty by default, but fetches by the time you access
			 - `FetchType.EAGER` - it should load all items of the relation
		 - `cascade` - how to handle updating the relation when the current class is updated
			 - `CascadeType.ALL` - apply any updates to relations as well
				 - aka a new insert, it should update the table of the relation
				 - deletes also cascade automatically
 - **DateTime**
	 - Must use the `@Temporal` annotation to specify it's SQL data type
		 - `TemporalType.DATE` - should store the date only
		 - `TemporalType.TIME`  - should store the time only
		 - `TemporalType.TIMESTAMP` - both date and time

**See below for an example of a EntityClass**

## EntityManager
 - retrieve an entity by primary key
	 - get an entity manager from the EMF
		 - retrieve an object by it's primary key using the find method
			 - first parameter - the type of entity you want to find
			 - second parameter - value for the primary key
			 - returns null if it was not found
			 - JPA automatically converts the result set to the correct type of object
			 - need to close the entity manager when you're done
			```java
			public class DBUtil{
				public static EntityManagerFactory getEmFactory(){
					// unit name here must match the unit name defined in the persistence.xml file
					Map<String, String> properties=new HashMap<String, String>();
					properties.put("javax.persistence.jdbc.driver","com.mysql.jdbc.Driver");
					properties.put("javax.persistence.jdbc.url", "jdbc:mysql://localhost:3306/java_database");
					properties.put("javax.persistence.jdbc.user", "root");
					properties.put("javax.persistence.jdbc.password", "");
	            
			        EntityManagerFactory emf = Persistence.createEntityManagerFactory("my_persistence_unit", properties);
					return emf;
				}
			}
			```

### Getting data
 - JPA converts between objects and sql
	 ```java
	 // EntityManagers are not thread safe, need to create entity managers for each method that needs one
	 EntityManager em = emf.createEntityManager();
	 // Will throw runtime errors if the first parameter is not an entity || if the 2nd parameter is not of the valid type
	 User user = em.find(User.class, userId);
	```
 - JPQL - java persistence query language
	 - used to retrieve entities based on a column other than the primary key
	 - object oriented query language defined in the JPA spec
	 - uses **path expressions** to explore properties between relations
	 - `em.createQuery()`
		 - first parameter is a query string
		 - 2nd parameter is an optional Result class
	```java
	TypedQuery<Invoice> q = em.createQuery("SELECT i from Invoice i WHERE i.isProcessed = 'n'", Invoice.class);
	// retrieve the list of invoices using the getResultList() method of the TypedQuery object. note that invoices could be null depending on implementation
	List<Invoice> invoices = q.getResultList();
	// throws NoResultException when there it doesn't find any result
	// throws NonUniqueResultException when the query returns more than one result
	Invoice invoice = q.getSingleResult();
	em.close(); // make sure to clean up to avoid leaks
	```
	 - you can use **parameterized queries** to prevent SQL attacks
	 ```java
	 TypedQuery<User> q = em.createQuery("SELECT u FROM User u WHERE e.email = :email", User.class);
	 q.setParameter("email", "scinorandex1@gmail.com");
	 User user = q.getSingleResult();
	 em.close();
	```

### Modifying data
 - uses transactions so you can rollback changes based on commits
	 - ensures data integrity and that data isn't left in an inconsistent state
 - entity manager has a `getTransaction()` method that returns an `EntityTransition` object
	 - has a `begin()` method and a `commit()` method when you're done or a `rollback()` method to rollback the changes
	 - the data is also saved when you call the `flush()` method or if JPA saves it automatically, thus you explicitly need to call `rollback()` when something goes wrong
	```java
	EntityTransaction trans = em.getTransaction();
	trans.begin();
	em.persist(user); // add a single user
	em.merge(user); // update an existing user
	em.remove(em.merge(user)); // delete an existing user
	trans.commit();
	em.close();
	```


### Example Entity Class
```java
package me.lancegulinao.models;

import java.io.Serializable;
import javax.persistence.Column;
import javax.persistence.Entity;
import javax.persistence.Id;
import javax.persistence.Table;

@Entity
@Table(name = "post")
public class User implements Serializable {
    private static final long serialVersionUID = 1L;
    @Id
    @Column(name = "id")
    private Integer id;

    @Column(name = "firstName")
    private String firstName;

    @Column(name = "lastName")
    private String lastName;

    @Column(name = "email")
    private String email;

    public User() {
    }

    public User(Integer id) {
        this.id = id;
    }

    public User(Integer id, String firstName, String lastName, String email) {
        this.id = id;
        this.firstName = firstName;
        this.lastName = lastName;
        this.email = email;
    }

    public Integer getId() {
        return id;
    }

    public void setId(Integer id) {
        this.id = id;
    }

    public String getFirstName() {
        return firstName;
    }

    public void setFirstName(String firstName) {
        this.firstName = firstName;
    }

    public String getLastName() {
        return lastName;
    }

    public void setLastName(String lastName) {
        this.lastName = lastName;
    }

    public String getEmail() {
        return email;
    }

    public void setEmail(String email) {
        this.email = email;
    }

    @Override
    public int hashCode() {
        int hash = 0;
        hash += (id != null ? id.hashCode() : 0);
        return hash;
    }

    @Override
    public boolean equals(Object object) {
        // TODO: Warning - this method won't work in the case the id fields are not set
        if (!(object instanceof User)) {
            return false;
        }
        User other = (User) object;
        if ((this.id == null && other.id != null) || (this.id != null && !this.id.equals(other.id))) {
            return false;
        }
        return true;
    }

    @Override
    public String toString() {
        return "me.lancegulinao.models.User[ id=" + id + " ]";
    }
    
}


```