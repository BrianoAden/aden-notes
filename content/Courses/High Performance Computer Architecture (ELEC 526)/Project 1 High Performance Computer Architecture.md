2025-09-03 15:13

Status:

Tags: [[High Performance Computer Architecture]] [[Assignments]]

This is a 3-part project focused on implementing and analyzing a 5-stage processor for a small subset of the DLX instruction set. 

The processor follows the description found in the lectures. See [[High Performance Computer Architecture Lecture 3]]

## Processor Instruction Set

The processor only supports a few instructions:
1. The processor supports two ALU instructions
	1. **ADD** and **ADDI**, which add two 32-bit register operands or a 32-bit register operand and a sign-extended 16-bit constant, respectively. 
	2. **ADD** adds the values in two registers **rs** and **rt**, and **ADDI** adds the value of **rs** to a sign-extended 16-bit value and stores the value in **rt**.
2. The processor supports a **LOAD** instruction that reads a 32-bit memory word into a specified register.
	1. The only memory addressing mode supported by this processor is *base+offset* mode: in other words, the specified register **rs** only stores the 32-bit base address of the value,. The specified 16-bit immediate value is then sign-extended to 32 bits and added to base register contents to get the 32-bit memory address.
3. The processor supports a **STORE** instruction, which writes a 32-bit memory word into a specified register. 
4. The processor also supports a **BNEZ** instruction, which takes the branch if the value in the specified register is non-zero.
	1. The **BNEZ** instruction computes the branch target address as the sum of the sign-extended offset specified in lower-16 bits of the instruction and the address of the instruction immediately following the branch, i.e. the instruction that we branch to. Source register **rs** determines the branch condition: the branch is taken if the value in **rs** is non-zero, and not taken otherwise. 
5. **NOP** instruction that does not affect processor register or memory state.
6. **HALT** instruction that completely stops the processor. 

## Instruction Formats

The instruction formats are below. The Opcode tells the processor what type of instruction it is receiving, which is why it is consistently the first 6 bits of the instruction.

![[Pasted image 20250903154436.png]]

## Pipeline Model

Note: The reason we have **shadow pipeline registers** to store outputs of stages is because our implementation of the processor is not in a HDL. In other words, all of the stages are not computed concurrently. This is a problem because we will see that some data necessary to complete a stage will be overwritten if we complete the stages sequentially. The way we choose to work around this is to compute each stage sequentially, but store the outputs in **shadow pipeline registers** so that the value in the corresponding pipeline register is not overwritten and can be referenced for the next stage computation. In the end, we write the values of the shadow registers to their corresponding pipeline registers. 

The processor has 5 stages, numbered 1 to 5:
1. **FETCH**: Read an instruction from instruction mem location pointed to by the **PC** and update **PC** to the address of the next instruction to be executed (typically +4, unless a branch is taken). 
2. **ISSUE**: Decode the instruction and generate relevant flags to distribute to other modules within the processor. Read from source registers, and store fields and values in shadow pipeline register PR1. Set **writeback** flag if instruction will update a destRegister in the WRITE stage. Output a four bit bit vector called **control** identifying the instruction. A **HALT** instruction should set an **isHalt** flag HIGH.
3. **EXEC**: The execute stage reads the pipeline register PR2 to identify the operation and the operands needed by the ALU. It performs the requested operation and stores the results in shadow PR3.
4. **MEM**: This stage performs memory instructions as well as resolving the branch outcome of the BNEZ instruction. The address for a LOAD or STORE is obtained from the result field of PR3. The data for a STORE is gathered from the operand2 field of PR3, while the memory value read by a LOAD updates shadow PR4.

	MEM also handles branches. The outcome of the branch would have been computed in EXEC stage and saved in PR3. The target address of the branch is computed in MEM. If the branch is taken, **updatePC** is set HIGH, and **nextPC** is set to the computed target address. These are used by the FETCH stage in the following cycle to determine the next PC read from instruction memory.
5. **WRITE**: This stage checks PR4 to see if the instruction should update a register (writeback from decoder in ISSUE is HIGH), and, if so, writes to the destination register with the result. 

Each stage is separated by pipeline registers to store intermediate data. The goal here is to break up our combinational logic into stages so that we can increase our clock speed. Another nice side effect of this is that we can start pushing other instructions through the pipeline immediately after the first one gets pushed in. 

![[Pasted image 20250903155717.png]]


## Synopsis

The idea for this project is to implement NOPs to avoid data and control hazards.

**Data hazards:** Data dependencies between instructions.

**Control hazards:** Disruptions caused by program control flow. 
## How to Compile and Execute

To COMPILE:

	% gcc sim.c fetch.c issue.c exec.c mem.c write.c sync.c utils.c <PROGRAM FILE> ./yacsim.o -lm -o runme

<PROGRAM_FILE> is one of program1-3.c. 

To EXECUTE: 

	% ./runme


## Files

**program1.c:** Adds together integers of array1.
**program2.c:** Performs element-wise addition of integer arrays *array1* and *array2*, and stores the result in *array3*. 
**program3.c:** Copies integers from array1 to array2.

Size of the arrays is changed by the constant NUM_ITERATIONS in global.h

Constants in global.h to change the memory address of each array.

Maximum size of the arrays is 256 integers

The reset() function loads the program into instruction memory, initializes the arrays, sets initial register values, and clears internal pipeline registers


# References
