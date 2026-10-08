---
title: Processor Microarchitecture Lecture 2
publish: "true"
---
File Created: 2026-01-15 11:01  
Last Modified: 2026-01-15 11:01

# Why [[CISC]]? Why [[RISC]]?

## CISC
- **Reduce Semantic Gap:** Instructions closer to language constructs reduce burden on [[Compilers|compilers ]](theoretically).
- **Reduce Instruction Memory Size:** Main memory expensive and small. Reduces pressure on instruction cache.
- **Faster:** Avoid multiple [[Instruction Memory|fetch]] and [[Decoders|decode]] cycles.

## RISC
- **Software:** Compilers seldom used very complex instructions. Move more towards flat programming languages (like C).
- **Hardware:** Main memory got larger and cheaper, so easier to accommodate large instruction memory sizes of RISC. Decoding complex instructions slowed down the entire system. Simpler instructions of RISC were easier to decode. Smaller decoder means we can use leftover chip area for additional registers, caches. We can also use optimization techniques like [[Pipelining|pipelining]] with RISC. 

# Basic Computer Organization

![[Pasted image 20260115111537.png]]

# Simplified DLX ISA

[[DLX]]: Idealized RISC processor (similar to [[MIPS]], [[ARM]], [[RISCV|RISC-V]]).
- All operands are 32-bit.
- 32 32-bit Integer General Purpose Registers.
- 32 32-bit Floating Point Registers.
- No condition code registers. 
	- A register that stores a flag that is set as the result of an operation (ADD, SUB, etc), and referenced when executing conditional branch instructions. 
	- Having a condition code register means every instruction might have a side effect. Meaning we need to constantly check to see if we need to set the flag as a result of an operation.  

**Word-addressable** memory
- 32-bit words at address 0, 1, 2, ...
- 32-bit memory addresses.

**Load/Store** architecture
- Only memory operations are LOAD (LW) and STORE (SW).
	- **LW** reads a word from memory into a CPU register.
	- **SW** writes a CPU register into a word of memory.

Memory accessed using **base + offset** 

**Target Address** for control instructions (conditional branches) is calculated as PC + 4 + Sign-Extended(d), where d is a 16-bit displacement bit vector.  

# Single-Cycle DLC Microarchitecture 

**Functional Modules**
- Register File
- Instruction Memory
- Data Memory
- Arithmetic Logic Unit
- Decoder, Program Counter 

**Data Path**
- Path of information flow in executing an instruction. Sequence of Functional Modules.
- Typically IM -> PC -> Decoder -> Reg File -> ALU -> Data Memory.

**Timing and Control**
- Enforce sequencing in the data path.

# Combinational Circuit vs Registers

**Combinational Circuit**
- Composed of logic gates (AND, OR, XOR, etc).
- Output is a function of inputs and continuously updates.

**n-bit Register** (Memory Device)
- Built from n **edge-triggered Flip Flops** each storing 1 bit.

**Read**
- Current contents of the Flip Flops always available at the output.

**Write**
- Register value updated at the **positive edge** of the **clock** signal.
- To update:
	- the **Write Enable** signal must be asserted.
	- the **DATA** to be written must be stable at the register inputs (setup time).

**Flip Flop vs Register**
- Flip flop changes at every clock cycle. Registers have an additional enable signal to allow changes to occur at the operator's discretion.  

# Hypothetical Single-Cycle Implementation of DLX

Each instruction completed in 1 clock cycle.  

**During clock cycle:**
- Read Instruction from Instruction Memory
- Decode/Generate control signals
- Read source register values
- Generate ALU output
- Read Data Memory for LOAD instruction

# Timing: Single-Cycle Design

Clock Period T determined by delays in the longest datapath
# References
