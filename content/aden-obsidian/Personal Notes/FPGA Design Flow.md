Here, we will discuss the FPGA Design Flow.

## Design Entry
Here, we use an HDL to program our system. This is the longest step in the implementation process.

## Design Simulation
Once your design is described in HDL, you need to verify that it functions correctly. We do this through simulation. 

In simulation, you can observe the outputs of the system corresponding to the input set that you have provided for the system in your test benches. You can then compare the observed output to the expected result. 

## Design Synthesis
This is a vital step. It's the conversion of a high-level description of hardware to a lower-level implementation!

In the case of FPGAs, LUTs are configured.

## Design Placement
In this stage, the exact location of hardware resources is decided.

## Design Routing
Proper connections between wires and hardware resources are established!
![[LUTInterconnect.png]]
Note that the red and green wire are valid connections between these two LUTs. 

## Configuration File Generation

Synthesis, placement, and routing results are transferred to FPGA using a bit file. 

After the bit file, or bitstream, is written to the FPGA, the FPGA is fully configured!

The bitstream file contains data to configure LUTs and interconnect wires.

## FPGA Configuration
Bit file is written into the FPGA using a programmer device. This is typically done over JTAG protocol.

![[FPGAProgramming.png]]

