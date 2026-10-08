---
title: Processor Microarchitecture Lecture 1
publish: "true"
---
File Created: 2026-01-13 11:00  
Last Modified: 2026-01-13 11:00

## Goals
- Understand the **principles** underlying computer architecture
- Learn the micro architectural **mechanisms** used for high performance
	- Register Bypass
	- Reorder Buffer
	- Load Store Queue, etc
- Develop **implementation** experience of components and their integration in Verilog
	- Simulate behavior of RTL blocks
	- Future iterations of the course will port blocks onto FPGAs

**Instruction Set Architecture:** Contract between hardware and software. Details instructions that are able to run on the [[Microprocessors|microprocessor]]. 
**Microarchitecture:** Hardware implementation of the [[InstructionSetArchitecture|ISA]]. 

## Overview

![[Pasted image 20260113111703.png]]

## Quiz

1. "Optimize the common case" as a design paradigm in computer architecture is a corollary of **Amdahl's Law.**
	1. **Moore's Law** states that the number of transistors we can fit on a processor roughly doubles every 2 years.
	2. **Dennard's Law** states that the power consumption, as a result of increased transistors on a die, increases exponentially. This reduces our ability to scale, and thus led to the introduction of multiprocessor cores.
2. The acronym [[MIPS]] in computer architecture refers to **Multiple Instruction Processing System** and **Millions of Instructions per Second**. 
	1. **Multiple Instruction Processing System** is a type of [[RISC]] processor. It was an early pioneer of RISC processors. 
	2. **Millions of Instructions per Second** is a metric to measure processor performance.
3. RISC processors generally **have a LARGER instruction memory than their CISC counterparts**, due to requiring more, albeit simpler, instructions to complete the same task. They also use **[[Pipelining|pipelining]] to improve performance.**  Pipelining [[CISC]] designs is much more difficult due to variable instruction lengths, which introduce hazards. Modern processors get around this by internally converting instructions into multiple micro operations. RISC processors also **perform operations on register operands rather than memory operands.** 
4. ![[Pasted image 20260113114941.png]][[NonBlockingAssignment|Non-blocking assignment]] forces both variables to be assigned concurrently. Used for[[SequentialLogic|sequential logic]].
5. ![[Pasted image 20260113115125.png]][[BlockingAssignment|Blocking assignment]] allows both variables to be assigned sequentially. Used for [[CombinationalLogic|combinational logic]].
6. ![[Pasted image 20260113115241.png]]We witness a [[RaceConditions|race condition]] in this example. This is bad code, since you can never be sure which will "execute first". It is nondeterministic. 
7. ![[Pasted image 20260113115639.png]]
8. A [[TrapInstruction|trap instruction]] is used by a program to request a service from the [[OperatingSystem|operating system]]. An [[Exceptions|exception]] is raised on certain program errors. A device requesting service raises an [[Interrupts|interrupt]].
9. A [[Stacks|stack]] data structure is used to implement function calls to allocate local variables and to save the initial state (before function call) and registers.  
# References
