Combinational circuit
 - set of gates whose output at any time is a function only of the input at that time
 - the appearance of the input is followed by the input of the output
 - is represented using a truth table / graphical symbols and boolean operations
 - any boolean function can be implemented as a network of gates
 - can also be represented using a sum of product
	 - each term is represented using an AND gate where the input is inverted if the term digit is inverted
	 - then all the terms are combined using an OR gate
 - can also be represented using product of sum
 - It is often possible to drive a simpler boolean expression from the truth table than either SOP or POS
 - It may be preferable to implement the function with a single gate type using either NAND or NOR

Karnaugh Maps
 - convenient way of representing a Boolean function of a smaller number of variables

Readonly memory
 - combinatorial circuits are memoryless because their output depends only on their current input and no history
 - ROM is implemented using combinatorial circuits
	 - performs only the read operation, a given input to the ROM address lines always produces the same output
	 - the outputs of the rom is determined only by the current inputs - hence it is a combinatorial circuit
	 - can be implemented with a decoder and a set of OR gates
	 - the decoder selects which bank of memory to activate, the OR gates combined all banks together

Adder
 - if carry values can be determined without having to ripple through all stages, each adder can function independently, is referred to as carry look ahead
 - each carry term can be expressed in SOP as a function of the original inputs, only two levels of gate delay occur
	 - evaluating this function can be complicated, full carry lookahead is only done 4-8 bits at a time
	 - carry look ahead adders can be chained together to form a partial ripple carry and CLA adder

# Sequential circuits
 - the current output of a sequential circuit depends also on the past history of inputs
 - depends on the current input and the current state

## Flip flops
 - a bi stable device that exists in one of two states
	 - In the absence of input, it remains in that state (functions as 1 bit memory)
 - has two outputs, which are always complements of each other
 - Flipflops can be clocked so their changes are synced to an external clock
 - **SR Flip Flop** - Set and reset
	 - Q is high when set is called
	 - Q is low when reset is called
	 - Not all combinations of input are valid because when S and R are both high, it triggers a race condition
 - **D Flip Flop** 
	 - Q is high when the input is 1 when the flip flop is clocked
	 - Q is low when the input is 0 when the flip flop is clocked
	 - Sometimes referred to as the data flip flop as its a storage of 1 bit of data
		 - The output is always equal to the most recent captured input
		 - It remembers and produces the last input
 - **JK Flip Flop**
	 - Like an SR flip flop but the output inverts when both inputs are applied
	 - Prevents a race condition
## Registers
 - an example of the use of flip flops
 - used within the CPU to store one or more bits of data
 - parallel registers - can be read or written simultaneously
	 - load - control signal that controls writing into the register
 - shift register - accepts or transmits information serially
	 - Loads data at one at a time
 - counter - register whose value is easily incremented by 1
	 - ripple counter - the change that occurs to increment the counter starts at one end and ripples through the other end
		 - The output is tied to the clock of the next input
	 - Sync counter
		 - All flip flops are clocked at once
		 - The input of JK in Bit K is straight from the output of Bit K-1

## Programmable logic devices
 - PLA - a boolean function can be expressed in a sum of products form
	 - consists of a regular arrangement of NOT / AND / OR gates on a chip
	 - Each chip input is passed through a not gate so that each input and its complement are available to each and gate
		 - Arbitrary SOP connections are possible
	 - A general term that refers to any type of IC that is used to implement digital hardware
	 - Is made by having a fuse between every connection that is blown or by having an inter connection mask
	 - the structure of the programmable logic plane grows too quickly in size as the number of inputs is increased
 - FPGA - consists of an array of uncommitted circuit elements called logic blocks
	 - Logic block - configurable logic block where the computation takes place
		 - can either be a combinatorial or sequential circut
		 - programming is done by downloading the contents of a truth table for a logic function
	 - IO block - IO blocks connect IO pints to the circuitry on the chip
	 - Interconnect - signal paths available for establish connections among IO blocks and logic blocks
