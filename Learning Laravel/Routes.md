 - we define web routes in `routes/web.php` and API routes in `routes/api.php`
	 - web routes are those that will be visited by your end users
		 ```php
		 // create a closure, which is an anonymous function in PHP
		 Route::get("/", function(){
			 // we could also return a view
			 // return view(name of view);
			 return "Hello World";
		 })

		 Route::match(["get", "post"], '/', function(){
		 
		 });
		 
		 $router->get("/", function(){
			 return "hello, world";
		 })
		```
	 - api routes are those for your api
 - Route closures can't take advantage of laravel's route caching which can save time per request
	 - we can use **controller methods** instead
	 - `Route::get('/', 'WelcomeController@index')`
		 - pass requests to the path of the index method of the WelcomeController class
		 - will be passed the same parameters and treated the same way as a closure
	 - `Route::get('users/{id}/friends', function($id){})`
		 - if you are defining path parameters, the segments in the URL structure map to method parameters in the closure
		 - path parameters are provided to the route handler in order of declaration
		 - they can also be optional using a question mark, can be provided a default value in the parameter declaration
	 - Can use regexs to define a route that should only match if a parameter meets particular requirements
	```php
	Route::get('users/{id}', function($id){})->where('id', '[0-9]+');
	Route::get('users/{username}', function($username){})->where('username', '[A-Za-z]+');
	// could also provide multiple validators by providing an associative array to the where method and the keys are path parameter names
	```
 - you can list all routes using `php artisan route:list`

**Route names**
 - refer to routes elsewhere in your application just by their path
 - `url()` helper that simplifies linking to your views when you need it
	 - can give nicknames to complex routes using the `name()` method when you define a route in the web.php file
	 - `Route::get('members/{id}', MembersController@show)->name('members.show');`
		 - naming convention is `<resource>.<action>`
 - `<?php echo route('members.show', ['id' => 14]); ?>`
	 - `route()` is intended to be used in views so simply linking to a named route
	 - if route has no parameters you can pass the route name only and receive a route string
	 - if it has parameters, pass them as an array as the second parameter

**Route Groups**
 - a group of routes share a characteristic (middleware)
 - route groups allow you to group routes together and apply shared configuration settings once to the entire group to reduce dupe
```php
// apply auth middleware to a group of routes
Route::group(["middleware" => "auth", "prefix"=>"api"], function(){
	Route.get('/hello', function(){
		// is defined under /api/hello
		return "Hello";
	})
})

// other options also include domain property so the route is only called when through that one subdomain. is also useful for multitenancy where each client has it's own subdomain
Route::group(['domain' => '{account}.domain.com'], function(){
	Route::get("users/{id}", function($account, $id){
		
	})	
})
	
// we can also attach middleware straight into the routes at the controller instead of the route definitionusing the middleware method in the controller's constructor
class DashboardController extends Controller{
	public function __construct(){
		$this->middleware('auth');
	}
}
```
## Resource controllers

 - a controller that has REST / CRUD methods
 - comes with a generator out of the box and a convenience route definition that allows you to bind an entire controller all at once
	 - `Route::resource('tasks', 'TasksController');`
 - `php artisan make:controller MySampleResourceController --resource`
	 - creates the index(), create(), store(), show(), edit(), update(), and destroy() methods

**Route model binding**
 - allows you to define that a route parameter in the route resolved that it should look up an Eloquent record with that id and pass it into the parameter
 - Implicit route
	 - name your route parameter something unique to that model and then typehint that parameter in the handler method and use the same variable name there
 - Custom route model binding
	 - change the boot method in RouteServiceProvider
	 - `$router->model('event', Conference::class);`
		 - whenever a route has a parameter named event, the route resolved will return an instance of the `Conference` class with the id of the url parameter
		 - Primary key can be controlled using the `getRouteKeyName()` method in the class model

**Route caching**
 - must be using all controller and resource routes
 - `php artisan route:cache`
	 - serializes the results of routes files
 - laravel now matches routes against the cached file instead of the files in the routes folder
 - you will have to recache each time you make a change
 - only route cache in prod

**Form method spoofing**
 - html forms only allow get or post
 - informs laravel that the form you're submitting should be treated as something other than POST **by adding a hidden variable called `_method` with the value of PUT PATCH or DELETE**
	 - laravel will automatically match that route as if it was actually requested with that verb
	 - `<input type="hidden" name="_method" value="DELETE">`

**CSRF**
 - input named token is passed along each request, every non ready only route compares the submitted token against the session token
 - laravel checks X-CSRF-TOKEN header on every request
	 - results in TokenMismatchException when they don't match
 - `<input type="hidden" name="_token" value="<?php echo csrf_token(); ?>">`

**Redirects**
 - we can return other instructions to tell the browser what to do
 - `return redirect()->to('login');`
	 - `$status` - the http status that defaults to 302 FOUND, could return 301 permanent
	 - `$headers` - define which http headers are to send along with your redirect
	 - `$secure` - whether to override http versus https
 - `return redirect('login');`
 - `return Redirect::to('login');`
 - `return redirect()->route();`
	 - points to a route name instead of pointing to a path
	 - the 2nd parameter is an associative array containing path parameter values for the chosen route name
 - `redirect()->back();`
	 - redirects the user to whatever page they came from
 - `redirect()->with();`
	 - pass data along with them when redirecting to different pages
	 - stored in the user's session
	 - `return redirect('dashboard')->with(['error => true, 'message] => 'whoops');`

**abort**
 - exit from processing a route early
 - `abort(code, "message")`
	 - could also use `abort_unless` whose first parameter must be true for execution to *continue*
	 - `abort_if` first parameter must be false for execution to continue

**Responses**
 - `response()->make();`
	 - first parameter is the body
	 - second parameter is the status code
	 - third parameter is the headers
 - `response()->json(); response()->jsonp();`
	 - json encoded http response
	 - must pass serializable content such as arrays to the json method
	 - uses `json_encode()` to serialize the content and sets appropriate headers
 - `response()->download()` and `response()->file()`
	 - accepts an `SplFileInfo` instance or a string filename to download
	 - second parameter is an optional filename
	 - use `file()` to display it in the browser instead of downloading