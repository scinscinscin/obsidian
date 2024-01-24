# Signals
 - are used to notify a process that some condition has occurred
 - is an interrupt but wrapped for C
 - we can provide a function that is called when the signal occurs using the `signal` function

# Syscalls
 - service points through which programs request services from the kernel
 - unix provides a well defined limited number of entry points into the kernel called system calls
 - the system call interface is documented in the unix programmer's manual
	 - its definition is in the c language is used on any given system to invoke a system call
	 - each system call has a function of the same name in the C standard library
	 - user calls this function, using the c calling sequence
		 - function invokes the appropriate kernel service using whatever technique ie: (the function may put one or more of the arguments into general registers then execute some machine instruction)
 - the difference between a syscall and a library function is fundamental, but the difference is not critical since they both appear as normal C functions
 - malloc() implements one type of allocation
	 - if we don't like it, we can implement our own malloc using sbrk
	 - sbrk is a syscall inside the kernel
 - syscalls provide a more minimal interface, where library functions provide more elaborate functionality


# POSIX
 - promotes the portability of applications among various unix system environments
 - defines the services that an operating system must provide if it is posix compliant
 - based on the Unix operating system but is not restricted to unix
 - specifies an interface only, no distinction is made between system calls and library functions, hence all routines are called functions
 - is extended by the single unix specification
	 - adds additional interfaces that extend the functionality
 - defines optional interfaces and those which must be supported for an implementation to be XSI conforming (UNIX systems)

# File descriptors
 - all opened files are referred to by file descriptors
 - a non negative integer that is returned by the kernel to the process
 - we identify a file with the file descriptor that was returned by `open` or `creat` as an argument to either `read` or `write` 
	 - 0 - standard input
	 - 1 - standard output
	 - 2 - standard error

**open()**
 - a file is opened or created by either calling these functions
