Ruby on Rails
 - DHH released first version of rails in 2004
 - MVC / Restful json apis / convention over config / ActiveRecord

Laravel
 - shallow learning curve and minimizing the steps between creating a new app and publishing it
 - willing to use laravel's defaults, much less work than other frameworks
	 - dependency injection and mocking
	 - can be used with complex patterns
	 - expressive / dynamic and simple coding practices and language features

```php
Route::get('/', function(){
	return "Hello, world";
})

namespace app\Http\Controllers;
class WelcomeController{
	public function index(){
		return "Hello World";
	}
}
```

## Getting laravel to work
``composer global require "laravel/installer=~1.1"``
``laravel new projectName``

alternatively could also use create-project
`composer create-project laravel/laravel projectName --prefer-dist`

**Folder structure**
- app - bulk of application code
- bootstrap - files that laravel uses to boot when it runs
- config - config files
- database - migrations and seeds
- public - directory the server points to when its service the website
	- index.php - front controller that kicks of bootstrapping process and routes all requests appropriately
	- all public facing files
- resources - non-PHP files that are needed by other scripts
	- views / language files / sass and less / source JS files
- routes - route definitions lives for HTTP routes / console routes / artisan commands
- storage - caches / logs / compiled files
- tests - unit and integration tests
- vendor - node_modules

**Config**
 - each file in the config folder returns an array and each value in the array is accessible by a config key that is comprised of the filename and all descendant keys
	 - `config/services.php` returns an array that has a sparkpost array with secret value
	 - can be accessed using `config('services.sparkpost.secret')`
 - any config variables distinct for each environment should live in .env files
	 - can be pulled using `env("API_KEY_NAME_HERE")`

**Testing**
 - brings in PHPUnit as a dependency and is configured to run tests in any file in the tests directory that ends with Test.php
	 - `./vendor/bin/phpunit` from the command line