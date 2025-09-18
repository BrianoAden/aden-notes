Hello! In this page, I will discuss what an FPGA is, how it works, and what it is used for!
## What is an FPGA?
An FPGA is a *Field Programmable Gate Array*, or a specialized IC that is designed for implementing custom algorithms and Digital Circuit blocks on the fly. 
## How do They Work?
Well, recall that Digital Circuits are systems of Digital Logic Gates configured in such a way that they can perform desired functions. 

FPGAs contain *hundreds of thousands* of these **Configurable Logic Blocks**, or CLBS, that can be connected in various ways to perform any custom task. There exist programmable interconnects between these [CLBs](obsidian://open?vault=Obsidian%20Vault&file=Personal%20Notes%2FConfigurable%20Logic%20Blocks), which we can interface with through **HDL.** 

![[FPGAInternal.png]]

## How do we Program FPGAs?
**HDL**, or Hardware Description Languages, are high-level languages which allow you to describe the functionality of your system, and synthesize low-level gate designs to implement it. 

Once you've written your high-level program, a bitstream file is created
## What Can we Use FPGAs For?
Anything we want! We can use them to emulate a processor, or a microcontroller for example. They're very fast, and can be used to conduct many operations in parallel. 

Microprocessors have to execute according to their instruction set every single time, but the CLBs inside an FPGA are completely configurable and separate. This way, inputs go their respective blocks, and all computation can be performed in parallel. Neat!

FPGAs can have up to one thousand pins. 

## What Are The Disadvantages? 
FPGAs are expensive! It's not cost effective to emulate a microcontroller on an FPGA, when you can just buy the microcontroller for cheap. 

Since they are so flexible, they are not dedicated to optimizing for power consumption, like microcontrollers are. 

Sometimes the high pin count is not always the most friendly/easy to use. 

You have to use complex tools to program and verify FPGA behavior (HDL, waveform viewers). 