## Generics
 - an interface can be declared to have one or more type parameters
	 - written in angle brackets and supplied when declaring a new variable belonging to the interface / class when creating a new class
	 - type parameters must always be bound to reference types and not primitive types
		 - Each primitive type in java has a corresponding library class of a reference type in the `java.lang` package
			- primitive -> reference = **boxing**
			- reference -> primitive = **unboxing**
		- java automatically inserts boxing and unboxing coercions when appropriate
			- equality is defined differently on primitive and reference types
			- `int` - equality of values
			- `Integer` - object identity
 - `ArrayList<R> implements List<R>`
 - generics are implemented by erasure because `List<Integer>` and `List<String>` are all represented at run-time by the same shape
	 - the process erases type parameters but adds cast
		 - in C++, templates are defined by expansion
			 - each instance of a template of a new type is compiled separately
			 - a hundred different list types will have a hundred versions of the code
	 - no matter how many types of list are used, there is always one version of the code
	 - implicit casts by the compilation of generics never fail IF there are no unchecked warnings by the compiler
 - array types differ in key ways from parameterized types
	 - `new String[size]` - allocates an array and stores info in the array that its components are of type string
	 - `new ArrayList<String>()` - allocates a list but does not store in the list any indication of the type of its elements
 - **Generic methods**
	 - indicated by writing `<T>` at the beginning of the method signature, which declares T as a type variable
		 - scope and type of T is local to the method itself, may appear in the method signature and inside the method body
	```java
	class Lists{
		// triple dot is a variable argument
		// one may either pass a list of arguments to be implicitly packed or pass the array instead
		// will create an unchecked warning since this will create an array of a generic type, var
		public static <T> List<T> toList(T... arr){
			/* add some code here */
		}
	}

	// these two are the same, at runtime, arguments are packed into an array which is passed to the method
	List<Integer> ints = Lists.toList(new Integer[] { 1, 2, 3 });
	List<Integer> ints = Lists.toList(1, 2, 3);

	// explicit parameters can be provided in calls that have a dotted form
	List<Object> objs = Lists.<Object>toList(1, "two");
	```

**Foreach loop**
 - can be applied to any object that implements the interface `Iterable<E>`
 - can also be applied to an array
 - is kept simple and catches only a common case

## Subtyping
 - one type is a subtype of another if they are related by an `extends` or `implements` clause
	 - Integer is a subtype of Number
	 - Double is a subtype of Number
	 - `ArrayList<E>` is a subtype of `List<E>`
 - **transitive** - if one type is a subtype of a second, and the second is a subtype of a third, the first is a subtype of the third
	 - every reference type is a subtype of `Object` and it is a super type of every reference type
	 - every type is a subtype of itself
 - Substitution principle - wherever a value of one type is expected, we can provide a value of any subtype of that type
	 - a given type may be assigned a value of any subtype of any type
	 - a method with a parameter of a given type may be invoked with an argument of any subtype of that type
 - `Integer` is a subtype of `Number` but `List<Integer>` is not a subtype of `List<Number>`
	 - `Integer[]` is a subtype of `Number[]`
		 - array subtyping is covariant
	 - an argument of type `List<Integer>` can be passed into a method expecting a parameter type of `List<Numbers>` using the wildcard statement
 - **wildcard statement** allows you to get elements but not put elements in the structure
	 - use an extends wildcard when you only get values out of a structure
		 - `? extends T` - refers to collections that when fetched from, is guaranteed to have a type of T
	 - `? super T` - the destination may have elements of any type that is a supertype of T
		 - refers to all collections that can contain a value of T
		 - use a super wildcard when you only put values into a structure, and don't use a wildcard when you get and put into a collection

![[Interfaces and Enums]]
# Collections
## `Iterable` interface
 - defines the contract that has a class to fulfill for its instances to be usable with the `foreach` statement
 - is implemented by all collections, sets, and lists
 - has the `iterator()` method that returns an **`Iterator` object**
	 - provides a uniform way of accessing collection elements sequentially
	 - methods
		 - `hasNext()` - returns true if the iteration has more elements
		 - `E next()` - returns the next element in the iteration
		 - `void remove()` - removes the last element returned by the iterator

## `Collection` interface
  - core functionality required for any collection other than a map
 - no direct concrete implementations
	 - `AbstractCollection` / `AbstractSet` / `AbstractList`
		- provides functionality common to different concrete implementations of each interface
 - **methods for adding elements**
	 - `boolean add(E e)`
	 - `boolean addAll(Collection <? extends E> c)`
	 - these methods return true if the collection was changed by the call
		 - can be false for sets if they are asked to add elements that are already present
	 - will throw an Exception if they are asked to add elements that cannot be added
 - **methods for removing elements**
	 - `boolean remove(Object o)`
		 - removes any element `e` in the collection if `o.equals(e)`
	 - `void clear()` - remove all elements
	 - `boolean removeAll(Collection<?> c)` - remove all the elements in C
		 - returns the set difference between current and c
	 - `boolean retainAll(Collection<?> c)`
		 - remove all the elements not in C
		 - returns the set intersection between current and c
	 - returns a true if the collection is changed
 - **methods for querying contents**
	 - `boolean contains(Object o)`
		 - returns true if there is an element `e` such that `o.equals(e)`
	 - `boolean containsAll(Collection<?> c)`
		 - returns true if all elements of c are present in the collection
	 - `boolean isEmpty()` - true if no elements are present
	 - `int size()` - returns the element count
 - **methods that make it available for further processing**
	 - `iterator()` - return an iterator over the elements
	 - `Object[] toArray()` - copy the contents to an `Object[]`
		 - convert the collection into an array
 - constructors
	 - `public HashSet()`
		 - creates an empty set
	 - `public HashSet(Collection<? extends E> c)`
		 - a set that will contain the elements of any collection
		 - create an empty set with the default constructor then adding the contents of c using `addAll()`
		 - sometimes called a copy constructor
## `Set` interface
 - a collection without duplicates, and in which order is not significant
 - `SortedSet` - sorts elements and returns them in order
	 - `NavigableSet` - extends `SortedSet`, adding methods to find closest matches to a target element
 - `HashSet`
	 - most commonly used implementation of Set, and is implemented using a hash table (specifically, a specialized `HashMap`)
		 - an array in which elements are stored at a position derived from their contents
		 - the position is calculated by a hash function of its contents, which are designed to give an even spread of results over the element values that might be stored
		 - when elements collide, we store them in buckets, usually done by storing them in linked lists
	 - **the order in which elements are iterated on depends on their hashcodes, there is no guarantee on the order in which elements are returned**
	 - has constant time performance for basic operations, but poor iteration performance since iterating requires to check every bucket in the underlying hashmap
 - `LinkedHashSet`
	 -  iterators will return their elements in the order that they were added
		 - done by maintaining a linked list of set elements
	 - `next()` performs in constant time since the linked list can be used to visit each element in turn
		 - results in better performance than `HashSet` since buckets don't need to be visited, nodes themselves link to each other
 - `TreeSet`
	 - trees are used when you need fast insertion and retrieval of individual elements and also require they be held in sorted order
		 - trees are a branching structure that represent hierarchy
	 - uses a balancing tree called a `red-black` tree that can be rebalanced in O(log n) time
		 - is a binary search tree that has the minimum height possible, to be searched as fast as it can
		 - similar to AVL trees, just uses a different balancing technique

## `Queue`
 - accept elements at the tail for processing, yielding at the head in the order they are processed
 - includes methods aside from those inherited
	 - `offer(e: E): boolean` - add an element at the tail of the queue
		 - insert the element if possible
	 - `element(): E` - retrieve the head element, throw if null
	 - `removed(): E` - retrieve and remove the head element, throw if null
	 - `peek(): E` - retrieve the head element, **return null if null**
	 - `poll(): E` - retrieve and remove the head element, **return null if null**
 - `Deque` - extends by allowing elements to be added or removed at both head and tail
	 - Deque's contract specifies the ordering it will use in presenting its elements
	 - linear structure in which elements added to the tail are yielded up in the same order at the head (is always first in first out)
	 - if elements are removed from the same end, it acts as a last in first out data structure
	 - adds new methods symmetric with respect to head and tail
		 - it also renames some methods to make their behavior explicit for deque
		 - `addFirst(e: E)`, `addLast(e: E)`, `offerFirst(e: E)`, `offerLast(e: E)`
		 - `peekFirst()`, `peekLast()`, `removeFirst()`, `removeLast()`
 - `BlockingQueue` and `BlockingDeque` - supports concurrent access and allows threads to be blocked, indefinitely or for a maximum time until an operation can be carried out
 - `PriorityQueue`
	 - implemented using priority heaps
		 - heap - binary tree where each node should be larger than its children
			 - the tree must be complete at every level except the lowest
			 - inserting and removing elements is performed using `heapifyUp` and `heapifyDown` procedures
 - `LinkedList`
	 - permitting null elements, which are not allowed in the Queue interface because the use of null as a special value
	 - based on a linked list structure
		 - with an extra field in each cell, pointing to the previous entry
		 - allows the list to be traversed backwards for reverse iteration, or to remove an element from the end of the list
 - `ArrayDeque` 
	 - general choice for first in first out and deque applications
	 - adding and removing elements at the head or tail takes constant time
 
## `List`
 - collection in which order is significant, allowing duplicate elements

**Methods**
 - has methods for positional access
	 - `add(int index, E e)` - add element e at a given index
	 - `boolean addAll(int index, Collection<? extends E> c)`
		 - add contents of c at given index
	 - `E get(int index)` - return element at a given index
	 - `E remove(int index)` - remove element with given index
	 - `E set(int index, E e)` - replace element with given index by e
 - has methods that search for a specified object in the list and return its numerical position, returning -1 if they are not present
	 - `int indexOf(Object o)` - return index of first occurrence of o
	 - `int lastIndexOf(Object o)` - return index of last occurrence of o
 - a method that gets a sub list of the list
	 - `List<E> subList(int fromIndex, int toIndex)`
		 - return a view of a portion of the list, using the position of elements in the list
		 - starting on `fromIndex`, up to *but not including* `toIndex`
 - has methods for returning `ListIterators`, which are iterators that can take advantage of the list's sequential nature
	 - **`ListIterator<>` interface**
		 - `void add(E e)` - insert the specified element into the list
		 - `boolean hasPrevious()` - return true if this list has further elements in the reverse direction
		 - `int nextIndex()` - return the index of the element that would be returned by a call to `next()`
		 - `E previous()` - return the previous element in the list
		 - `int previousIndex()` - return the index of the element that would be returned by a call to `previous()`
	 - `ListIterator<E> listIterator()` - return a `ListIterator` for list positioned at index 0
	 - `ListIterator<E> listIterator(int index)`
		 - return a `ListIterator` or this list positioned at index index

**Implementations**
 - `ArrayList`
	 - arrays cannot be resized once they are created
	 - is literally backed by an array
	 - stores the elements in a contiguous array, with the first element stored at index 0
	 - requires an array at least large enough to contain the elements and a variable to keep track of occupied locations
	 - if the `ArrayList` has grown to the point where its size is equal its capacity, the backing array will be replaced with a larger one capable of holding the old contents with a margin for expansion
	 - set and get operations take constant takes
	 - adding / removing elements at random positions take a lot of time since that requires adjustment of other elements
 - `LinkedList`
	 - the list must iterate internally to reach the required position
	 - positional `add()` and `remove()` have linear time complexity if you have to traverse to a certain index
	 - `iterator.remove()` takes place in constant time since you don't have to rearrange elements afterwards

## `Map`
 - collection that uses key-value associations to store and retrieve elements
 - does not inherit from `Collection` interface
 - methods that are supported by a set of key to value associations in which the keys are unique

**Methods**
 - adding associations
	 - `V put(K key, V value)`
		 - add or replace a KV association, return the old value if the key was present; otherwise returns null
	 - `void putAll(Map<? extends K, ? extends V> m)`
		 - add each of the KV associations in the supplied map into the receiver
 - removing associations
	 - `void clear()` - remove all associations from this map
	 - `V remove(Object key)` - remove the association based on key
		 - return the value which it was associated with or null
 - querying the contents of a map
	 - `V get(Object k)` - return the value corresponding to k or null if k is not present as a key
	 - `boolean containsKey(Object k)` - return true if k is present as a key
	 - `boolean containsValue(Object v)` - return true if v is present as a value
	 - `int size()` - return the number of associations
	 - `boolean isEmpty()` - return true if there are no associations
 - providing collection views of the sets / values or associations
	 - any changes between the returned values and the map are reflected onto each other
	 - `Set<Map.Entry<K, V>> entrySet()`
		 - `Entry` - represents a key-value association
			 - provides a `setValue()` method which can be used to change values in the backing map
		 - return a set view of the associations
	 - `Set<K> keySet` - return a Set view of the keys
		 - removing a key removes the single corresponding Key-value assocation
	 - `Collection<V> values()` - return a Collection view of the values
		 - removing a value removes only one of the associations mapping to it, the value can still be present as part of an association with a different key

**Implementing map**
 - `HashMap`
	 - constant time performance for `put` and `get`
	 - uses rehashing to control the load and minimize the number of collections
 - `LinkedHashMap`
	 - guarantees the order in which the iterators return its element
	 - offers a choice of iteration orders
		 - order in which they were inserted in the map
		 - order in which they were accessed (from least recently to most recently accessed)
			 - implements `removeEldestEntry(Map.Entry eldest)`
				 - oldest entry in the map / least recently accessed
				 - a subclass can implement this method to return true to delete the eldest child whenever `put` or `putAll()` is called
 - `TreeMap`
	 - allows you to supply a Comparator
	 - standard constructor uses the natural ordering of the keys
	 - `get`, `put`, and `remove` perform in O(log n) time

**Storage mediums that are used to implement Collections**
 - Main operations performed on collection interfaces
	 - adding and removal of elements by position
	 - retrieval of elements by content
	 - iteration over collection elements
 - Arrays
	 - implemented directly in hardware
	 - has the features of random access memory
		 - very fast for accessing elements by position and iterating over them
	 - used by `ArrayList` and many `Queue` and `Deque` implementations
 - Linked list
	 - chain of linked cells, where each cell contains a reference to data and a reference to the next cell in the list
	 - perform differently from arrays, accessing elements by position is too slow
	 - insertion and removal operations can be performed in constant time by rearranging the cell references
	 - primary backing structure used for `LinkedList` 
		 - also used secondarily in `HashSet` and `LinkedHashSet`
 - Hash tables
	 - storing elements indexed on their content rather than an integer valued index
	 - provide no support for accessing elements by position, but access by content is very fast, and insertion /removal
	 - Backing structure for many `Set` and `Map` implementations
		 - `LinkedHashSet`, `HashSet`
		 - `LinkedHashMap`, `HashMap`
 - Trees
	 - organize their elements by content, can store and retrieve them in sorting order
	 - relatively fast for inserting and removing, accessing by content and iterating over them
	 - Used by `TreeSet` and `TreeMap`
