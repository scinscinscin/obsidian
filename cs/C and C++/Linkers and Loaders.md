[]() - binds more abstract names to concreate names
 - allows programmers to write code using the abstract names
	 - converts `getLine()` into `location 612` bytes from the beginning of executable code module `iosys`
 - names were bound to addresses too early
	 - assemblers allowed programmers to write programs in terms of symbolic names, with assemblers binding names to machine addresses
	 - if program changed, the programmer had to reassemble it, but the work of assigning addresses is pushed into the computer
 - computer installations keep a library of prewritten programs that programmers can draw to use in their own programs
	 - relocation and library search
 - relocating loader allows authors to write each subprogram as if they were location zero and defer address binding until the subprograms were linked with a particular main program
	 - before, each program could be assembled and linked knowing that the entire address space is available, but now programs had to share memory
	 - the actual addresses at which the program would be running weren't known until the operating system loaded the program into memory, deferring final address binding past link time to load time
	 - most systems provide a shared library for programs to use
		 - all programs that share a library can share a single copy of it, improving performance and disk space
	 - static shared libraries
		 - bound to specific addresses at the time the library is built - the linker binds program references to library routines to those addresses at link time
		 - inflexible, programs have to be relinked every time any part of the library changes
	 - dynamic link libraries
		 - sections and symbols aren't bound to actual addresses until the program that uses the library starts running

 - linkers assign relative addresses within each program, and loaders do a final relocation step to assign actual addresses
 - linkers do more and more complex name management and address binding
	 - linker lays out storage and assign the addresses both for the subprogram and common blocks
	 - linkers provide overlays, a technique that let programmers rearrange different parts of a program to share the same memory, with each overlay loaded on demand when another part of the program called into it
 - compilers and assemblers were modified to create object code in multiple sections
	 - operating system can use a single copy of unchanging parts of the program
	 - one section for readonly code and another section for writable data
	 - linker had to be able to combine all sections of each type so that the liked program would have all the code in one place and all of the data in another
**program loading**
 - copy a program from storage, into main memory so it is ready to run
 - can involve arranging virtual memory to map virtual addresses to disk pages

**relocation**
 - compilers and assemblers create each file of object code with the program address at 0
 - relocation happens more than once, linker creates a program from multiple subprograms that start at zero
	 - the subprograms are relocated to locations within the big program
	 - when this is loaded, the system picks the actual address and the linked program is relocated as a whole to the load address
 - symbol resolution
	 - references from one subprogram to another are made using symbols
	 - linker resolves symbols by noting the location assigned and patches the caller's object code so the call instruction refers to that location

# Linker
 - scan the input files and to find the sizes of segments
 - collect definitions and references of all symbols
 - create a segment table listing all segments defined in the input file and a symbol table with all of the symbols imported or exported
 - assign numeric locations to symbols
 - read and relocate object code, substituting numeric addresses for symbol references, adjusting memory addresses in code to reflect relocated segment addresses, write the relocated code to the output file
 - Symbol table contains the info that the runtime linker will need to resolve dynamic symbols, the linker itself will generate small amounts of code in the output file used to call routines or dynamically linked libraries, or an array of pointers to init routings that need to be called at startup time
	 - symbol table is also used for relinking or debugging that isn't used by the program
 - object files feed into the linker, with libraries that contain lots of files following along
 - identifies shared libraries that resolve the undefined name in a linker run, but it notes in the output file the names of the libraries in which the symbols were found so the shared library can be loaded in when the program is run
 - compiler and assembler generates code using unrelocated addresses of code and data defined within the file, 