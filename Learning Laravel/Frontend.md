Elixir
 - build tool that provides an interface on top of Gulp
 - can preprocess css using sass / less
 - can minify the files it generates

Pagination
 - displaying the results of a database query and too many results for a single page
 - Eloquent and the query builder and uses it to provide a paginate method on any result sets
 - `return view('posts.index', ['posts' => DB::table('posts')->paginate(20)]);`

## Validating data
- can inject the Request object into the route handler
	- alternatively use the request global helper or the Request facade
```php
Route::post('form', function(Request $request){
	// returns an array containing all the info the user has provided
	// form body and query parameters
	$request->all(); 

	// can choose one or more fields to exclude by passing either a string or an array of strings
	$request->except();
	$request->only(); // is the inverse of except() method

	// detect if a piece of user input is available
	$request->has(); // returns FALSE if the key exists and is empty
	$request->exists(); // returns TRUE if the key exists and is empty

	// get the value of just a single field
	// the second variable is the default value if name is not provided
	$request->input('name', '(anonymous)';

	// you can use dot notation to get values in arrays
	// employees.0.firstName, employees.*.lastname, employees.1
	// this is also applicable for json inputs
	// $request->json() picks up bodies without application/json header

	// returns an array of segments()
	// if passed a number, it allows us to get the value in a single segment
	// 1-index
	$request->segments();

	// make sure that the upload form is using multiparty/form-data for the upload
	if(
		$request->hasFile('profile_picture') && 
		$request->file('profile_picture')->isValid()
	) // the file method returns a UploadedFile class that extends SplFileInfo
		var_dump($request->file('profile_picture'));
})
```

## Validation
 - can use the `validate()` method of the Controller in the methods to check if the request has the specified properties
	 - throws a ValidationException, with instructions on how to handle depending if the caller is AJAX or an HTML form
 ```php
	 $this->validate($request, [
		 // required and has a maximum of 125 char length
		 // must be unique in the proeprty_name column of recipes table
		 'property_name' => 'required|unique:recipes|max:125'
	 ])

	// can display errors using
	// should check beforehand if there are any errors using $errors->any()
	@foreach($errors->all() as $error)
		<li>{{ $error }}</li>
	@endforeach
```