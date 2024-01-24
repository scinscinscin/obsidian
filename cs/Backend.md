# Request and Response Lifecycle
 **Whenever our server receives a request, we have to figure out what code to run to generate a response**

 - routing - figuring out what code runs when a specific request is received
	 - is controlled using the path and path parameters
	 - every API endpoint is composed of middleware and a resolver
		 - the resolver is the code that does all the logic and generates a response

 **Where can information be stored in a request**
 1. query parameters
	 - are at the end of the path, after a question mark
	 - typically used with filtering queries and / or pagination
 2. path parameters
	 - are embedded in the path and is used to control routing
	 - typically refer to resources using identifiers
		 - `GET /users/{id}`
 3. request headers
	 1. contain cookies and controls how the response is to be received
 4. request body
	 - `application/json` - is most typically used with AJAX requests
		 - De facto standard when using JavaScript libraries
	 - `multipart/form-data` - is most used with file uploads
	 - `x-www-form-urlencoded` - is the default when using a form with `method=POST`
	```html
	// sends a request to /testing with x-www-form-urlencoded
	<form action-"/testing" method="POST">
	</form>
	```

## Middleware
 - **middleware** intercept the request and perform different operations on it
	 - could check if the user is logged in before proceeding (authentication)
	 - could check if the user has access with what they want to do (authorization)
	 - could add different functions to the request (error logging)
	 - could validate the contents of the body before calling the resolver
	 - could protect against CSRF by checking double send
 - middleware can be applied per route / globally / on a group of routes

## Cookies
 - a cookie is a header that is attached to an http request whenever a request is made
 - whenever we send a request to youtube.com, we send our cookies
 - a server can set cookies in the client's computer by sending a `Set-Cookie` header in the response
	 - a server can delete cookies in the client's computer by sending a `Set-Cookie` header with a date in the past
 - have different properties but the important ones are `HttpOnly` and `MaxAge`
	 - `MaxAge` specifies how a long a cookie will be stored on the computer
		 - `time` - delete the cookie after a set period of time
		 - `session` - delete the cookie when the browser is closed
		 - `permanent` - do not delete the cookie ever
	 - `HttpOnly`
		 - when set to true, the cookie cannot be retrieved or modified using JS
	 - `Secure` - just set this to true if you're in production
 - whenever we're dealing with auth, we can either use session based or token based

## Sessions
- when a user logins, we create a session id that we store in the database, and this session id is stored in the client's cookies
	- the session id maps to the user object, and this is how we know who the user is in every request
- when the user logs out, we remove the session id cookie
- we have to maintain the state in the database

## JWTs
 - when a user logs in, we create an encrypted token that encodes their unique identifier, and this token is stored in the client's cookies
	 - for every request, we decode the encrypted token using our private key, and this is how we know who the user is in every request
	 - only the server can verify the user's information due to encryption
 - when the user logs out, we remove the jwt cookie
 - we DO NOT have to maintain state in the database

## CSRF protection
 - since cookies are sent for every request to a website, `b.com` can send a request to `a.com` and `a.com` would see the cookies of the user
	 - `b.com` can pretend to be a user using `a.com` and create fake inputs, form submissions
	 - is called Cross Site Request Forgery
 - we can mitigate CSRF using "Double sending"
	 - the request must have a token in the cookies and also in the headers
	 - `b.com` CANNOT set `a.com`'s cookies, therefore it cannot pretend to be a user using `a.com`
	 - `a.com`'s code has to set a special csrf token in the cookies and headers with every request
	 - ``{{ csrf_token() }}`` in laravel

## Validating the request body
 - we validate the request body whenever we have requests that want to change data
 - we do this for security and to ensure that what we're getting from the client is what we're expecting
	 - check if the request body has `username` and `password` fields of type string
	 - can check primitive types and structure for big types
 - once we validate the body, we can fearlessly use the contents of the body

# Responses - Oops, I did it again!
**Figuring out what we send in response to a request**
## HTML pages
 - is the `V` in `MVC` - Model view controller 
 - html pages can either be static or dynamic
	 - static pages must still be compiled even if they do not have changing data
	 - dynamic pages populate a template with content fetched from a database
 - **server side rendering**
	 - the act of populating a template with values fetched from the server and returning html to the requester

	```tsx
	interface Props{
		users: User[];
	}
	
	export default function(props: Props){
		return <>
			{props.users.map((user) => (<p>{user.username}</p>))}
		</>
	}
	
	// fetching the values here, and is provided to the view
	// above through the props parameter
	export const getServerSideProps = async () => {
		return { props: { users: await db.getAllUsers() } };
	}
	```

**Not all data fetching requires server side code**
We don't always have to fetch data from a database, sometimes it can be retrieved from a different file. (in NextJS)

```tsx
// since it's not fetching dynamic data from a db, we can import the hard coded json directly for use in the page 

import MyJsonContent from "../content.json";
export default function(){
	return <>
		{MyJsonContent.movies.map(
			(movie) => (<h1>{movie.title}</h1>)
		)}
	</>
}
```

# The better you can abuse an ORM - the better
- handles all SQL queries for you and maps the data and relations to objects in the language
	- in PHP `Eloquent` converts database rows into associative arrays and groups of rows into collections
	- in Next.js `Prisma` converts database rows into JavaScript objects and groups of rows into arrays

```js
const db = new PrismaClient();
async function main(){
	const users = await db.users.findMany({
		where: { 
			username: { endsWith: "@ust.edu.ph" },
		},
		include: { posts: true }
	});

	console.log(users);
}

main();
```
# Other things we do in backend
 - Image optimization
	 - frequently used assets should be optimized so they load faster for slower connections and use less bandwidth
	 - `next/image`
	 ```tsx
	import TomasinoWebLogo from "../assets/logos/logo.png"
	import Image from "next/image"

	export default function(){
		return <Image src={TomasinoWebLogo} alt="TW Logo" width={300}/>
	}
	```
	 - **When to use public and when to use assets:**
		- public folder for things that will change and path will be sourced from an external file
		- assets folder for images with known file path

 - Search engine optimization
	 - we need to put special tags at the head of our webpages that control the way our website appears to other websites
	 - helps with social media embeds / how we appear in google
	 - `next-seo` - programatically set meta tags

 - rendering markdown
	 - the core of `tomasinoweb.org` is to push markdown from the db to the user
	 - `react-markdown` is used to render markdown into react elements