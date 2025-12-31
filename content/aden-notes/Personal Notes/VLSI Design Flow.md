## System Design

When beginning the development of an ASIC, the first thing you want to do is carefully lay out your requirements, as well as functionality you would like to see in your final product. 

This includes developing your FSMs and datapaths, how they will interact, inputs and outputs, etc. 

A lot of the work will be here!
## Implementation

Once you've decided on the system you want to implement, and have a good idea of what it will look like, you need to implement it!

We use HDL, or Hardware Description Languages, to model our FSMs/Datapaths and how they will interact with one another. 
## Pre-Synthesis Simulation and Verification

After implementation, you will need to write a testbench for your design. This is also written in HDL. Here, you supply inputs for your design, with the intention of verifying key functionality, as well as sniffing out any bugs that may have snuck in during implementation.

After you've written your testbench, you need to simulate your design in QuestaSim. QuestaSim is a waveform viewer that you can use to view inputs and outputs, and verify that everything is functioning correctly. 

Oftentimes, you will find bugs and have to go back to the Implementation phase.

## Synthesis

After you've verified that your design is functioning as expected, it's time for synthesis! Here, we use a tool, like Synopsys Design Compiler, to synthesize our design into hardware using a predetermined cell library. 

Synthesis produces a .vh file, or structural description of your system using cells from the cell library. Sometimes, issues can arise from synthesis, which leads us to our next phase.

Here, you can view an approximation of the cell usage, area, power consumption, and timing. 
## Post-Synthesis Simulation and Verification

After synthesis, it's important to verify that everything is STILL functioning as expected. Sometimes errors can happen when cells in the cell library you are using are used in unexpected ways. 

## Place and Route

Okay. Now you have a synthesized design that works as you expect it to! Great. Now we can use a tool like Innovus to place and route the synthesized hardware. We can then import the GDS file into a VLSI Layout tool like Magic.

Here, you acquire a .vh file from your synthesis tool. This is a structural description of your logic, using cells from the used cell library. Your density matters, and is a value from 0-1. A very aggressive density like 0.9 can lead to shorts or cells overlapping. 

## Gate Level Simulation

Now, we can create a .sim file with inputs described across many clock cycles. We simulate our Magic cell, and verify that everything is still functioning as expected.

## Integrate into I/O Padframe

Now, we can import the cell into a padframe. A padframe is a perimeter of I/O pads that allow your cell to interact with the outside world. The pads are configurable (i.e. they can be set as inputs or outputs, depending on if they're connected to GND or VDD), and are internally connected to the inputs and outputs of your cell.

## Final Simulation 

Now, we need to do our last simulation to make sure that our pads are successfully delivering inputs and receiving outputs from our IC. 

## Tape Out
