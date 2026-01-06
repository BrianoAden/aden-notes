2025-08-25 23:05

Status:

Tags: [[High Performance Computer Architecture]] [[Lecture Notes]]

## Overview

First homework is a pipelined processor. Homework 0 gets us familiar with simulation software used in the class.

## Processor Architecture

**Instruction Set Architecture (ISA):** 
- Hardware/Software interface
	- In other words, it's how the computing device reconciles software and hardware
- Model seen by SW:
	- Instruction format, registers, memory, addressing, etc
**Microarchitecture:** 
- Hardware implementation of the ISA
- Functional Units, Datapaths, Controllers, Timing, etc
- Trade-off between cheap and slow processors vs expensive, complex and fast processors
- Under-the-hood optimization (These are not visible to program)
	- Caching
	- Pipelining
	- Out-Of-Order Execution
	- Transparent multithreading
	- Coherence and consistency protocols

## Processor Parallelism

**Instruction Level Parallelism:** Trying to do many things all at once
- Pipelined, Superscalar, VLIW
- Achieves more performance by conducting many instructions in parallel
**Data Parallelism:** Good for scientific level programs
- Identical operations on elements of large arrays (vector addition, for example)
	- SIMD, Vector and Stream Processors, GPUs
- Might break up an array into four chunks, and conduct vector addition on each chunk using a different adder
**Thread Level Parallelism:** Most general. Multiprocessors can support thread level parallelism, as long as their SW is compatible.

## Memory Systems

**Uniprocessor Memory**

Suppose you have one processors with one memory and multiple caches. 

**Cache:** Small amount of high speed memory

The processor can access the cache in a certain number of cycles. Usually ordered in terms of size and speed. L1 is smallest and fastest, LN is largest and slowest. 

An inclusive cache means that everything in L1 is also in L2, and L3, and so on. Exclusive cache means that every cache has a unique value saved in memory. Most caches are inclusive. One advantage of inclusive is that if you probe one cache looking for a specific value, you will immediately know if it is stored in cache or not. 

**Lockup-free caches**

**Miss Under Miss:** Stall until you find value (?). 
**Hit Under Miss:** Don't stall. Continue executing instructions after miss (didn't see value in cache). Stop after second miss.

**Multiprocessor Memory**

Suppose you have multiple processors, each with their own cache, and a shared memory. An x variable is stored in memory. Each processor conducts operations on x, and looks to the x in memory when it performs these operations. 

**Coherence:** Almost every HP processor implements this. 

## Synchronization

Multiprocessors, all with different instructions?

## RISC/CISC and More

**DLX:** Idealized RISC processor

**Reduced Instruction-Set Computer:** Small instruction set so that it may complete instructions quicker. 

Prior to RISC the main school of thought was CISC (complex instruction set). Instruction sets allowed for string compares, etc. 

The goal with RISC was to reduce the *semantic gap*, or the gap from what the hardware understands, and what the software programmer understands. 

The argument against RISC was that with CISC it only required one instruction to perform a complex task, however, the gain in hardware speed was not worth it because the complex instructions were hardly ever used. It didn't suit the programmer's need.

RISC kept things simple. Allowed the programmer to create software to implement complex instructions. Hardware optimization (pipelining, etc) made up for lack of hardware speed. 

**Load/Store Architecture**: The only instructions that can read/write from memory are Load and Store. 

**Byte-addressable**: Granularity of memory. Each byte has its own address. 

**Condition Codes:** Condition codes are a flag which is set as a side effect of some other instruction (if an add generated a carry, overflow, etc). The issue here is that the instruction has created an unnecessary state that you may or may not need. We used this in 326!

The alternative is to just determine if there was a carry or something else in the next instruction, rather than having to store a state. 

# References
