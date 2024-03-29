 - provides functional requirements for the processor
 - implementing the processor is a task that involves implementing the machine's instruction set
 - defines the operation of the processor
	 - is referred to as machine instructions
 - **instruction set** - the collection of different instructions that the processor can execute
 - Elements
	 - **Operation code** - the operation to be performed, is called opcode
	 - **Source operand reference** and **Result operand reference**
		 - Main or virtual memory
		 - Processor register
	 - **Next instruction reference** - where to fetch the next instruction after the execution of this instruction is complete
		 - can either be a real address of virtual address
 - instruction representation
	 - Each instruction is represented by a sequence of bits, divided into fields corresponding to constituent elements of the instruction
	 - Opcodes are represented using abbreviations that indicate the operation
 - Instruction types
	 - Data processing - arithmetic and logic instructions
	 - Data storage - Movement of data into or out of register and or memory locations
	 - Data movement - IO instructions
	 - Control - test and branch instructions
		 - skip / procedure call
		 - jump instruction has one of its operands the address of the next instruction to be executed
			 - conditional branch instruction - the branch is made only if a certain condition is met
				 - else the next instruction in sequence is executed
			 - unconditional branch - the branch is always taken
			 - generating the condition - most machines provide a 1-bit condition code that is set as the result of some operations (**flag register**)
				 - also called status flags
				 - C - Carry
				 - P - parity
				 - A - auxilliary carry - used for bcd
				 - zero - the result of everything is zero
				 - sign - the sign of the result of a logic operation
				 - o - arithmetic overflow after an addition / two's complement
				 - 
		 - skip instruction includes an implied address. Implies that one instruction can be skipped
			 - does not require a destination address fields
			 - typical example is increment and skip if zero
		 - procedure - a self container computer program that is incorporated into a larger program
			 - can be invoked where the processor is to go and execute the entire procedure and return to the point from which the call took place
			 - a call instruction and a return instruction which are both branch instructions
			 - When the processor executes a call, it places the return address on the stack, when it executes a return, it uses the address on the stack. **When a processor executes a call, it stacks the return address and also the parameters to be passed into the called procedure, the proc can access the parameters by popping from the stack.  When returning, the return parameters are also passed through the stack**
		 - Memory management - can only be executed by the  operating system
			 - allow descriptor tables to be loaded and read

**What is the maximum number of addresses one might need in an instruction?**
 - arithmetic and logic instructions require most operands
	 - they are either unary or binary requiring atleast 2 operands
	 - they must have a destination operand

## Instruction set design
 - affects many aspects of the computer system
 - Operations - how many operations, which should be provided / how complex should those operations be
 - Data types - various types of data which operations should be performed
	 - Addresses
	 - Numbers
		 - Binary integer / binary fixed point
		 - Binary floating point
		 - Decimal
	 - Characters
		 - Number of codes have been devised which characters are represented using a sequence of bits
		 - ASCII and EBCDIC
	 - Logical Data
		 - store an array of boolean or binary data items, in which each item can take only 2 values
			 - most efficiently stored using bitfields
 - Instruction format - size / number of addresses and size of various fields
 - Registers
 - Addressing