**How to connect**
 - configuration for database access lives in `config/database.php`
 - define multiple connections then decide which the code will use by default
 - create named connections and still be able to set the driver in the named connections
	 - each connection allows you to define the properties necessary for connecting to and customizing each connection type
 - the connections section it comes out of the box is a template that makes it easy for apps to use any supported connection types
	 - you might need multiple connections within the same application
 - other config option
	 - redis access / customize table used for tracking migrations
	 - determine default connection
	 - whether non eloquent calls use stdClass or array instances
	 - sessions can also be backed using either database or file storage
	 - cache can either be memcached or redis
	 - you can define multiple connections and also choose that a particular connection be default
## Migrations
 - every new table, column, index, and key can be defined in code
 - a migration is a single file that defines
	 - the modification desired when running the migration up
	 - the modification desired when running the migration down
		 - rolling back / undoes whatever the up migration makes
 - `php artisan make:migration <name of migration>
	 - optional `--create=table_name` parameter prefills the migration with code designed to create a table called table_name
	 - optional `--table=__table_name__` prefills the migration for modifications to an existing table

**Creating tables**
 - Everything done in migrations relies of methods on the Schema Facade
```php
Schema::create('table_name', function (Blueprint $table){
	$table->string('column_name')->nullable();
	// other things you can chain
	// default(); // the default content for the column if no value is provided
	// unsigned() - marks an integer column as unsigned
	// first() - places column first in mysql
	// after() - places after another column in the column order
	// unique() - adds a unique index to the column
	// primary() - makes the column the primary key of the table
})
```

**Drop tables** - `Schema::drop('contacts')`
**Updating tables**
```php
	Schema::table('users', function($table){
		$table->string('name', 100)->change();
		$table->renameColumn('promoted', 'is_promoted');
		$table->dropColumn('column_name');
	})
```
## Primary keys and indexes
```php
$table->primary('primary_id'); // unnecessary when increments() is used in an an integer
$table->primary(['first_name', 'last_name']); // composite keys
$table->unique('email'); // unique index
$table->unique('email', 'custom_index_name');
$table->index('basic_index');
```
## Foreign keys
 - to add a foreign key that defines a particular column references a column on another table
	 - `$table->foreign('user_id')->references('id')->on('users');`
	 - creates a foreign index on the user_id column showing that it references the id column on the user table
	 - can chain `onDelete("cascade")` method
 - to drop an index
	 - `$table->dropForeign('contacts_user_id_foreign')`
	 - `$table->dropForeign(['user_id'])`
		 - pass an array of the fields that its referencing on the local table

`php artisan migrate`
- runs all outstanding migrations
- laravel keeps track of which migrations you have run and which you haven't

`php artisan migrate --seed`
`php artisan migrate:install` 
 - creates the database table that keeps track of which migrations you have / haven't run
`php artisan migrate:status` 
 - shows y/n beside each migration showing whether they have been run or not

## Seeding
 - there is a `database/seeds` folter that comes with a DatabaseSeeder class that has a `run()` method that is called when you call the seeder
 - `php artisan migrate --seed`
	 - seed the database as it's being migrated
 - `php artisan db:seed`
	 - run whatever you have defined in the run() methods of every seeder class
	 - could pass `--class` parameter to pick which class to use as seeder in the `database/seeds` folder
**Creating a seeder**
 - `php artisan make:seeder ContactsTableSeeder`
```php
public function run(){
	DB::table('contacts')->insert([
		'name' => 'name-here',
		'email' => 'email-here'
	])
}
```


Model factories can be used to create fake entries for your database
 - named after an eloquent class
 - are stored under `database/factories/ModelFactory.php`
```php
// User::class is an eloquent class
$factory->define(User:class, function(Faker\Generator $faker){
	return ['name' => $faker->name]
})

// can be as such
$contact = factory(ContactGenerator::class)->create();
factory(ContactGenerator::class, 20)->create();
// make() creates an instance but doesn't save it to the database
// create() - saves it to the database instantly
```

## Query Builder
 - fluent interface for interacting with the database
	 - uses method chaining to provide a simpler API than the end user
 - ``DB::select('select * from contacts where validated = ?', [true])``
	 - a basic prepared statement query
	 - pretty much the same as `DB::insert('insert into contacts (name, email) values (?, ?)', ['sally', 'email'])`
	 - same as update and delete statement
		 - these return the new of rows updated
 - `$users = DB::table('users')->get();`
```php
DB::table('users')->join('contacts', function($join){
	$join->on('users.id', "=", 'contacts.user_id')
		->where("contacts.type", "donor");
})->get();

// SELECT * FROM users INNER JOIN contacts ON users.id = contacts.user_id WHERE contacts.type = "donor";
```
 - methods a Collection for any method that returns multiple rows

**constraining methods**
 - take the query and constrain it to return a smaller subset of possible data
 - `select()` - choose which columns you are selecting, can also be used to alias columns
 - `where()` - limit the scope of what's being returned using WHERE
	 - first parameter = column name
	 - second name = comparison operator
	 - third parameter = value
	 - can chain multiple where statements one after another or pass an array of arrays to a single where clause
 - `orWhere()` - can be used to create a simple OR WHERE clause
	 - for more complex statements, it can be passed a closure
	```php
	->orWhere(function ($query){
		// WHERE something_condition OR (created_at > timestamp AND trial = false)
		$query->where('created_at', '>', 'timestamp')->where('trial', false);
	})
	```
	 - chaining a `where()` after an `orWhere()` makes the new `where()` call be appended using AND

**modifying methods**
 - change the way that query results will be output rather than limiting its results
 - `$contacts = DB:table('contacts')->orderBy('last_name', 'asc')->get();`
 - `$contacts = DB:table('contacts')->groupBy('city')->havingRaw('count(contact_id) > 30')->get();`
 - `skip()` and `take()`
	 - most often used for pagination
	 - define how many rows to return and how many to skip before starting the return
	 - page number and page size in a pagination system
 - `latest(colName)` and `oldest('colName')`
	 - sort by the passed column in descending or ascending order

**ending methods**
 - `get()` - get all results for the built query
 - `first()` - get only the first result
	 - fails silently if there are no results, `firstOrFail()` will throw an exception
	 - accepts an array of column names, will only return the data for those columns instead of all columns
 - `find(id)` - can pass an id value that corresponds to primary key look up
 - `value()` - plucks a single field from the first row
 - `count()` - returns number of rows in the result set
 - `min()` and `max()` - return the minimum / maximum value of a column in the resultset
 - `sum()` and `avg()` - return the sum or average of all of the values in a particular column

**Sql joins**
```php
// create an inner join, can use leftJoin() to create a left join instead
$users = DB:table('users')
	->join('contacts', 'users.id', '=', 'contact.user_id')
	->select('users', 'contacts.name', 'contacts.status')
	->get();

```
# Eloquent
```php
class Contact extends Model{
	// the name of the table, by default, it snake_cases the name of the model
	protected $table = "contacts";

	// each table will have an autoincrementing primary key named id by default
	protected $primaryKey = "id";
	public $incrementing = true;
	public $timestamps = true;
}
```

 - ActiveRecord orm
	 - single interface to interact with multiple database types
	 - a single eloquent class is responsible for representing each table row and also the entire table
 - `php artisan make:model Contact`
	 - can pass the `--migration` flag to automatically create a migration when you create your model
 - get everything using `Contacts:all();`
 - filter using `Contacts::where('property_name', "value")->get()`
	 - see below for a complete list of manipulating Eloquent's query builder
	 - everything you can do with the DB facade is possible with Eloquent
 ```php
 Contact::chunk(100, function ($contacts){
	 foreach($contacts as $contact){
		 // do something with contact
	 }
})
```

**Inserting and new data**
 - create a new instance of an Eloquent model than call save when you're done
 - could also pass an array to `Model::create` with column names as keys and property values  
	 - every property you set in `Model::create` has to be approved for mass assignment
		 - must have `fillable` and `guarded` properties in the Eloquent class that are string arrays of column names that can be filled using mass assignment and not
	 - don't need to call the `save()` method

**Updates**
 - get an instance, change it's properties then save it
 - can make a single call and pass an array of updated properties

**Deleting things**
 - `Contact::destroy(id);`
	 - can also pass an array of ids for records to delete

Accessors - define custom attributes to your eloquent models for when you are reading data from the model instance
 - change how a column is output
 - create an attribute that doesn't exist in the db table
 - create a public method in the model called `getAttributeNameAttribute`
 - mutators work in the same way but are for setting data

### Defining relationships
```php
class Contact extends Model{
	public function phoneNumber(){
		// phone_numbers table should have a contact_id column in it by default
		return $this->hasOne(PhoneNumber::class);
	}
}

class PhoneNumber extends Model{
	public function contact(){
		// for defining the inverse of a one-one and one-many relationship
		return $this->belongsTo(Contact::class);
	}
}

class User extends Model{
	public function contacts(){
		return $this->hasMany(Contact::class);
	}

	public function phoneNumbers(){
		// hasManyThrough - pulls in relationships of a relationships
		return $this->hasManyThrough(PhoneNumber::class, Contact:: class);
	}
}

$contact = Contact::first();
$contactPhone = $contact->phoneNumber;


// many to many relationships rely on a pivot table to store connect two tables
// conventional naming of this able is done by placing the two singular names together
// users and contacts table would be connected using contacts_users
// can pass the table name as the first parameter, it would require the columns contact_id and user_id
// return $this->belongsToMany()
```
## Collections

 - packages queries that return multiple rows
 - base collection
	 - arrays but expose methods that are helpful
	 - filter and map methods, methods that can be changed to perform functional operations on arrays
 - eloquent collections are normal collections but extended for the needs of a collection of eloquent results
	 - objects represent database rows
	 - has a method called `modelKeys()` that return an array of the primary keys of every instance in the collection
	 - `find($id)` that looks for an instance that has the primary key of $id
	 - you can define that any model should return its results wrapped in a specific collection class
	```php
	class Order extends Model{
		// any time you get a collection of orders, it wouldbe an instance of the OrderCollection class
		public function newCollection(arrays $models = []){
			return new OrderCollection($models);
		}
	}	 
	```

### Serialization
 - convert an array or an object into a string
 - done using the `toArray()` and `toJson()` methods
	 - can also cast directly to string
 - how to hide attributes and relationships
	 - add a `hidden` property in the model, which is an array of strings of the columns to not include in the json
	 - whitelist: `visible` allows you to do the opposite
	 - note: contents of relationships are not loaded when you get a database refo