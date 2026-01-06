2025-09-18 13:08

Status:

Tags: [[Lecture Notes]] [[Advanced VLSI]]

## Mapping Matrices ot TPU and GPU

Unfold tensors into matrices. Map them to either TPU or GPU

## Scaling Limitations

As the size of the problem increases, more and more of our processing elements are utilized, and at some point our hardware platform saturates. 

## Zynq Architecture

The Zynq-7000 AP SoC architecture consists of two major sections
- **PS: Processing System**
	- Dual ARM Cortex-A9 processor based
	- Multiple peripherals
	- Hard silicon core
- **PL: Programmable Logic**
	- Shares the same 7 series programmable logic as 
		- Artix-based devices
		- Kintex-based devices

## Memory Map

- The Cortex-A9 processor uses 32-bit addressing
- All PS peripherals and PL peripherals are memory mapped to the Cortex-A9 processor cores
- All slave PL peripherals will be located between **4000_000 and 7FFF_FFFF** and **8000_000**

**PS ARM Core Boots First**
- CPU0 boots from on chip memory (OCM) ROM; CPU1 goes into sleep state
- On-chip boot loading in OCM ROM (Stage 0 boot)
- Processor loads First Stage Boot Loader (FSBL) from external flash memory
	- SD Card

## Configuring the PL

- The PL is configured after PS boots

# References
