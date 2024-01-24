# Structures
 - each element is named and has its own data type
 - structures may be initialized at declaration time by putting the list of elements in curly braces
 - the definition of structure and variable can be combined one step
```c++
// Declare a variable of type bin, which has a field called name that has a type of char[30]
struct bin {
	char name[30]
} printer_cable_box = { "Printer Cables" };
```

# Unions
 - it defines a single location that can be given many different field names
 - can be used to create a tagged union, where a union is inside a struct that has a "kind" property
```c++
// these two fields share the same space, only one is active at a time
// if you set something in i_value, assigning something to f_value will delete the old i_value 
union value{
	long int i_value;
	float f_value;
}

struct TaggedUnion{
	int kind;
	union value data;
}
```

# Typedef
 - provides a way to extend C++'s basic types
 - `typedef type-decl`
	 - same as a variable declaration except a typename is used instead of a variable name
	 - `typedef int width`
 - Can be used to define more complex objects beyond the scope of a `#define`
 - `typedef int group[10]`
	 - create a new type called group that is an `int[10]`

# enum
 - an enumerated data type, can only contain a limited set of values
 - values are referenced by the name
 - The compiler assigns each tag an int value internally
 - `enum Day { SUNDAY, MONDAY, TUESDAY, ..., SATURDAY }`

# Bitpacked structures
 - packed structures allow you to declare structures in a way that takes a minimum of storage
 ```c++
 // takes up 16 bits in total in memory
 // list and seen only use 1 bit for each field, is an expensive operation to take the value out of memory
 struct item{
	 unsigned int list:1;
	 unsigned int seen:1;
	 unsigned int number: 14;
 }
 ```

# Class
 - using a class is like using a structure (defined with word class instead of struct)
 - the members of a class can be both data and functions, can only access members that are public
 - C++ will automatically call a number of member functions
	 - constructor function - has the same name as the class
		 - a variable is created when it is declared (can also be created using the new operator), so declaring a variable is a class type calls the constructor of that class
		 - a constructor can be overloaded
		 - a constructor can be parameterized
		 ```c++
		person::person(const char i_name[], const char i_phone[]){
			// do things with i_name and i_phone here
		} 

		person person_instance("Name here", "number here");
		```
	 - destructor function
		 - is called when the variable is destroyed
		 - goes out of scope or when a pointer is deleted (using the `delete operator`)
		 - special name is the class name with a tilde in front of it
		 ```c++
		 stack::~stack(void){
			 if(count != 0) cerr << "Attempted to delete a non empty stack";
		 }
		```
	 - copy constructor
		 - is used to make an exact copy of a class
		 ```c++
		 // this function is expected to turn the current class into an exact copy of the parameter
		 // is automatically called when the reference of a stack is passed into a parameter of a function that is expecing the stack itself
		 stack::stack(const stack &old_stack){}
		```

It is possible to define the body of a function inside the class itself instead of using function prototypes.
```c++
class Stack{
	public:
		void push(const int item){
			// perform operation here
		}
}
```