 - a special type of class that runs on a server and does processing
 - extends the `HTTPServlet` class
 - `doPost` - special method name that gets called when the URL of the servlets receipts an HTTP request using the post method
	 - it accepts a request and response object from the web server
		 - req object has a `getParameter()` method
		 - req object has a `setAttribute()` method where you can store context information
			 - `getAttribute()`
		 - response object has a `sendRedirect()` method when you want to redirect to a url
 - Only one instance of a servlet is created, when the servlet engine starts or is first requested
	 - Each request starts a thread that can access the singleton instance
		 - the `service()` method is called that checks the HTTP method of the request, and calls `doGet()` or `doPost()` appropriately
			 - this is why we only override `doGet` and `doPost`
	 - init method is called once when the servlet is created. You can override it to add init code that's required
	 - if idle for some time, the servlet engine unloads all instances of the servlets it has created
		 - it calls the `destroy()` method of the servlet where you can add cleanup code
		 - this method is not called if the server crashes

`web.xml`
 - deployment descriptor
 - used to configure the deployment of the application server
 - stored in the WEB-INF directory of the application

**JavaBean**
 - zero argument constructor
	 - sets all properties to a default value
 - get and set methods for everything the JSP accesses
 - implement the serializable and externalizable interfaces
	 - Serializable signifies that it has get, set, and is methods that another class can use to write and persist
 - defines the business objects of the app
 - you can use special jsp tags for working with the beans
	 - expression language tags, they begin with a dollar sign followed by an opening brace
	 - is literally string interpolation from javascript

Netbeans
 - a project is a folder that contains all of the files that make up the application
 - make sure to have JDK1.8 installed (adoptium.org or ung free eclipse version is fine)
 - glassfish 5 is best
 - regular java classes to define the business objects of the app
	 - a servlet needs to be mapped to a url or url pattern
		 - `@WebServlet` annotation (do not check the checkbox thing that comes up)
			 - import statement for the WebServlet class
			 - add the `@WebServlet` annotation before the class decl with a url as a parameter
				 - can also use the url patterns attribute
				 - ![[Pasted image 20230731124222.png]]
		 - the url mapping must be stored in the web.xml file for the application

Get real path - `this.getServletContext().getRealPath(path_here);`
 - where the root is the web-inf subdirectory
 - forward request using `getRequestDispatcher().forward()` method

environment variables - initialization parameters
	- context init param - available to all servlets in the web app
		 - context-param element
			 - param-name and param-value element
		 - then you can use the `this.getServletContext().getInitParameter(env_variable_here)`;
	 - servlet init param - available to a specific servlet
		 - init-param element within a servlet element following the servlet-name and servlet-class
			 - param-name and param-value element
		 - you can also use `@InitParam()` annotation to specify servlet initialization parameters
		 - then you can use the `this.getServletConfig().getInitParameter(env_variable_here)`;
	   - ![[Pasted image 20230731131728.png]]
	   - 