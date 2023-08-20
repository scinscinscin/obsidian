- combinatorial and sequential circuits can be used to create simple digital systems
	- characterized in terms of the registers they contain and the operations that they perform

**Microoperations**
 - perform operations on data stored in one or more registers
 - transfer data between registers and external buses of the cpu
 - also perform arithmetic and logical operations on registers
 - functions built into registers are example of microoperations
	 - shift / load / clear / increment
 - types
	 - register transfer - data moves from register to register
	 - arithmetic - perform arithmetic on data in registers
	 - logic - perform bit manipulation on data in registers
		 - change bit values / delete a group of bits / insert new bit values into a register
		 - applications
			 - selective set - sets 1 to certain bits in a register / done using OR
			 - selective complement - negates bits in register A when there is a corresponding 1 in register B - done using `A <- A XOR B`
			 - selective clear - clears to 0 the bits in register A when there is a corresponding 1 in register b
				 - `A <- A ^ B'`
					 - negate B, turning all its 1s into 0, then AND it with A to mask
			 - mask - clears to 0 the bits in register A when there is a corresponding 0 in register B
			 - insert - insert a new value into a set of bits in register A
	 - shift - perform shift on data in registers
		 - used for serial transfer of data and is used in conjunction with arithmetic and logic operations
		 - contents can be shifted either left or right
		 - circular shift - circulates the bits of the registers around two ends with no loss of information, is either `cir` or `cil`
		 - logical shift - transfers 0 through serial input, with all bits involved in the shifting
			 - in the logical shift right, (`shr`) the most significant bit is 0
			 - in logical left shift (`shl`), the least significant bit is 0
		 - arithmetic shift - multiplies or divides a signed number by two
			 - shifting right preserves the sign bit (most significant bit) of the register
			 - shifting left may cause in a different sign than from the original
				 - remember that negative numbers are stored as 2's compliment
				 - -1 is 0b1111, left shifting gives 0b1110, which is -2 

**Hardware organization**
 - set of registers it contains and their function
 - source of microoperations performed on the binary information stored in the registers
 - control signals that indicate the sequence of operations

RTL - a symbolic language that is used to describe the sequence of microoperations
 - registers are denoted by capital letters
 - registers and their contents can be viewed and represented in different ways
	 - a single entity
	 - the bits they contain `R2(0-7)`
		 - can also specify a single bit `R2(5)`
 - transfer of information `R2 <- R1`
	 - contents of register R1 are copied into register R2
		 - implies the existence of circuitry to transfer between R2 and R1
	 - simultaneous transfer of all bits during one clock pulse
	 - non destructive, does not remove the information from R1
	 - register transfer
 - comma `R2 <- R1, R1 <- R1`
	 - if two or more operations occur simultaneously, they are separated with commas
	 - simultaneous transfer
 - conditional transfer
	 - `a: X <- Y, Y <-Z`
	 - only do the simultaneous transfer when a is high
 - can also load constant values to registers using 0 and 1
 - bit and bit range transfers
	 - `a: X(3-1) <- Y(2-0)`
		 - transfer first 3 bits of Y to positions 1-3 of register X

Connecting registers
 - transferring information between registers through a common bus
 - control signals determine which register is needed
 - using a multiplexer
	 - select line of the MUX indicates which registers will have the contents transferred to the bus
	 - a bus systems will multiplex k registers of n bits to produce a n-line bus
	 - require nkx1 multiplexers
	 - the bus is connected to the input of all destination registers and will activate the load control of the selected register when it is ready to transfer data
 - using three state bus transfers
	 - the 0th bit of all registers are AND'd to the bus bit 0
	 - only one 0th bit from the registers are selected at a single time using a decoder that selects which register is connected "directly" to the bus
		 - when a register is not connected to a bus, it acts in a high impedance state that behaves like an open circuit
		 - when a register is connected directly to a bus, the bit of the register corresponds to the bit of the bus,

memory transfer
 - collectively, the memory is viewed at the register level as a device M
 - is accessed by putting the address in the MAR
 - when memory is accessed, the contents of MAR is sent to the memory unit's address lines
	 - `[DESTINATION REGISTER] <- M[AR]`
		 - copy data from memory's address to the data register
		 - can also be done the other way around