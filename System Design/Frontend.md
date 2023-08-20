  - **Traditional**
	  - clicking a link or a button initiates a new request and results in the browser reloading an entire page with the response received from the server.
  - **Single page application**
	  - most business logic is in the browser
  - **Hybrid applications**
	 - most the way that most modern web applications are built
	 - applications are a hybrid of traditional and multipage web applications and SPAs

## State management
 - statelessness is a property of a service, server, or object indicating that it does not hold nay date. Statelessness makes instances of the same type interchangeable, allowing better scalability.
	 - they delegate to external services any time that clients state needs to be accessed
 - Managing http sessions
	 - sessions can be implemented using cookies
	 - a webapp stores your user identifier and additional data in a web session scope somewhere.
	 - any data you put in the session should be stored outside of the web server itself to be available from any web server.
		 - store session state in cookies
			 - is expensive since the cookies are sent in every single request. Cookies are sent by the browser with every single request regardless of the type of resource being requested.
			 - they have to send the cookies even just for requesting static content that is unencrypted
			 - works well if you can keep the data minimal
		 - delegate the session storage to an external data store
			 - the cookie stored in the user is an identifier that can be mapped into an external data store
			 - serialize the session data and save it back in the data store
			 - does not hold session data between requests
			 - is fast with the only requirement having fast get by key and put by key operations
				 - best paired with automatic scalability
		 - use a load balancer that supports sticky sessions
			 - the load balancer needs to be able to inspect the headers of the request to make sure that requests with the same session cookie always to go the server that initially issued the cookie
			 - are a bad idea because web servers become unique
				 -  you lose the ability to restart and auto-scale web servers without breaking user's sessions.

## File storage
 - use S3
	 - public content can be cached by a CDN
	 - private content can be hosted on a private bucket where the frontend handles permission and serving of content from S3

## Cache inconsistencies
 - You should cache objects using a shared object cache so there is only one copy of each object and it could be invalidated more easily **if cache inconsistencies is dangerous to the type of the application**
 - Share resource locks globally by removing locks code from the frontend and create an independent service from it. Then use the shared lock service on all of your web application servers to share locks globally.
	 - might result in increased latency
	 - isolate a piece of functionality that requires a global state, remove it from the application, and create a new independent service encapsulating this functionality. Since this functionality is more narrow, it is easier to scale out and hides the shared state behind a layer of abstraction from the rest of the system.