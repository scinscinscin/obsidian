 - pretty much custom components
	 - reduce the amount of java scripting needed in the JSP pages
	 - organize the code of an app, reducing duplication making it easier to maintain
 - code a taglib directive in the jsp
	 - the URI attribute must specify the location of a tag library descriptor
	 - prefix attribute must specify a prefix that you can use for the custom tags defined by the TLD
	 - `<%@ taglib prefix="scin" uri="/WEB-INF/murach.tld"`
 - create a tag library descriptor that describes the tag
	 - it is typical to code a single TLD (XML docuemnt) that contains all the custom tags of an app
	 - ![[Pasted image 20230731234155.png]]
		 - after header, taglib element defines the tag library
			 - version, short name and the URI, info element for a description
		 - one tag element for each custom tag in the tag library
			 - code a name element that defines a name of the tag
			 - tagclass element that defines the class that carries out the actions
				 - also called as tag handler class
			 - info element that provides a description of the custom tag
			 - if the tag element has attributes, then you must define it as such: 
			 - ![[Pasted image 20230801000137.png]]

### The tag class
 - must implement the Tag interface or extend the `TagSupport` class
	 - the TagSupport class has an instance variable called `pageContext` that has a `setAttribute()` method that allows you to set properties that can be accessed in the JSP 
	 - override the `doStartTag()` method of the `TagSupport` class
		 - called when the custom tag is read
		 - must return the `SKIP_BODY` constant when the tag doesn't have a body
		```java
			JspWriter out = pageContext().getOut();
			out.print("the thing that you want to send to the jsp page")
		```
	- when the tag has a body
		- you must code a bodycontent element that has a value of JSP
			- in the XML of the tag, `<bodycontent>JSP</bodycontent>`
		- return `EVAL_BODY_INCLUDE` field so the body of the tag is evaluated and displayed
			- this enum has no chance to work with the client and is being written to the client
	- when the tag has props
		- `<id:name key="value" />`
		- the tld must define the attributes of the custom tag
		- the keys should be instance variables of the tag class and they should have setters
		- ![[Pasted image 20230801000951.png]]

### custom tag that reiterates it's body
 - extends the `BodyTagSupport` class instead of `TagSupport`
 - the tag class overrides the `doStartTag()` returns `EVAL_BODY_BUFFERED` instead
	 - `SKIP_BODY` - the body of the tag is not displayed and the rest of the class is skipped
	 - `EVAL_BODY_BUFFERED` - the tag evaluates the body by calling `doInitBody()` and `doAfterBody()` methods
 - the tag class overrides the `doInitBody()` method
	 - this method is where you can initiate custom instance variables in the tag class
	 - you can set the attributes using `pageContext.setAttribute()` method will be accessible in the JSP
	 - the body is stored in the `bodyContent` object that's provided by the `BodyTagSupport` class 
		 - not yet displayed, you must write the body to the JSP yourself
 - override the `doAfterBody()` method which can be used to re-evaluate the body of the tag again by returning the `EVAL_BODY_AGAIN` enum 
		 - this enum adds the body to the existing `bodyContent` object, and it calls the `doAfterBody()` method to evaluate the body again
		 - if it's over then you can return normally using
	```java
	JSPWriter out = bodyContent.getEnclosingWriter();
	bodyContent.writeOut(out);
	return SKIP_BODY;
	```

## Methods of the TagSupport class
 - you need to override the `doStartTag()` method for many tags
	 - no body - return `SKIP_BODY` so the body is not evaluated
	 - has a body - return `EVAL_BODY_INCLUDE` so the body is evaluated
 - `doEndTag()` is called after the `doStartTag()` finishes executing.
	 - this method returns an `EVAL_PAGE` by default, which causes the rest of the JSP to be evaluated
	 - you can instead return `SKIP_PAGE` so any JSP after the custom tag is not displayed
 - `release()` is called after `doEndTag()` finishes executing
	 - clean system resources in use
	 - you can use this method to close streams that you have used in the tag class

## Methods and fields of the PageContext class
 - available as `pageContext` for all tag classes, it allows jsps and tag classes to communicate by getting and setting objects and attributes
	 - `getRequest()` and `getResponse()` methods for getting the request and response objects
	 - has set and get methods of the pageContext class to set and get attributes
		 - you can specify the scope when you attempt to get the attribute
			 - scopes are available as enums
		 - if you don't specify the scope, only the page scope is considered
	 - `findAttribute()` method to search for the attribute smallest to largest

## Methods and fields of the BodyTagSupport class
 - `doStartTag()` methods returns `EVAL_BODY_BUFFERED` field which indicates that the tag has a body
	 - causes the `doInitBody()` and `doAfterBody()` methods to be called
	 - override this method if you want to add code that writes data to the jsp before the body is evaluated or skip the body under conditions using `SKIP_BODY`
 - `doInitBody()` is called to evaluate the body for the first time
	 - to evaluate - the body is read and placed in the bodyContent object which stores ethe body
 - `doAfterBody()` method is called that you can override to add statements that need to be executed each time the body is evaluated.
	 - if you want to evaluate the body again, return the `EVAL_BODY_AGAIN` field
	 - once you are done, return `SKIP_BODY`
 - `doEndTag()` and `release()` methods are called after `doAfterBody()`

