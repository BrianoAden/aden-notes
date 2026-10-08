2025-08-26 13:02

Status:

Tags: [[Advanced VLSI]] [[Lecture Notes]]

## Overview

Lab Assistants: Phong Tran pt51@rice.edu

We will be using design tools on PCs for FPGA and GPU with Linux CLEAR cluster for ASIC and FPGA. We will focus mostly on FPGA SoC. This is a high-level synthesis down to Verilog class. We are going to be using C++ for high-level synthesis. We will also be using CUDA. 

## ASIC and System on Chip Design Flow

Algorithm --> Architecture --> Implementation --> Runtime

**Algorithm:** Linear Algebra based algorithms. Use software like C++ Vitis HLS, Catapult. 
**Architecture:** ASIC, FPGA-SoC
**Implementation:** ASIC (Design Compiler Synthesis, Innovus P&R), **FPGA-SoC (Vivado, Vitis)**
				ASIC (Custom, Standard Cells), **FPGA-SoC (Ex: ZYNQ)**
				ASIC (Custom I/O), **FPGA-SoC (PetaLinux, Vitis)**
				ASIC (Custom driver), **FPGA-SoC (Bare Metal, Linux)**

## Course Structure

6 projects on FPGA/GPU/ASIC design using:
- AMD Xilinx system generator/model composer tools
- CUDA "C" for GPU
- Vivado/Vitis HLS for high level synthesis "C" to HDL
- Vivado for FPGA place and route
- Possible DC and SoC Encounter for P&R
- Vitis "C" code with Vivado for ARM PS/FPGA PL SoC integration

## Course Contents - Logic

Design methodology for ASIC - FPGA implementations
FPGA HW structures and fabrics
GPU HW structure and programming
Combinational Logic, Sequential Machines, and SoC Architecture
High-level DSP algorithm simulation and code generation

**Why HLS?** 
HDL programming is time-consuming. Hard to test and verify. HLS tools come from companies that are building embedded systems with specialized logic. They are trying to make it so HW design is more accessible to SW oriented individuals. 

## Course Contents - Architecture

Design and analysis of algorithm-specific VLSI processor architectures. 
- Implementation of pipelined and systolic processors

**GOAL:** Develop HW accelerators - exploit algorithmic parallelism

## Course Contents - Systems

How data moves throughout modules in a system. This will be the more challenging part of the course. We will be using AXI bus interface.

- GPU architecture and programming
- ARM core/AXI bus attachments of Programmable System (PS) to Programmable Logic (PL)
- I/O and timing analysis

**GOAL:** Real-world accelerator integration - overcome I/O bottlenecks

## Course Contents - Case Studies

Good to look at case studies to see where others have gone wrong, what they have done right.

**GOAL:** Understand system tradeoffs - learn from successes and failures

## Course Focus - Xilinx Zynq 7000

- Single chip SoC design
- Embedded ARM Core "PS" runs C++ code
- ARM AMBA Interconnect from core to internal and external peripherals
- AXI bus interfaces core to FPGA "PL" created from C++ or Verilog

Notes:
FPGAs typically do computations in integers. Not floating point. Can be configured to do FLOP, but inefficient. 

## Wolf Book - Review of Architecture

Anatomy of FPGAs - LUTs and Flip Flops

## Why VLSI?

Integration improves the design:
- lower parasitics = higher speed
- lower power
- physically smaller

Everything you touch has a processor inside! 

**Moore's Law:** Number of transistors will double every 18 or so months. Flattening out now.

## Cost of Fabrication

~$5 Billion. 

Typical fab line occupies about 1 city block, and employs a few hundred people. New fab processes require 6 - 8 months turnaround. Most profitable period is first 18 months to 2 years. 

New 2022 USA CHIPS Act - Industry, University, and workforce funding to build more domestic fabs.

## Cost Factors in Integrated Circuits

For large-volume ICs:
- Packaging is largest cost
- Testing is second largest cost

The smaller your technology, the more your mask cost is. The trend is exponential. 
# References
