**Creational patterns**
 - independent of how objects are created, composed and represented
 - Class creational pattern - uses inheritance
 - Object creational pattern - delegates instantiation to another object
 - Are important when we move to fundamental classes that can be composed instead of specialized behaviours
 - Gives control on what, who, how and when something is created
 
 - **Factory method**
	 - Define an interface for creating an object, letting subclasses decide which class to instantiate
		 - Guarantees typesafety as subclasses generate products specific to them, instead of getting a non-typesafe product from their superclass
	 - An Application abstract class has a CreateDocument() method returning a Document, that is implemented by the subclass. This implementation returns a concrete MyDocument product.
		 - Application has a concrete method NewDocument(), which calls CreateDocument()
		 - From the perspective of MyApplication, everything is typesafe, since it decides which class to initiate.
		 - CreateDocument() is a factory method since it's responsible for creating an object that is used by other methods in the superclass.
	 - Useful when the superclass can't anticipate which class it must create, only knowing the generic interface of those objects / it needs the subclass to specify the objects it creates
		 - Creating objects inside a factory method is always more flexible than creating an object directly, this pattern provides hooks for generating an extended version of an object
	 - Implementations
		 - CreateDocument() is an abstract class that must be implemented by subclasses, or it has a default implementation that returns the generic product.
		 - CreateDocument() is concretely implemented / cannot be overriden, instead it takes a parameter that dictates the type of product subclass it creates.
	
 - **Abstract factory method**
	 - Provides an interface for creating families of related or dependent objects without specifying their concrete classes.
	 - Declare an abstract class (WidgetFactory) that defines an interface implemented by different standards
		 - Create an abstract class for each widget(Window/Scrollbar), which is also implemented by subclasses for each standard
		 - WidgetFactory has methods for creating Window and Scollbar, and the WidgetFactory's implementations' implement this by returning subclasses of Window and Scrollbar according to their specific standard.
		 - Clients can call WidgetFactory's methods and not be aware of the concrete classes they are using, thus their behaviour commits to the interface by an abstract class, not a particular concrete class.
	 - The AbstractFactory defers creation of product objects to its concrete subclasses.
		 - Makes exchanging product families easy, and promotes consistency among products
		 - Isolates clients from implementation classes, they can only work with the interface presented to them.
		 - Supporting new kinds of products is difficult, since all implementations will have to be updated when adding a new product

 - **Builder pattern**
	 - Separate the construction of a complex object from its representation so that the same construction process can create different representations
		 - Is called the builder pattern as each subclass is a builder with different implementations on constructing the complex object.
		 - Useful when you need to construct different outputs from the same input, since you can just swap the builder that you're using to make it.
		 - The builder hides the internal representation of the product through an abstract interface. To create a new product, you just have to define a new kin of builder.
		 - Clients don't need to know anything about how the classes that define the product's internal structure.
	 - LLVM has to compile its intermediate representation to different computers, the Compiler class can use a single Architecture interface which is then implemented by subclasses representing different architectures.
		 - Architecture interface has a method for each possible bytecode, and these methods are implemented by subclasses for hardware specific instruction sets.
		 - Each architecture class is referred as a **builder**, and the compiler class is called the **director**
		 - The algorithm for generating binary files is separate from the compiler
		   
 - **Prototype pattern**
	 - Specify the kinds of objects to create using a prototypical instance.
	 - The client creates a new object by asking a prototype to clone itself, it doesn't need to know what the prototype contains or what it can do with the prototype aside from the common interface (Clone(), Draw())
		 - Is useful when the programmer does not control the client, IE is using a framework. The programmer can write prototypes that the framework can use in a reliable way, even if the framework is not written for the programmer's specific needs in mind.
		   
- **Singleton pattern**
	- Some classes must only have one instance. The singleton pattern makes the class itself responsible for keeping track of its sole instance, ensuring no other instance can be created.
		- It is easy to change the number of instances possible when using this pattern. Only the operation that grants access to the singleton instance needs to change.
	- Implementation
		- Hide the operation that creates the instance behind a static member function that has access to the variable that has access to the unique instance.

**Structural patterns**
 - Concerned with how classes and objects are composed to form larger structures
 - class patterns - use inheritance to compose interfaces or implementations
 - object patterns - describe ways to compose objects to realize new functionality
 - **Adapter** (Wrapper)
	 - Convert the interface of a class into another interface that clients expect so they can work together even if they have incompatible interfaces
	 - Maintains separation of concerns between your application code and libraries since your application code doesn't have to be written specifically to be understood by the library
	 - Class composition - uses multiple inheritance so that the library and framework code can live inside the same class definition, without composition
	 - Object composition
		 - Create a subclass that can be used by the framework, and have a property in the subclass that composes a class from the application code.
			 - Example: TextShape extends from Shape in a drawing framework. TextShape has a instance property for TextView, which is your own code. This way TextView can be written agnostically without the framework in mind. The TextShape adapter can be changed.
	 - Consequences
		 - (Class Adapters) The Adapter can override some of adaptee's behaviour since the Adapter is a subclass of adaptee
		 - (Object Adapters) Lets a single adapter with many adaptees, all the subclasses of Adaptee are supported, adding functionality to all adaptees at once.
			 - Makes it harder to override adaptee's behavior since it's not a subclass but rather composition
 - **Bridge**
	 - Decouple an abstraction from its implementation so that the two can vary independently
	 - Inheritance binds an implementation to the abstraction permanently
	 - The bridge pattern keeps the inheritance hierarchy clean by not mixing implementations alongside the abstractions.
		 - It relies on an implementation class that provides primitives for instructions, which is used in the root class
			 - Example: A Window class has DrawText() and DrawRect() nodes that is used by subclass to create more complex behaviour like DrawBorder() methods. The Window class has an implementation variable of class WindowImp that contains methods which are implemented by different Window systems
			 - This means that the Window class hierarchy is completely removed from the implementation hierarchy. This is opposed to every class under window having their own subclasses implementing window system specific behaviour.
		 - Avoids permanent binding between an abstraction and implementation, the implementation can be chosen at runtime.