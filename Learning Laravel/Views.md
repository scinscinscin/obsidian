 - MVC - views are files that describe what some output should look like
 - could either be in plain PHP or blade templates
	 - php is rendered using the php engine
	 - blade is rendered using the blade engine
 - once a view is loaded it can simply be returned if it doesn't use any variables from the controller
 - view method looks at `resources/views/*.blade.php` or `resources/views/*.php` by default and loads its contents and parses any inline PHP until you have the view's output
	 - can pass variables using `with()` method 
		 - `return view(view_name)->with('tasks', Task::all());`
		 - passes a single variable named tasks which contains the result of the `Task::all()` static method
	 - view composes can be used to share variables with every view
		 - share certain variables with every template or just certain templates like in all code
		 - `view()->share('variableName', 'variableValue');`
## Controllers

 - classes that organize the logic of one or more routes together in one place
 - tend to group similar routes together
	 - a single controller might handle all the actions that can be performed on a resource
 - capture the intent of an HTTP request and pass it to the rest of the application
 - `php artisan make:controller TasksController`
	 - artisan can be used to run migrations / create users and other database records
	 - under make, it provides tools for generating skeleton files for a variety of system files
	 - creates a new file under `app/Http/Controllers` called `TasksController.php`
	 - can pass the `--resource` flag to create the controller with CRUD methods

## User input

 - in the Controller method called by the POST route, we can access body parameters using the`Input::get(parameter_name)` method
	 - Input is a facade, could also be pulled from the Request object
		 - facades are not present in every namespace, it must be imported using `use Illuminate\Support\facades\Input;`
		 - are an alternative to dependency injection
	 - typically, create a new database model instance, pull data from the user input and set it on the task
	 - save it then redirect back to the page that shows all the tasks
 - Laravel service container
	 - all controller methods are resolved out of Laravel's container, anything you typehint that the container knows how to resolve will be automatically injected
	 ```php
	 // define that a parameter must be passed into the store method
	 // Laravel knows how to resolve this so the Request object is ready in your method
	 public function store(\Illunminate\Http\Request $request){
		 $task = new Task;
		 $task->title = $request->input('title');
	 }
	```