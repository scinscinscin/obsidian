`Comparable<T>`
 - contains a `int compareTo(T o)` method that can be used to compare one object to another
	 - returns a positive number if `this` is higher than `o`
	 - `x.equals(y)` if and only if `x.compareTo(y) == 0`
	 - important when you use `SortedSet` and `SortedMap` since they compare using the natural ordering
 - ordering specified by a class that implements `Comparable` is called the natural ordering of the class
 - an object belonging to a class can only be compared with an object belonging to the same class

`Comparator<T>`
 - allows to compare objects that do not implement the Comparable interface
 - compare objects using a different ordering from the one specified by the interface
 - methods
	 - `int compare(T o1, T o2)`
		 - returns positive if `o1 > o2`
	 - `boolean equals(Object obj)`
	```java
	// comparator that considers the shorter of two strings to be smaller
	Comparator<String> sizeOrder = new Comparator<String>(){
		public int compare(String s2, String s2){
			return s1.length() < s2.length() ? -1 :
				s1.length() > s2.length() ? 1 : s1.compareTo(s2);
		}
	}
	```
- for any method with a type variable of `Comparable`, there is another generic method with an additional type argument for `Comparator`

# Enums

 - each enumerated type declaration can be expanded into a corresponding class, and this class is a subtype of `java.lang.Enum
	 - it has exactly one instance for each of the enumerated constant, bound to a suitable static final variable
	```java
	enum Season { WINTER, SPRING, SUMMER, FALL }
	// expands to a class called Season with four instances of the class
	// bound to static final variables with the name WINTER, SPRING, SUMMER, and FALL
	class Season extends Enum<Season>{
		private Season(String name, int ordinal){ super(name, ordinal); }
		// one class for each of the seasons
	}

	public abstract class Enum<E extends Enum<T>> implements Comparable<T>{
		// you can compare two values of the type seasonw ith each other
		public final int compareTo(E o){ return ordinal - o.ordinal; }
	}
	```