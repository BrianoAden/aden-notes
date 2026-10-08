2025-09-02 13:00

Status:

Tags: [[Advanced VLSI]] [[Lecture Notes]]

Project 1 assignment going to be posted on Thursday. 
- The purpose of the assignment is to become familiar with the design tools.
- Tutorial labs from Xilinx on Model Composer intro.
- Basic Vivado FPGA design intro.
- Aslo, NVIDIA GPU and CUDA intro.

## FPGAs as Prototyping Tools

Flexible hardware resource for system design
Many possible design flows - we work with two in this class:
- **Xilinx Model Composer**
	- Add-on Module to Simulink within Matlab
	- More flexibility in choice of FPGA boards - JTAG
	- User needs to manage separate ".bit" file
- **Labview FPGA**
	- Used in Physics labs, industrial settings
	- National Instruments Add-on Module
	- Uses specialized NI FPGA boards
	- Adds synthesized ".bit" file to "VI"

## Uploading to FPGA

Constraints file specifies what peripherals the pins of the FPGA are connected to. 

## Introduction to GPU and CUDA

Graphics Processing Units have evolved from basic display controllers in ASCII or text graphics terminals.

Original GPUs were a "helper" to the main CPU to off-load display tasks

Relied on "dual port" graphics memory
- CPU would fill with data
- GPU would "raster" on the display screen

As images became more complex, GPUs were outfitted with computational capabilities so that we could rotate or perform operations on an image
- They eventually became the General Purpose Processing Unit

Programming of GPU became more versatile, leading to the development of CUDA
- Compute Unified Device Architecture with NVIDIA

## Heterogeneous Parallel Computing

Use the best match device for a specific operation
- DSP Cores
- Throughput Cores
- Memories, etc

## CPU AND GPU

CPU is latency oriented, GPU is throughput oriented

CPU has
- Powerful ALU
	- Reduced operation latency
- Large Caches
	- Convert long latency memory access to short latency cache accesses
- Sophisticated control
	- Branch prediction for reduced branch latency
	- Data forwarding for reduced data latency
GPU has
- Small caches
	- To boost memory throughput
- Simple control
	- no branch prediction 
	- no data forwarding
- Energy efficient ALUs
	- Many, long latency but heavily pipelined for heavy throughput
- Require massive number of threads to tolerate latencies
	- Threading logic
	- Thread state

**CPUs are best for sequential operations, whereas GPUs are good for parallel operations**

## ASIPs

Application Specific Instruction Processors: Processors that are programmable, and designed to be good at a specific application
# References
