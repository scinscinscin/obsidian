## EL - expression language
 - compact syntax that allows you to get data from beans, arrays, and lists that have been stored as an attribute
 - more compact and elegant, easier to read and access nested properties
 - handles null values better than standard jsp tags
 - doesn't create a javabean if the bean hasn't been stored as an attribute, no way to set the properties of a bean
	 - you should use a servlet to create a bean, its properties, and store the bean as an attribute
 - Scopes followed by EL
	 - page - page context object
	 - request - `HTTPServletRequest` object
	 - session - `HTTPSession` object
	 - application - `Servercontext` object
 - Implicit objects that you can use
	 - param - map that returns a value for the specified request parameter name
	 - paramValues - array of values for the specified request parameter name
	 - header - map for the specified HTTP request header
	 - headerValues - array of values for a specified request header
	 - cookie - cookie object for the specified cookie
	 - initParam - context-param eleemnt of the web.xml file
	 - pageContext - implicit `pageContext` element available from any JSP

## JSTL - JSP standard tag library
- more like a Blade template than php
- must make sure that it is added to the library using the taglib directive
 - out tag is used to escape output that's returned to the browser to prevent XSS attacks
	 - `<c:out value="${user.email}" />`
- provides tags for common jsp tags
	- forEach tag
	```jsp
	// you can use forTokens tag to loop through items container in a string as long as they have a delimeter
	 <c:forEach var="variable_name" items="${thing_to_iterate}">
		 // begin - the first index for the loop
		 // end - the last index for the loop
		 // step - the number to increment the index each time through the loop
		 // varStatus - specifies the name of a variable that can be used to get information about the status of the loop
		 <p>${variable_name.somethingElsehere}</p>
	 </c:forEach>
	```
	- Choose tag - is a switch instead of a `<c:if />` tag (see below)
  ```jsp
	<c:choose>
		<c:when test="${cart.count == 0}">
			<p>Your cart is empty</p>
		</c:when>
		<c:otherwise>
			<p>default case here</p>
		</c:otherwise>
	</c:choose>
	```

- storing an attribute in the request object - only available in the current request - request scope
- ![[Pasted image 20230731143613.png]]
- attribute to be available in all servlets - ServletContext object - application scope
- this is not thread safe
- available to all servets in a user sesssion - store the attribute in the session object
- session scope

```jsp
<% 
	// you can add java statements here
	// you have to use get attributes from the request object since you are not using expression language here 
	if(condition here){
%>
	<p>This is what should be rendered</p>
<%
	}
%>

// include a file at compile time with an include directive
<%@ include file="/includes/footer.html" %>

// jstl code below which requires jstl to be imported
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<c:if test="${condition_here}">
	<p>Conditional code here</p>
</c:if>
<c:import url="/includes/component.html" />
```

![[Pasted image 20230731150718.png]]

