- lightweight subprocess
- smallest independent unit of a program
- contains a separate path of execution
- every program contains at least one thread
- a thread is created & controlled by the `java.lang.Thread` class
- multithreaded programming
	- multiple threads are from one Runnable instance
	- threads share the same data and code
- lifecycle
	- new
		- going to initiate a new Thread
	- runnable
		- once the thread is started
		- can be in a waiting state
			- inactivity - waiting for some other thread to give back some data
	- running
		- it is executing a run method and the yield() method that can send them to go back to the runnable state
	- terminated
		- when the thread has completed the task

- extends from Thread
	- override run method
	- create object of class
	- invoke start method
- implement Runnable interface
	- override run method
	- create object of class
	- invoke start method

```java
public class ThreadTester{
	public static void main(String args[]){
		HelloRunner r = new HelloRunner();
		Thread t = new Thread(r);
		// starts the thread by calling the start method
		r.start();
	
		// can call r.join() to join r's thread with the main thread
	}
}

// Implementing runnable allows for better object-oriented design
// Single inheritance and consistency
// But extending Thread class allows for simpler code
class HelloRunner implements Runnable{
	int i;
	public void run(){
		i = 0; 
		while(true){
			if(i == 50) break;
			else System.out.println("Hello " + i++);
		}
		
		// can call Thread.sleep() to put the thread on hold
		// allows a thread to pass time without doing anything
		// does not consume CPU cycles while sleeping
		// Can be used for pacing
		// allows other threads to execute

		// Thread.yield() - used by thread currently running to allow another thrad to run
		// prevents a thread from hogging the CPU
	}
}
```

Race conditions
 - two or more threads try to update the same object
 - execution of two threads on the same object overlap
 - must ensure that the entire region executes as a whole or it waits
	 - refers to as being **atomic**
		 - it cannot be interrupted during its execution
 - Every object has one lock
	 - a thread that wants to execute an object's sync code must first attempt to acquire the lock on the object
		 - if it is available, the thread acquires and executes the sync code
		 - if not, the thread is blocked until the lock is released by the thread that is holding it
	 - lock is released automatically upon return of the method or the method throws an Exception
	 - `synchronized` keyword
		 - can be used as a modifier of the method that must be atomic
		 - can be used to create a block of code that has a lock on the data you want to acquire
		 ```java
		synchronized(anObject){
			// statements that use anObject, will have an exclusive lock on that
		}	 
		```
 - a deadlock can occur when two threads are waiting for a lock from the other
	 - deciding on the order to obtain locks
	 - adhering to this order throughout
	 - releasing locks in the reverse order

# The Thread Class
```java
class OurClass extends Thread{
	// is the method that the newly created thread will execute, should override this method with the code that they want the new thread to run
	public void run(){
		// some expensive computation here
	}
}

class OurApplet extends Applet{
	public void init(){
		OurClass oc = new OurClass();
		oc.start();
		// the implmenetation of the start method is part of the Thread class, that indirectly calls the run method in another thread
		
	}
}
```
## Stopping a thread
 - when the `stop()` method is called, the run method needs to return to signify it has completed its execution
	 - threads should terminate by returning from their run method, it is up to a developer to decide how a thread should do this.

# Runnable interface
 - due to java being a single inheritance language, the Runnable interface can be implemented to allow classes to be run in separate threads without the use of inheritance
 ```java
 public class OurClass implements Runnable{
	 public void run(){
		 // some expensive code here
	 }
 }
// this class can then be run using
Runnable ot = new OurClass();

// a thread class is still needed, but OurClass is no longer a thread object
Thread th = new Thread(ot); // <-- A runnable target is passed into it
th.start(); // <- the start() method is called to begin execution
```

**Thread life cycle**
 - there is a period of time after you call `start()` before the virtual machine can start the thread
 - there is a period of time after you return from `run()` before the virtual machine can clean up after the thread
 - there is an even greater period of time after you call `stop()` before the virtual machine can clean up the thread
 
 **methods used for querying and controlling the thread life cycle**
 - `isAlive()` method - returns if the start method has been called / if the thread has been terminated
	 - a thread is alive from sometime before a thread is actually started to sometime after a thread is stopped
	 - the interval is longer than the time that `start()` and `stop()` are called
	 - more useful to check if the thread has stopped running
 - `join()` method
	 - joins the method that was forked off from us earlier when we started the thread
	 - waits for the completion of the thread - `join()` returns as soon as the thread is considered not alive
	 - can also include a `timeout` in milliseconds
 - `setName()` and `getName()` - attach a name to the thread object and fetch it
	 - used by the `toString()` method when the Exception is called
 - `static currentThread()`
	 -  returns a Thread object that represents the current thread
 - `static int enumerate(Thread threadArray[])`
	 - gets all thread objects of the program and stores the result into the thread array
	 - the value returned is the number of thread objects stored into the array
	 - stores thread references into the array and the number of thread objects stored
	 - can get the size using the next method
 - `static int activeCount()` - number of threads of the program

## Sync techniques
 - **atomic**
	 - smallest possible unit of code that cannot be interrupted or be in an intermediate state
		 - can be dealt with using the `synchronized` keyword
			 - allows a programmer access to a resource that is similar to a mutex
			 - when used as a modifier, it prevents the method from being called two times at once
 - mutex lock - mutually exclusive lock
	 - only possible for one thread to get a mutex lock at a time
	 - if two threads try to grab a lock, only one succeeds, the other thread has to wait until the first thread releases the lock
 - race condition
	 - when the order of execution of two or more threads may affect some variable or outcome in the program
	 - simple changes in the algorithm can cause race conditions to manifest in different ways (and change in JVM implementation)