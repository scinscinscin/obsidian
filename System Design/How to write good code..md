**Simplicity**
 - not about using shortcuts and creating the quickest solution to the problem at hand
 - Easiest way for another software engineer to understand your solution in the future
 - comprehend the system as it grows larger and more complex

**Hide complexity and build abstractions**
 - you will not be able to build a mental picture of the entire system as there would be too many details
 - Your code must allow to zoom in and out the context to see larger and smaller parts of the system
 - Local simplicity - look at any single class / module and understand its purpose and how it works
	 - When looking at a class you should see how it works without knowing all the details of how other remote parts of the system work
	 - Separate functionality into modules so you can look at the higher level of abstraction. You need not be worried about how modules perform their duties but how they interact
 - Complexity is not about how many nodes you have in your network, but how many edges you have between the nodes
	 - Nodes should be understood on their own and outside the context of other classes
	 - No class should depend on a more than few other interface or classes
	 - **Interactions between classes and modules are what's important**

**Avoid overengineering**
 - when you try to predict every possible edge case, you lose focus on the most common use-cases. 
 - Good design allows you to add more features later on, but does not require you to build a massive solution up front.
	 - iterating over it gives better results than trying to predict the future and build everything that might be needed later on

**Test driven development** - engineers write tests first and then implement the actual functionality
	there is no code without unit tests and there is no spare code
 - they would not add unnecessary functionality as it would require them to write tests for it as well
 - tests can be used as documentation

**Loose coupling**
 - keep coupling between parts of your system as low as necessary
 - Coupling is a measure of how much two components know and depend on each other. 
	 - the higher the coupling, the higher the dependency and less code reuse
	 - Loose coupling refers to components that know as little as possible about each other.
		 - Introduce changes without breaking other parts of the system
		 - Keep complexity localized, have multiple engineers work on them independently
		 - No one knows the entire system in full detail
		 - A class is the smallest unit of abstraction. 
			 - A class should have a single purpose and no more than a few screens of code
			 - You can promote coupling by correct use of public protected and private keywords
				 - declare as many methods as private and protected and therefore hide the implementation from the outside world
		 - Share the absolute minimum amount of information that satisfies the requirements. Sharing too much too early increases coupling and makes changes more difficult in the future.
- Unnecessary coupling
	- Methods have to be invoked in a specific order
		- Increases coupling as now the order is also a part of the usage, not just the method signature
	- Circular dependencies between layers of your application

**Coding to contract**
 - extract the things the clients are allowed to see and depend upon
 - decouple parts of your system and isolate changes is a key benefit discussed earlier in the chapter
 - Contract - a set of rules that the provider of the functionality agrees to fulfill
	 - a set of the things that the code may assume and depend upon
	 - the public interface of a class
		 - low level: All accessible methods and their signatures. 
		 - high level: some form of web service and API specification
	 - think of what the clients really need and then define the minimal interface as the contract.

**Class diagrams**
 - present the structure of individual modules
 - interface / classes / key method names / relationships between different elements
 - Each class becomes a node of the diagram and each dependency becomes a line
 - See which classes are coupled with the rest of the module and which are more independent

**Module diagrams**
 - displays structure and dependencies
 - focuses on a higher level of abstraction, with less depth but more surface area.
 - Relationships between larger parts of the system

## Single responsibility
 - every class should have one single responsibility and no more
 - decreases coupling and increases simplicity
 - makes it easy to refactor reuse and unit test your code
 - Classes become large and closely coupled with each other if we don't take care when adding new features.
	 - Large classes make it hard to understand its behaviour and its role
	 - The complexity rises sharply with every new line of code
 - Some guidelines
	 - keep class lengths below two to four screens of coed
	 - ensure a class depends no more than five other interfaces / classes
	 - Ensure that a class has a goal and purpose
	 -  Summarize the responsibility of the class in a single sentence and put it in a comment at the top of the class name. 
 - We end up with more testable code that have less logic and fewer dependencies.

## Open closed principle
 - creating code that doesn't have to be modified when requirements change and new use cases arise
 - Open for extension but closed for modification, ie: creating code with the intent to extend it in the future without the need to modify it
	 - Leaves more options available and delay decisions about the details
	 - Increases flexibility of your software and makes future changes cheaper
	 - Instead of having a class that has a fixed implementation of what it can do, we can break it down into parts and use interfaces to define contracts to allow it do operations on multiple types of entities.

## Dependency injection
 - provides references to objects that the class depends on than allowing the class to gather the dependencies itself
 - allows classes to not know how their dependencies are assembled
 - reduces the local complexity of the class and makes it dumber, removing assembly code from your classes
	 - makes them more independent, reusable and testable.

## Inversion of Control
 - important principle and a subclass of a broader principle called inversion of control
 - a generic ideas that can be applied to different problems
 - **removing responsibilities from a class to make it simpler and less coupled to the rest of the system**
	 - not having to know who will create and use your objects, how, or when
	 - the framework runs the code that you write
	 - properties
		 - Create plugins for your framework
		 - Each plugin is dependent and can be added or removed at any point in time
		 - framework can auto detect these plugins or there is a way of configuring which plugin should be used and how
		 - the plugin code that the user writes has no control over how it is run

## Adding more clones
- clones should be idempotent and identical, they should be stateless
- perfectly interchangeable web servers and distribute the load equally among them all
- distributed among clones using a load balancer where the LB doesn't need to know where the previous request went
- **need to keep track of there state is stored and how state changes propagate**
		
## Functional partitioning
- look for parts of the system focused on a specific functionality and create independent subsystems out of  them
 - isolation of different functions into different subsystems
	 - If a subsystem requires X different services to function, they should be colocated together instead of type per server all colocated together.
 - split a monolithic web application into a set of smaller functional services
	 - multiple teams working in parallel on independent codebases and gaining more flexibility in scaling each service

## Data partitioning
 - partition the data to keep subsets of it on each machine instead of cloning the entire data set onto each machine
 - Each node is fully autonomous, each node can make decisions about its state without the need to propagate state changes to its peers.
 - allows for infinite scalability
 - keep track of which servers answered the requests prior
 - the most complex and expensive technique since you need to track the partition on which the data lives before sending queries to the servers

## Self healing services
 - make the service appear as if all of its components were functioning perfectly even when things break during maintenance times
 - highly available system
	 - expected to be available to its clients most of the time
	 - different services have different outage tolerances
	 - the larger your system gets, the higher the chance of failure
		 - A component that relies on 15 different services will become unavailable even if only one of those different services goes down unless you handle failures gracefully or fail over transparently
		 - Failures become much more of a frequent occurrence.
 - prepare for the worst, think about what can fail and in what order
 - crash only - whenever it reboots, it should be able to continue to work without human interaction. 
	 - the system detects its own failure and fix the broken data if necessary and resume work as normal
 - **Single point of failure** - any piece of infra that is necessary for the system to work properly
	 - DNS / database master server
 - Redundancy - having more than one copy of each piece of data or each component of the infrastructure.
	 - the system can use the remaining clones to serve clients' requests. Systems that are not redundant just need special attention.
 - 

