---
tags:
  - reviewer
course: ICS2608 - Front-end Web Development
period: Finals
assessment: Final Exam
---

![](https://www.youtube.com/watch?v=SnI4CGjeVOM)
# Chapter 1

**Web client**
 - requests a resource (HTML, PDF)
 - knows how to communicate and interpret the request and response types of the server

**Webserver**
- gets the resource requested by the client and returns it in the server
- can be a physical machine or server application
- can only return static content, finds the file requested as is and hands it back to the client
	- Cannot do computations
	- Need a helper application to generate pages just in time / dynamically and save data on the server
		- the page is based on data submitted by the user
		- the page uses information from databases or other server-side sources

**Hyper Text Markup Language (HTML)**
 - is returned by servers
 - tell browsers how to present content to user

**Hyper Text Transfer Protocol (HTTP)**
 - protocol used by web server and a browser
 - HTTP request it sent by the browser and the server sends the HTTP response back
 - **Request** - requests and sends form data to the server
	 - HTTP method (the action to be performed)
		 - GET method
			 - has limited length (dependent on the OS)
			 - form data is appended to the URL
				 - can be bookmarked (good for search)
				 - may not be secure since the form data can be seen in the URL
			 - `method="GET"` in HTML form element attributes
			 - An anchor tag always sends a GET request
		 - POST method
			 - has unlimited length
			 - form data is in the request body
				 - user can't bookmark the resulting URL
				 - considered more secure
			 - `method="POST"` in the html form element attribute
		 - There are other methods
			 - PUT and DELETE - used in RESTful applications
			 - HEAD, TRACE, OPTIONS, CONNECT - used in CORS
	 - Page to access (URL)
		 - **Universal Resource Locator (URL)**
			 - Has the protocol, domain, port and path
			 - Protocol - which protocol to use
			 - Server / domain - physical name of the server you're looking for
			 - Port - identifies ethe server application. 80 is the default since 80 is the port used by http
			 - Resource - The name of the content being requested
	 - Form parameters
 - **Response**
	 - Status code
	 - Content-type
	 - The content

**JavaServer Pages (JSP)**
- just like an html page but you can put java code inside of it 
```jsp
<%= new java.util.Date() %>
```

# Chapter 2
**WebContainer**
 - servlets don't have a main method since they are under the control of the WebContainer, also called the Application server (glassfish, tomcat)
 - **what do they do?**
	 - Communication support
		 - WebContainers know HTTP and how to communicate with the webserver
	 - Lifecycle management - life and death of servlets
	 - Multithreading - creating threads for every request
	 - Declarative security - no need to recompile your code since configuration is done with an XML file
	 - JSP support
 - **How Requests are handled**
	 - it creates an `HttpServletRequest` and `HttpServletResponse` objects, and finds the correct servlet based on the URL in the request
	 - the `service()` method of the servlet is called, which picks which method handler to call depending on the method of the request
		 - `doGet()` or `doPost()` is run, which stuffs the page into the response object, so the response goes back to the container
	 - The container converts the response object into an HTTP response and sends it back to the client
		 - request and response objects are GC'd

 - **Classes and interfaces**
	 - `Servlet` interface - contains mostly lifecycle methods
		 - `init()` - executed once when the servlet is first loaded and before the servlet can service any client requests
			 - a unique ServletConfig is created for the servlet
			 - gives you a chance to init your servlet before handling any client requests
			 - container reads the servlet init parameters from the Deployment Descriptor and gives them to servlet config, which is passed into the init method
		 - `service()` - looks at the request and figures out what it should run
			 - when a request is sent, the container starts a thread and invokes service().
			 - service() looks at the request and invokes the matching `do<Method>()` post in the servlet
		 - `destroy()` - called when the server deletes the servlet instance, not called after every request
			 - cleaning resources
		 - `getServletConfig()`
		 - `getServletInfo()`
	 - `GenericServlet` - an abstract class that implements a lot of the work that is common between different types of servlets
		 - most of the secret behavior comes from this class
	 - `HttpServlet` - extends GenericServlet and adds HTTP specific methods
		 - implements the service method to reflect HTTP specific behavior
	 - `MyServlet` - the place where you override the HTTP methods that you used
		 - `doGet()` and `doPost()` - where you should actually put your application code, usually have a common method that is called by both these methods

- **Web.xml** examples
	- Web.xml is also called **Deployment Descriptor** or DD
	- **ServletConfig**
		- Allows us to not hardcode values by placing them in a configuration file that can be read by servlets
		- If these data changes, no need to modify and recompile the servlet
		- The config of a servlet is specific to that servlet
			- Creating a new init param
				- Using the parameter: `getServletConfig().getInitParameter("email")`
		```xml
			// this is located inside a servlet tag, it's only available for that servlet
			<init-param>
				<param-name>Insert the key here</param-name>
				<param-value>Insert the value here</param-value>
			</init-param>
		```
	 - **ServletContext** - exposes a parameter to all servlets in the same web application
		 - Creating a new context param
			 - parameters that are available to the entire application
			 - ``getServletContext().getInitParameter("the_key")``
	 ```xml
		<context-param>
			<param-name>Insert the key here</param-name>
			<param-value>Insert the value here</param-value>
		</context-param>
	```
	 - **Servlet mappings**
		 - Allows you to change the organization of your packages and servlets without having to change URLs in HTML and JSP
		 - Also prevents clients from knowing the directory structure of the server
		 - can also use `@WebServlet(name="ClassName", urlPatterns={"/path1", "/path2"})` annotation
		 ```xml
		 // whenever `/this_is_path` is called, it runs the code in the thing1 class
		 <servlet>
			 <servlet-name>Internal name</servlet-name>
			 <servlet-class>thing1</servlet-class>
			 // optional, if 1 then initialize this servlet on server startup than first request
			 <load-on-startup>1</load-on-startup>
		 </servlet>
		 <servlet-mapping>
			 <servlet-name>Internal name</servlet-name>
			 <url-pattern>/this_is_path</url-pattern>
		 </servlet-mapping>
		```
		
 - **ServletContextListener**
	- Allows you to pass objects that can be accessed by servlets
	- `javax.servlet.ServletContextListener`
		- is created when the web application is created, before any of the servlets
	- Creating a `ServletContextListener`
	```java
	@WebListener // make java autodiscover the class
	public class ContextListener implements ServletContextListener{
		// called when the application is created
		public void contextInitialized(ServletContextEvent sce){
			// get the servlet context
			ServletContext context = sce.getServletContext();
			context.setAttribute("key", value);
		}
		
		// called when the application is stop. Needs to be overridden.
		public void contextDestroyed(ServletContextEvent e){
		}
	}
	```
	- Getting and setting data
		- ``getServletContext().getAttribute("key")`` in the implementation
		- ``sce.getServletContext().setAttribute("key", value)`` in the `contextInitialized()` method
	- you can add the `@WebListener` class annotation so Java autodiscovers the ServletContextListener that are creating, alternatively you can define it inside the web.xml file like request mapping
	```xml
		// web.xml example
		<listener>
			<listener-class>path.to.class.Listener</listener>
		</listener>
	```

# Chapter 3
 - Linking forms to servlets
	 - the HTML form element has a `action` attribute which should point to the link of the servlet url pattern (remember to prefix it with the name of the deployment)
	```html
	<form action="<%= request.getContextPath() %>/name_of_servlet" method="POST">
		{your input fields here}
	</form>
	```
	 - it also has a method attribute which is `GET` or `POST`
		 - dictates the type of request method to use and where to store the form parameters
			 - GET - query string in the path
			 - POST - hidden request body
 - **Acquiring form data in servlets through the request parameter**
	 - `request.getParameter(parameter_name)`
		 - parameter name should match the `name` attribute of the input element you want to get
		 - returns the first occurrence of `parameter_name` in the query string
			 - will return an empty string if the parameter exists but has no value
		 - returns null if it doesn't exist
			 - For text inputs: you need to check that it isn't null before validating it
			 - For checkbox inputs: it returns null if and only if it wasn't checked
	 - `request.getParameterValues(parameter_name)`
		 - returns an array of URL decoded values of all occurrences of `parameter_name` in the query string or the request body
		 - returns null if `parameter_name` does not appear in query string or the request body
	 - `request.getParameterNames()` and `request.getParameterMap()`
		 - returns an `Enumeration<String>` of the parameter names and map of the request parameters respectively (`Map<String, String[]>`)
		```java
		// how to loop through all request parameter names
		for (Enumeration<String> e = request.getParameterNames(); e.hasMoreElements();)
			System.out.println(e.nextElement());

		// how to loop through all request parameters
		for(Map.Entry<String, String[]> entry : request.getParameterValues().entrySet())
			System.out.println(entry.getKey());
		```
 - Other methods of `HttpServletRequest`
	 - `request.getCookies()` - returns an array of cookie objects of the request
	 - `request.getSession()` - returns the `HttpSession` object associated with the user
		 - An `HttpSession` object has `setAttribute()` and `getAttribute()` methods
	 - `request.getMethod()` - returns a string that is the HTTP method of the request
	 - `request.getHeader(header_name)` - returns the value of a header based on the name
		 - `User-agent` - identifies the client category / device type and browser used
		 - `Accept` - the mime types that the browser can handle
		 - `Referer` - URL of the referring webpage for tracking traffic
		 - `Cookie` - The saved cookies on the client
	 - `request.getHeaderNames()` - returns an enumeration of the names of the headers of the request
 - **`RequestDispatcher`**
	 - used to forward the HTTP request to another URL
	 - URL must be within the application
	 - `request.getRequestDispatcher("/path/to/new.jsp")`
		 - returns a `RequestDispatcher` object which has a `forward()` method that takes in the reqeust and response
		 - absolute paths are redirected to `domain.com/domain_deployment_name/path`
		 - `request.getAttribute("javax.servlet.forward.query_string")`
			 - get the name of the servlet that forwarded to the current servlet
	 - is used when request attributes must be rendered in the JSP file since `response.sendRedirect("/path")` sends a raw HTTP redirect instead of redirecting internally

# Chapter 4

`response.setContentType()`
 - set the content type header
 - tells the browser what type of content you are sending back
	 - same as the mime type
 - You can only set the content type once for every response
	 - Always set this first before you call the method that gives you the output stream

`response.getWriter()` - returns a PrintWriter which is the same interface as System.out
`response.getOutputStream()` - returns a `ServletOutputStream`
```java
public void doGet(HttpServletRequest request, HttpServletResponse response){
	// set the content type so the browser knows what we're sending
	response.setContentType("application/jar");
	// get the file as an input stream relative to the deployment folder
	InputStream is = getServletContext().getResourceAsStream("/file.jar");
	
	// the number of bytes read from the input stream, is -1 if there are no bytes left
	int bytesRead = 0;
	byte[] one_kb = new byte[1024]; // 1KB of space
	OutputStream os = response.getOutputStream();

	// is.read(bytes) loads 1KB of the file into one_kb, and returns the number of bytes read. If the returned value is -1, there are no more bytes to send
	while((bytesRead = is.read(one_kb)) != -1)
		// send one_kb of the file to the output stream, pass bytesRead so output stream knows when not all of one_kb is populated
		os.write(one_kb, 0, bytesRead);

	os.flush(); os.close();
}
```

**Setting response headers**
 - `response.setHeader("name", "header_value");` - sets an arbitrary header
	 - `Content-Type`
		 - The MIME type of the document being returned
		 - `response.setContentType("text/html")` is equivalent to `response.setHeader("content-type", "text/html")`
	 - `Refresh`
		 - The number of seconds until browser should reload page
		 - `requeset.setHeader("Refresh", "5; url=https://example.com/")`
			 - Go to `https://example.com` after 5 seconds
	 - `Cache-Control` - prevents the page from being cached 
	 - `Location` - use `response.sendRedirect()` instead
	 - `Set-Cookie` - use `response.addCookie()` instead
 - `response.addHeader("name", "header_value")`; - adds a new occurrence of the header
 - `response.setDateHeader("name", milli_since_epoch)`;
 - `response.addDateHeader("name", milli_since_epoch)`;
 - `response.setIntHeader("name", intValue)`;
 - `response.addIntHeader("name", intValue)`;

**Sending status codes**
 - `response.setStatus(number)`
	 - Status code constants are in `HttpServletResponse` and are preferred over using magic numbers
	 - 200 - everything is fine - `HttpServletResponse.SC_OK`
	 - 301 -requested document is temporarily moved elsewhere - `HttpServletResponse.SC_MOVED_TEMPORARILY`
		 - **Redirect** - makes the client do the work
			 - The new URL is seen in the browser
		 - **Forward** - makes the server do the work
			 - The client doesn't know some different resource is being sent
			 - Forwards the request and response objects
	 - 404 - content is not found - `HttpServletResponse.SC_NOT_FOUND`
 - `response.sendError(code, message)` - wraps message inside a small HTML document

# Chapter 5
 - **WebApplications**
	 - everything is bundled together in a single directory or file
	 - access to content in the webapp is through a URL that has a common prefix
	 - Many aspects of the WebApplication can be controlled through deployment descriptor
	 - all compliant servers support web apps, the code can be redeployed on a new server by moving a single file or directory
	 - **Registering a webapp**
		 - Copy the `build/web` folder of deployment directory into Tomcat's webapps folder
		 - Rename the web folder into the desired context path
	 - **WAR Files**
		 - A jar file with a different file extension
		 - All servers are required to support Webapps in WAR files
		 - Create: `jar cvf webAppName.war *`
		 - In tomcat: drop the war file in `webapps`, the file name becomes the app name
 - **Welcome file list**
	 - accessible to all directories under your webapp, glassfish looks at the same list
	 - uses the first thing that matches
```xml
<welcome-file-list>
	<welcome-file>index.html</welcome-file>
</welcome-file-list>
```
 - **Configuring error pages**
 ```xml
 <error-page>
	 // a catch-all error page
	 <exception-type>java.lang.Throwable</exception-type>
	 <location>/errorPage.jsp</location>
 </error-page>
 <error-page>
	 <error-code>404</error-code>
	 <location>/notFoundError.jsp</location>
 </error-page>
```
 - Loading a servlet on startup
```xml
<servlet>
	<servlet-name>My Servlet</servlet-name>
	<servlet-class>myServlet</servlet-class>
	<load-on-startup>1</load-on-startup>
</servlet>
```
 - `request.getContextPath()` or `${pageContext.request.contextPath}`
	 - Allows you to use absolute paths without hard-coding the application prefix
	```jsp
	<img src="<%= request.getContextPath() %>/images/home.gif" />
	```
# Chapter 6

**HTTP is a stateless protocol**
 - it provides no way for a server to recognize that a sequence of requests are all from the same client
 - after every request, the connection between client and server is dropped and forgotten
 - no memory between client connections

**How to maintain state within HTTP**
 - **URL Rewriting**
	 - Explicitly append the data you want to pass to the URL
	 - Not advisable for lengthy and sensitive data since its seen in the URL
	 - Need to encode the data into a URL-safe format using `URLEncoder.encode(testing, "UTF-8")`
 - **Hidden fields**
	 - Fields dynamically added to an HTML form that are not displayed in the client's browser
	 - Used when you go the the next page through a form submission
 - **Cookies**
	 - Flow
		 - Servlet sends a name and value to client
		 - Client saves the name and value to the file system
		 - The cookie is sent every time it connects to the same site
	 - How to add a cookie
	```java
	// by default, a cookie disappears when the browser exits
	Cookie cookie = new Cookie("key", value);
	response.addCookie(cookie);
	```
	 - How to get cookies
		 - ``request.getCookies()``
	```java
	Cookie[] cookies = request.getCookies();
	for(Cookie cookie : cookies){
		cookie.getName(); // returns a string of the cookie's name
		cookie.getValue(); // returns a string of the cookie's value
	}
	
	Cookie newCookie = new Cookie("cookie_name", "cookie_value");
	// newCookie.setDomain(string)
	// newCookie.setMaxAge(number_of_seconds)
	// newCookie.setPath(string)
	// newCookie.setSecure(bool)
	// newCookie.setHttpOnly(bool)
	// newCookie.setValue()
	response.addCookie(newCookie);
	```
	 - How to remove a cookie
		 - Get the cookie, set its age to 0 with the `setMaxAge(0)` method
		 - Add the cookie to the response
 - **Sessions**
	 - Randomly generated session ID is used to identify a user session
	 - SID is stored on the client as a cookie, Session data is stored on the server
	 - `HttpSession s = request.getSession()`;
		 - automatically creates the session and sends the session cookie in the response
	 - `HttpSession s = request.getSession(false);`
		 - don't automatically create a session
		 - returns null if there is no preexisting session
	 - **Setting and getting values in sessions**
	```java
	session.setAttribute("uname", uname);
	String str = (String) session.getAattribute("uname");
	session.removeAttribute("uname")
	```
	 - `HttpSession` methods
		 - `session.invalidate()` - when you are done
		 - `session.getAttributeNames()` - returns names of all attributes in the session
		 - `session.getId()` - returns the sid
		 - `session.isNew()` - Determine if session is new to client.
		 - `session.getCreationTime()` - return time when session was first created
		 - `session.getLastAccessTime()` - return the last time the container got a request with this sid
		 - `session.setMaxInactiveInterval(seconds)`
			 - maximum time in seconds that client should send requests for this session
			 - a session timeout of -1 means the session will never expire
			 - **alternatively this can be set in the DD**
			```xml
			<session-config>
				<session-timeout>value_in_minutes</session-timeout>
			</session-config>
			```
		 - `session.getMaxInactiveInterval()`

# Chapter 7

**JSP scripting elements**
 - The JSP is just a servlet
	 - the container translates it into a java source file
	 - the container compiles it into a java class
		 - this class is reused and is recompiled whenever the JSP is modified
 - **List of objects that you can use**
	 - `request` - `HttpServletRequest`
	 - `response` - `HttpServletResponse`
	 - `out` - a buffered version of `JspWriter`
		 - used to send output to the client
	 - `session` - `HttpSession` associated with the request
		 - unless disabled with session attribute of the page directive
	 - `application`
		 - The servlet context for sharing data
		 - obtained through `getServletContext()`
	 - `config`
		 - Obtained through `getServletConfig()`
	 - `exception` - only available through designated error pages

 - Expressions: `<%= expression %>`
	 - the expression is evaluated, converted into a String then placed in the html page
	 - since its an expression, never end it with a semi colon
	 - `<%= new java.util.Date() %>`

 - Scriptlets: `<% script here %>`
	 - Code that is inserted into the servlet's `_jspService()` method
		 - meaning that any variables declared are reset on each page run
	 - Not printed in the response, and can be used to add conditions to the page

 - Declarations: `<%! code %>`
	 - Code that is inserted into the servlet's class definition, outside of any existing methods
	 - Can be used to declare variables and also methods.

 - Directive: `<%@ page attribute="value" %>`
	 - High level information about the servlet that will result from the JSP page
	 - Can be used to import classes
		 - `<%@ page import="foo.*" %>`
		 - Is placed at the top of the generated servlet file
	 - Specify the Mime type of the page generated
		 - `<%@ page contentType="MIME-Type" %>`
	 - Defines tag libraries available to the JSP
		 - `<%@ taglib tagdir="path" prefix="cool" %>`
	 - Defines text and code that gets added to the page at translation time
		 - `<&@ include file="header.html" %>`

 - Comments
	 - HTML comments: `<!-- HTML Comment -->`
	 - JSP comments: `<%-- JSP comment --%>`

![[Servlet API class diagram.png]]
![[HttpServlet API UML diagram.png]]

# Servlet API

 - **Servlet** - an interface that contains initialization / lifecycle methods
	 - Methods
		- `init()` - executed once when the servlet is first loaded and before the servlet can service any client requests
			- a unique ServletConfig is created for the servlet
			 - gives you a chance to init your servlet before handling any client requests
			 - container reads the servlet init parameters from the Deployment Descriptor and gives them to servlet config, which is passed into the init method
		 - `service()` - looks at the request and figures out what it should run
			 - when a request is sent, the container starts a thread and invokes service().
			 - service() looks at the request and invokes the matching `do<Method>()` post in the servlet
		 - `destroy()` - called when the server deletes the servlet instance, not called after every request
			 - cleaning resources
		 - `getServletInfo()`
		 - `getServletConfig()` - returns the config of the servlet from the `web.xml` file
	 - **Subclass** - `GenericServlet`
		 - An abstract class that implements the methods of the Servlet interface
			 - It leaves the `service()` method unimplemented
		 - Most of the secret behaviour lies in this class
			 - **Subclass** - `HttpServlet`
				 - an abstract class that implements the `service()` method, calling `do<MethodName>()` methods
				 - This class is extended by your servlet
 - `ServletRequest` interface
	 - Methods
		 - `getParameter(String name)` - returns a string from request parameters
		 - `getParameterValues(String name)` - returns a `String[]` for parameters with multiple values
		 - `getAttribute(String key)` - returns an Object from attribute map
		 - `setAttribute(String key, Object value)` - sets an Object in the attribute map
		 - `removeAttribute(String key)`
		 - `getInputStream()`
		 - `getRequestDispatcher(String relativePath)` - returns a RequestDispatcher object to the path 
	 - **Extended by** `HttpServletRequest` interface
		 - Adds methods specific to HTTP, such as Cookies / Methods / Headers
			 - `String getContextPath()` - returns the portion of the URI that indicates the context path of the application
			 - `Cookie[] getCookie()` - returns an array of the request's cookies
			 - `String getHeader(name), int getIntHeader(name), Enumeration<String> getHeaderNames()`
			 - `String getMethod()`
			 - `HttpSession getSession(), HttpSession getSession(boolean)`
				 - returns an HttpSession object
 - `ServletResponse` interface
	 - Methods
		 - `PrintWriter getWriter()`
		 - `ServletOutputStream getOutputStream()`
		 - `setContentType(String)`
		 - `setContentLength(int)`
		 - `setCharacterEncoding(String)`
	 - **Extended by** `HttpServletResponse` interface
		 - Adds methods for modifying cookies, headers, 
			 - `addCookie(Cookie)`
			 - Raw methods to add headers
				 - `addDateHeader(String key, long value)`
				 - `setDateHeader(String key, long value)`
				 - `addHeader(String key, String value)`
				 - `setHeader(String key, String value)`
				 - `addIntHeader(String key, int value)`
				 - `setIntHeader(String key, int value)`
				 - `boolean containsHeader(String)`
				 - `String getHeader(String)`
				 - `Collection<String> getHeaders(String key)`
					 - returns an array of strings of the values for a key
				 - `Collection<String> getHeaderNames()`
					 - returns an array of strings of the key of the request headers
			 - `int getStatus(), void setStatus(int)`
			 - `void sendRedirect(String)`
				 - send an absolute redirect relative to the domain of the client
 - `ServletConfig` interface
	 - Methods
		 - `String getInitParameter(String)`
		 - `Enumeration<String> getInitParameterNames()`
		 - `String getServletName()`
		 - `ServletContext getServletContext()` - returns the ServletContext, which is accessible by all servlets and JSPs
 - `ServletContext` interface
	 - Can also share objects between the entire application using `setAttribute()` methods.
	 - `String getContextPath()` - get the context path of the application
	 - `String getRealPath()`
	 - Info sharing methods
		 - `Object getAttribute(String key)`
		 - `void setAttribute(String key, Object Value)`
		 - `void removeAttribute(String)`
		 - `String getInitParameter(String)`
		 - `Enumeration<String> getInitParameterNames()`
		 - `boolean setInitParameter()`
	 - `RequestDispatcher getRequestDispatcher()` - get a RequestDispatcher instance
 - `RequestDispatcher` interface
	 - Allows you to forward a request to other servlets, making it seamless to the client
	 - Methods
		 - `void forward(HttpServletRequest request, HttpServletResponse response)`
			 - Forward a request from a servlet to another resource
		 - `void include(HttpServletRequest request, HttpServletResponse response)`
			 - Include the content of a resource in the response
 - **Cookie** class
	 - `getName() / setName()`
	 - `getValue() / setValue()`
	 - `isHttpOnly() / setHttpOnly()`
	 - `getDomain() / setDomain()`
	 - `getMaxAge() / setMaxAge()`
		 - Set a cookie's maxAge to 0, and add it to the response to delete the cookie from the frontend
	 - `getPath() / setPath()`
	 - `getSecure() / setSecure()`
 - Listeners
	 - `HttpSessionActivationListener` - notifies objects bound to sessions that sessions will be passivated and activated
		 - A container that migrates sessions between VMs is required to notify all attributes that implement this interface
		 - `void sessionDidActivate(HttpSessionEvent se)`
		 - `void sessionWillPassivate(HttpSessionEvent se)`
	 - `HttpSessionAttributeListener` - receives notifications about HttpSession attribute changes
		 - is registered
		 - `void attributeAdded(HttpSessionBindingEvent e)`
		 - `void attributeRemoved(HttpSessionBindingEvent e)`
		 - `void attributeReplaced(HttpSessionBindingEvent e)`
	 - `HttpSessionBindingListener` - an object is notified when it is bound / unbound from a session (can be caused by a programmer unbinding the object, session being invalidated or a session timing out)
		 - `void valueBound(HttpSessionBindingEvent event)`
		 - `void valueUnbound(HttpSessionBindingEvent event)`
			 - can tell you if the session is about to timeout
	 - `HttpSessionIdListener` - notifications about HttpSession id changes
		 - is registered
		 - `void sessionIdChanged(HttpSessionEvent event, String old_id)`
	 - `HttpSessionListener` - notifications about HttpSession lifecycle events
		 - is registered
		 - `void sessionCreated(HttpSessionEvent se)`
		 - `void sessionDestroyed(HttpSessionEvent se)`
			 - a session is about to be invalidated / timeout
	 - `ServletContextAttributeListener` - notification events about ServletContext attribute changes
		 - is registered
		 - `void attributeAdded(ServletContextAttributeEvent e)`
		 - `void attributeRemoved(ServletContextAttributeEvent e)`
		 - `void attributeReplaced(ServletContextAttributeEvent e)`
	 - `ServletContextListener` - receiving notification about ServletContext lifecycle events
		 - `void contextDestroyed(ServletContextEvent sce)`
		 - `void contextInitialized(ServletContextEvent sce)`
	 - `ServletRequestAttributeListener` - notification events about ServletRequest attribute changes
		 - is registered
		 - `void attributeAdded(ServletRequestAttributeEvent e)`
		 - `void attributeRemoved(ServletRequestAttributeEvent e)`
		 - `void attributeReplaced(ServletRequestAttributeEvent e)`
	 - `ServletRequestListener` - receiving notification about ServletRequest lifecycle events
		 - `void requestDestroyed(ServletRequestEvent sre)`
		 - `void requestInitialized(ServletRequestEvent sre)`