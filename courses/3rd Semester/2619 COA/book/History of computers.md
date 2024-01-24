## Vacuum tubes
 - IAS computer
	 - stored-program approach - attributed to John von Neumann
		 - Alan Turing developed the idea at the same time
		 - first publication of the idea was in a 1945 proposal for a new computer called EDVAC
	 - in 1946 - began the design of a new stored program computer called IAS
	 - not completed until 1952
	 - structure
		 - main memory which stores both data and instructions
		 - ALU capable of operating on binary data
			 - memory buffer register - word to be stored in memory / sent to the IO unit / used to receive a word from memory or from IO
			 - memory address register - specifies the address in memory of the word to be written / read into the MBR
			 - instruction register - 8-bit opcode being executed
			 - instruction buffer register - hold temporarily the right hand instruction from a word in memory
			 - program counter - address of the next instruction pair to be fetched from memory
			 - accumulator - temporarily operands and results of ALU operations
		 - control unit - interprets the instructions in memory and causes them to be executed
		 - input output equipment controlled by the control unit
	 - performs elementary operations of arithmetic most frequently
		 - should have dedicated addition, subtraction, multiplication and division operations
			 - the specific way this is realized requires close scrutiny, a central arithmetical part of this device will have to exist (called the arithmetic control unit)
		 - the logical control of this device can be efficiently carried out with a central control organ called the program control unit
			 - a distinction must be made between specific instructions if it has to be an all purpose computer, between defining a particular problem
		 - any device that is to carry long sequence of operations should have considerable memory
			 - total memory constitutes the third part of the device
		 - arithmetic logic unit & program control unit & memory correspond to the associative neurons in the human nervous system
			 - the device must have the ability to maintain input and output contact with some specific medium of this type
	 - has 21 instructions
		 - data transfer - move data between memory and alu / between alu registers
		 - unconditional branch - sequence of instruction execution can be changed
		 - conditional branch - branching can be dependent on a condition, allowing decision points
		 - arithmetic - operations performed by the ALU
		 - address modify - addresses can be computed by the ALU and inserted into instructions stored in memory

## instruction cycle
 - fetch cycle - the opcode of the next instruction is loaded into the instruction register
	 - the address portion is stored into the memory address register
	 - instruction may be taken from the instruction buffer register or it can be obtained from memory by loading it into the memory buffer register
 - execute cycle - control circuity interprets the opcode and executes the instruction by sending out the appropriate control signals to cause data to be moved or an operation to be performed by the ALU

transistor - smaller cheaper and generates less heat than a vacuum tube
 - is a solid state device made from silicon
 - invented at bell labs in 1947 but first transistorized computer came out in 1950s
 - defines the second generation of computers
	 - each new generation is characterized by greater processing performance, larger memory capacity and smaller size than the previous one
	 - 2nd generation saw the introduction of more complex arithmetic and logic units and control units
 - important member includes the IBM 7094
	 - relative speed of the cpu increased by a factor of 50 through improved electronics
	 - control unit fetches two adjacent words form memory for an instruction fetch
		 - control unit has to access memory for an instruction on only half the instruction cycles
		 - data channel - an io module with its own processor and instruction set
			 - cpu does not execute detailed io instructions, stored in main memory to be executed by a special purpose processor in the data channel itself
				 - send a control signal to the data channel, instructing it to execute a sequence of instructions in memory
			 - performs the task independently and signals the CPU when the operation is complete, relieving the CPU of processing burden
		 - multiplexor - central termination point for data channels, the CPU and memory
			 - schedules access between these devices, allowing them to act independently

## Integrated circuits
 - gate - is a device that implements a simple boolean function
	 - is called gates because they control the flow of data
 - memory cell - is a device that stores 1 bit of data
	 - can be in two stable states at any time
 - by connecting gates and memory cells together, we can form computers

Benefits of having a family of computers
 - similar or identical instruction set
 - similar or identical operating system
 - increasing speed
	 - gained by the use of more complicated circuitry in the ALU, allowing suboperations to be carried out in parallel
	 - increase the width of the data path between main memory and the ALU
 - increasing number of io ports
 - increasing memory size
 - increasing cost

PDP-8
 - was cheaper than the System/360
 - could be integrated and resold by another manufacturer, referred to as OEMs
 - used the bus structure to carry control, address, and data signals
	 - the use of the bus, called the Omnibus, ould be controlled by the CPU
	 - highly flexible, allowing modules to be plugged into the bus to create various configurations

Intel 4004
 - first chip to contain all of the components of the CPU in a single chip
 - referred to as a microprocessor
 - can add two 4-bit numbers and multiply only by repeated addition
 - we measure the number of bits that the processor can work on using the width of the bus
	 - or also the number of bits in the accumulator / general purpose registers
 - evolved using the Intel 8008, which processed 8-bit numbers

Intel 8080
 - first general purpose microprocessor, the CPU of a general purpose microcomputer
 - faster, has a richer instruction set and has a large addressing capability
 - 16-bit microprocessors started to be created around the same time
	 - at the end of 1970s, a general purpose microprocessor appeared, the 8086
	 - in 1981, a 32-bit microprocessor appeared
		 - 1985, the 80386 was introduced

CISC vs RISC
 - decades of design effort on complex instruction set computers
	 - intel has ranked as the number one maker
 - compared to reduced instruction set computers
	 - used by arm in a wide variety of embedded systems
		 - most powerful and best designed RISC based systems on the market

Embedded systems
 - use of electronics and software within a product
 - embedded within larger devices as compared to a general purpose computer
 - often tightly coupled within their environment
	 - has real time constraints imposed by the need to interact with the environment

Microprocessor
 - registers / alu / some control unit
Microcontroller
 - a single chip that contains the processor / program / ram and a control unit
 - also referred to as a computer on a chip
 - range in physical sizes and processing power
 - does not provide human interaction most of the time