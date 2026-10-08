2025-08-28 09:45

Status:

Tags: [[High Performance Computer Architecture]] [[Lecture Notes]]


## Single Cycle DLX Microarchitecture

**Functional Modules:** 
- Reg file
- Instruction Mem
- Data Mem
- ALU : Performs arithmetic 
- Decoder : Decodes instructions and sets relevant flags
- Program Counter : Keeps track of where we are in the program

## Data Path

The path of information flow in executing an instruction sequence of functional modules. 

## Combinational Circuits vs Registers

**Combinational Circuit:** Memoryless. Made up of logic gates. Output is continuously evaluated as a boolean function of the inputs.

**Sequential Circuit:** Memory device. Only evaluated at a relevant clock edge or level. 

**EX:** n-bit registers are memory devices. Made from n edge-triggered Flip Flops, each storing 1 bit. 

## Functional Units

**Decoder:** Generates control signals from instructions. 

**ALU:** Takes into two operands and a ALUop, which determines the operation, and spits out a result. 

**Instruction Memory:** Combinational logic. We put in an ADDR, and return the data in the register at that address. 

![[Pasted image 20250828095427.png]]

**Registers/Memory:** Data written to register/memory only on pos clk edge. Data must be available for a small time before clock edge (setup time). Value must also be held constant for a small time after clock edge (hold time). 

**RegFile:** It will be an array of registers, typically 32. SRC1 and SRC2 inputs are the registers to be read from. destReg is register to be written to. DATA is data to be written, we is write enable.

**Data Mem:** Take an ADDR in and DATA. If MEMRead asserted, output DATA at ADDR, if MEMWrite asserted, output input DATA which should now be stored in ADDR.

![[Pasted image 20250828100044.png]]

## Hypothetical Single-Cycle Implementation of DLX

Each instruction completes in one cycle. 

**During clk cycle:**
1. Read instruction from Instruction Memory
2. Decode/Generate control signals
3. Read source register values
4. Generate ALU output
5. Read Data Mem for Load Instruction
6. New PC value is computed

**At next clk edge:**
- Update PC
- Update destination register if instruction updates a register
- Update data memory at the clock edge if a STORE instruction

![[Pasted image 20250828100647.png]]

There are various paths based on instruction. How do we get our processor to use the correct path based off the input instruction???
**MUXES**

![[Pasted image 20250828101124.png]]

Our Decoder module outputs a few more control signals for the MUXes, which chooses paths to take based off the input instruction.

The instruction tells us how to set these control signals. 

![[Pasted image 20250828101402.png]]

Branch allows us to jump to different instructions, rather than +4 every time. The PCSel tells us whether we want to branch or not. If we have a branch instruction, and the condition of the branch is met, then we take the branch. The condition of the branch is determined by the ALU. How do we set PCSel? 

![[Pasted image 20250828101800.png]]

All instructions take place in *one* clock cycle. The clock period needs to be long enough for signals to ripple through all of these modules. LW is the longest instruction, so the clock period is bounded by this instruction. 

## Performance Model

How do we quantify performance of a processor?
We look at things like:
**Instruction Throughput (MIPS rating):**
- Clock Frequency (cycles/sec) x IPC (instructions/cycle) x 10^-6
	- This gives us the number of instructions we compute per microsecond
IPC (Instructions/Cycle) = 1/CPI
CPI (Cycles/Instruction)
- Measure by counting instruction completion rate
- For single-cycle CPI = 1
**How do we improve the performance of a processor?**
- In the early days, we focused mainly on increasing the frequency. Less pressure on the architect, more on the manufacturing process.
- More modern techniques involve increasing IPC.
**Ways to increase IPC:**
- You can break up your combinational logic with registers to increase clk frequency. Clk period is bounded by register to register delay. This is called buffer insertion. 
- Variable cycles instruction execution (maybe one instruction takes 5 cycles, but the rest may take 2. Opportunity to increase clock frequency)
- Pipelining

## 5-Stage Processor Pipeline

![[Pasted image 20250828103439.png]]

When modules are freed up, load in data. 

![[Pasted image 20250828103632.png]]

CPI = 1 + 4/n (basically operating at CPI = 1 as n number of instructions grows arbitrarily large.)
# References
