- keeping track of users as they move around a website
- HTTP doesn't maintain state thus it's a stateless protocol
- Servlets automatically add a unique session id to a request if it doesn't have it
	- the server uses the session id to relate each browser request to the session object
	- a session object is used to store the data for the session
	- this way the servlet can relate each browser request to the session object even if the connection is dropped
	- the default method is to use a cookie to store the session id in the browser
		- the servlet API also provides a way to rewrite the url to include the session id
			- called url encoding and works with cookies disabled
		- 2 types of cookies exist
			- session cookies and persistence based cookies

`getSession()` method in the request object
 - one is created one if it doesn't exist
 - the session object has a `setAttribute()` object that allows you to set any object asn an attribute in the session
	 - `getAttribute()` to get properties
	 - `getAttributeNames()` method to get a list of all attributes in the session object
		 - returns enumeration object which contains `hasMoreElements()` and `nextElement()` methods
 - threadsafe access
   ```java
	   final Object lock = request.getSession().getId().intern();
	   synchronized(lock){ // sync around the sessionId using the string method
		   // do your threadsafe actions here with the session object
	   }
	```