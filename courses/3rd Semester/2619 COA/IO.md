- depends on the size of the computer and the peripherals connected to it
- efficient mode of comm between CPU and outside env
- CPU reads digital data while IO generates analog data

**IO interface**
 - parts
	 - io registers
	 - status registers
	 - decoder circuitry
 - function
	 - control and timing - coordinates flow of traffic between internal resources and external devices
	 - processor communication
		 - command decoding / data status reporting / address recognition
	 - data buffering
		 - balances devices and memory speeds
	 - devices communications
		 - commands / status information and data
 - solves
	- data transfer rates of IO are slower than the transfer rate of the CPU
		- we should be able to sync them
	- data codes and formats in peripherals differ from word format in the CPU
	- operating modes of peripherals are different from each other and must be controlled as to not disturb the operation of other peripherals connected to the CPU

Processor can access Io using either
 - shared io
	 - io devices are assigned addresses, isolated from memory address space
	 - input and output registers are required
	 - a separate control line has to be used
	 - has an address decoder circuitry for device identification
	 - status register for each input and output device
		 - indicates the status if the io device is ready to accept or send data
		 - adopted by intel
	 - advantages & disadvantages
		 - separation between memory address space and that of io deviecs
		 - disadvantage: needs to have special io instructions in the instruction set
	 - when reading
		 - send device number to decoder circuit
		 - buffers holding data will be enabled by the output of the decoder
		 - instruction encoding will gate the data available on the database into the specific cpu register (usually accumulator)
	 - output operation
		 - specific cpu register in the specified output device
		 - io operation performed this way are called **programmed io**
			 - performed under the control of the CPU
			 - complete instruction cycle is needed for every input and output operation
			 - useful where one character is to be processed
				 - keyword and character mode printers
 - memory mapped io
	 - io registers are treated as if they are memory locations
	 - used by motorola
	 - need to reserve a certain part of memory address space for addressing io devices