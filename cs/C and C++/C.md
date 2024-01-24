 - highly flexible and adaptable language
 - used for programming micro-controllers, operating systems, etc
 - most widely used languages in the world and is stable
	 - c++ adds a number of new features
		 - class facilitate code reuse through object oriented design
 - c is designed for writing operating systems
 - simple and flexible
 - used for many different types of programs
 - a portable c compiler is widely available, people can attach a c compiler with little expense
 - is a bridge between the programmer and the raw computer
	 - handles details of imposing the organization of data into the computer's memory
	 - has more complex data types
	 - programmer can arrange it in their on needs, and the compiler translates it into something the computer can understand
 - provides programs with a rich set of standard functions that perform common functions such as searching / sorting / input and outputs
 - can organize into reusable components to allow for programs to be written faster
 - is a standardized language that has different versions throughout history
	 - ANSI C - C89
		 - is also called C90
	 - C99 , C11 C17
		 - c11 is often called modern C

# Main function
 - the starting point of the executable file
 - `int main(){}`

# File input and output
 - file descriptors - small non negative integers that the kernel uses to identify files accessed by a process
	 - is returned by the kernel when we use a file
	 - read more on [[Unix]]
 - stdin / stdout / stderror
	 - all shells open a three descriptors when a new program is run
	 - all three are typically connected to the terminal
	 - can be directed to a file
 - open a file for reading using the `fopen` function
	 - `FILE *fp = fopen("myfile.txt", "r");`
	 - opens a file for reading, returning a pointer to a file stream represented by `FILE *`
	 - returns null if it opening the file failed
 - read a line of text from a file using `fgets` function
	 ```c
	 // str is char[100]
	 while(fgets(str, 100, fp) != NULL) ;
	```
 - close the file using the `fclose` function when we're done
	 - `fclose(fp);`
 - print to a file with formatting
	 - `fprintf(fp, "%s\n%s", "parameter 1", "parameter2");`

## Buffering
 - use the minimum number of read or write calls
 - try to do buffering automatically for each IO stream
 - fully buffered
	 - actual IO takes place ONLY when the standard IO buffer is filled
	 - files residing on disk are fully buffered by the standard IO library
	 - flush - writing a standard IO buffer
		 - can be done automatically when a buffer files
		 - can also call `fflush()` to flush a stream
		 - `tcflush()` - discard the contents of a buffer
	 - standard error is never fully buffered (always unbuffered)
	 - stdin and stdout are fully buffered iff they do not refer to an interactive device
		 - they are usually line buffered if they refer to a terminal device
 - line buffered
	 - perform IO when a newline character is encountered on input or output
	 - output a single character at a time knowing that actual IO will only take place when we are done writing each line
	 - used on a stream that refers to a terminal
	 - size of buffer uses to collect each line is fixed
		 - some io will take place if we fill this buffer before writing a newline
		 - whenever input is requested through an unbuffered stream or a line buffered stream, all line buffered output streams are flushed
 - unbuffered - standard io library does not buffer the characters

# Manipulating memory
 - memory obtained through malloc is not initialized
 - allocated memory has no meaningful values and trying to read it results in undefined behavior (calloc can be used to set it to 0)
 - `memset(void *destination, int value, size_t N)`
	 - dest - pointer to allocated memory
	 - value - what to fill the associated bytes
	 - the number of bytes of the allocated space
 - `memcpy(void *dest, const void *src, size_t N)`
	 - copies the number of bytes between src and dest pointer
 - `memcmp(const void *p1, const void *p2, size_t N)`
	 - compares the first N bytes from memory block pointed by p1 to the first N bytes pointed to by p2, returning 0 if they match
 - `memchr(const void *p, int c, size_t N)`
	 - find integer c between p and p+n, return the byte where it is located
	 - returns null if it was not able to find that byte

`_static_assert(expression, message)`
 - evaluates an expression during compile time, if it is 0, a message is displayed
`_Noreturn`
 - specifies that a function does not return either through the use of a return statement or by hitting the end of the function block
 - code following a call to a `_Noreturn` function is unreachable
`_Generic`
 - way to select one of several expressions during compile time based on a type of a given controlling expression
 - preprocessor switch case for selecting what to output based on type
`_Alignof`
 - returns the alignment requirements of the type, the property of an object that says how many bytes there are before these two addresses in order to store the objects successfully

# Threads
 - process has only one thread of control
	 - one set of machine instructions executing at a time
	 - multiple threads can exploit the parallelism possible on multiprocessor systems
	 - all threads within a process share the same address space, file descriptors, stacks and processor-related attributes
	 - are identified by ids, these are local to the process
 - create and join threads / creating mutexes, sync access and work with conditional variables
 - has to be compiled with the `-pthread` flag
```c
// is called by the thread system and the varargs are passed into the function as void *, must be casted before it can be used
int dowork(void *arg){
	// get the current thread id
	thrd_t mythreadid = thrd_current();
	for (int i = 0; i < 5; i++){
		printf("Thread id: %lu, counter: %d, code: %s\n", mythreadid, i, (char *)arg);
	}
	
	return 0;
}

int main(void){
	thrd_t mythread;
	
	// create a thread that executes a doWork with the following argument, and assign the thread into mythread
	if (thrd_success != thrd_create(&mythread, dowork, "Hello from a thread!")){
		printf("Could not create a thread.\n");
		return 1;
	}
	
	// join a thread to the main thread
	thrd_join(mythread, NULL);
}
```

# Network programming in C
 - `struct addrinfo`
	 - prepares the socket address structures for subsequent use
	 - host name lookups / service name lookups
	 - load the struct and call `getaddrinfo()`\ which returns a new linked list
	 - can be forced to use ipv4 or ipv6 using the `ai_family` field
	 - `ai_next` points to the next element
	 - `ai_addr` is a pointer to `struct sockaddr`
		 - holds socket information for many different types of sockets
		 - `sa_family` - is an enum that can be a variety of things
		 - `sa_data` - contains the destination address and the port number for the socket, is `char[14]`
			 - can be packed using `struct sockaddr_in`
				 - `short int sin_family` - corresponds to `sa_family`
				 - `unsigned short int sin_port` - is the port
				 - `uint32_t sin_addr` - 4 bytes (1 byte for each) part of the ip address
				 - don't have to manually pack info into a long
				 ```c
				 struct sockaddr_in sa;
				 // returns -1 on error and 0 if the address is wrong
				 inet_pton(AF_INET, "192.168.1.1", &(sa.sin_addr))
				 inet_ntop(AF_INET, &(sa.sin_addir), reference_to_string, INET_ADDRSTRLEN);
				```
 - `getaddrinfo()` - setup structs that you need later on
	 - `int getaddrinfo(const char *hostname, const char *port, const struct addrinfo *hints, struct addrinfo **res)`
	 - node - the host name to connect to or an ip address
	 - service - can be a port number or a name of a particular service in the /etc/services file
	 - hints - a reference to `struct addrinfo` that you have filled out with the relevant information
	 - ret - returned `struct addrinfo` in a linked list
		 - each node in the list contains a `struct sockaddr` which can be used later
 - `sockfd socket(int domain, int type, int protocol)`
	 - domain - `PF_INET` or `PF_INET6`
	 - type - `SOCK_STREAM` or `SOCK_DGRAM`
	 - protocol - can be set to 0 to choose the proper protocol for the given type
		 - can call `getprotobyname()` to look up the protocol that you want
	 - `s = socket(res->ai_family, res->ai_socktype, res->ap_protocol);`