**Collection interface**
- root interface int he collection hierarchy
- Represents a group of objects, known as its elements
- Some allow duplicates and others don't
- Some are ordered and unordered
- Used to pass collections around when maximum generality is needed

Collection
 - Set
	 - SortedSet
	 - Is an unordered collection, sequence is not ensured
	 - Duplicates are not permitted, all elements are unqiue
	 - At most, only one element can be null
 - List
	 - Ordered collection
	 - The user has control of where each element is inserted
	 - Can access elements by their integer index and search for elements in the list
	 - Duplicates are permitted
 - Queue
	 - Deque (stands for double ended queue)
	 - Is implemented directly by priority queue
	 - uses the compareTo method to determine the natural ordering of objects 
	 - is implemented by ArrayDeque
		 - adds a new element at the end of the collection using the add method and removes elements from the collection using the remove method
		 - can be used as a Queue using the addLast and removeFirst methods
		 - can be used as a stack using the addFirst and removeFirst methods

Map is not a subinterface of Collection
 - A data structure used to hold elements that can be accessed through a unique identifier
 - Cannot contain duplicate keys but can contain duplicate values
 - Can get the set of keys using the keySet method
 - Can get a set containing Map.Entry using entrySet method
	 - Map.Entry class has a getKey() and getValue() method

Iterator
 - an object that can be used to look through collections
 - ListIterator is a java iterator used to iterate elements one by one from List
	 - supports both forward and backwards
	 - is only possible with a List because of its sequential representation 

Generics
 - Supports for the parameterization of types called <E>
 - Reduces the amnt of code written when placing an object to and from a collection
 - Generics provide compile time typesafety that allows programmers to catch invalid types at compile time
 - Diamond operator
	 - Starting java7, you don't need to specify the type during instantiation

The Comparable interface
 - override the compareTo method from the Comparable interface
 - Set: Use treeset instead of hashset
 - List: call Collections.sort(list) to sort in ascending order and reverseOrder to sort in descending order
 - Map: use TreeMap to sort keys automatically
 - Create an iterator object to iterate through your set

Comparator interface
 - defines a single method
 - compare(T o1, T o2)
 - compare two objects, not this and another object
 - is passed as the second parameter into Collections.sort when the collection to be sorted does not implement the Comparable interface
 - 