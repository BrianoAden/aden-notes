---
publish: false
---

2025-10-07 13:20

Status:

Tags: [[Advanced VLSI]]

## Project 3 Overview

The idea is to study different optimizations. The base case is no pipelining matrix multiplication (nested for loops). Then we need to look at how it operates with a pipeline of 10ns, 5ns. We unroll (?) it with 10ns and 5ns. Unrolling means taking each iteration and performing it as a separate step/function. This would use more hardware, but changes the schedule at which we perform operations. 

For "external" functions, or some IP in the programmable logic communicating with the ARM processing system, the PIPELINE and UNROLL optimization methods are very effective. 

For systems with multiple "internal" functions, the INLINE and DATAFLOW are effective between each IP block. 

## No Pipeline 10 ns
10 ns clock gave us 250 ns of latency. It took 26 stages at 7.196 ns per stage. The latency is saying that for a 10 ns clock, it's taking 26 clock cycles, or 250 ns latency just about. It's just the amount of time it takes for the function to completely finish. 

## Pipeline 10 ns
110 ns latency. We see an improvement! FF and LUT usage stayed about the same. This is interesting, since we would think that pipelining would mean that you would need more FF to store intermediate values. 

## Pipeline 5ns
Now, for some reason, the stage time is about 3.238 ns. I assume this is because it broke up the combinational logic even further to accommodate the new clock speed. The new latency is 70 ns. The iteration latency went up from 3 to 6. 

## Loop Unroll 10 ns
Note: Apparently unrolling encompasses removing loop instructions from an instruction set, and instead just adding duplicate instructions which mimic the loop behavior. It's a space-time tradeoff.

![[Pasted image 20251007134410.png]]
New program only has to perform 20 iterations, as opposed to 100. 

90 ns latency. 
# References
