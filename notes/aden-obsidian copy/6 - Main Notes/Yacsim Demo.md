2025-09-01 20:51

Status:

Tags: [[Assignments]] [[High Performance Computer Architecture]]

## How to Untar

Simply run in your terminal

	tar -xvf filename.tar

## Trace File

The file maketrace.c creates a trace of memory writes to successive elements of an integer array. Create the memtrace file and execute it by running 

	% gcc maketrace.c
	% ./a.out

Then run

	% od -x memtrace

To preview the trace records. 

## Parsing the Trace File

The trace records are kept in hexidecimal.

The first 7 numbers are the index of the memory trace. The next 8 numbers are the *memory address* of the trace record. The third set of 8 are the *memory value*. The fourth set of 8 is the type of operation being performed. The last set of 8 is the memory address of the *subsequent trace record*.

This is the order that the memtraces follow. They are not necessarily all in the same position of the line however. 

## Simulation Files

The sim file holds demo.c with helper functions in utils.c. The object file yacsim.o is the simulator. The file global.h holds useful constants and definitions. 

To create the simulation executable in a file called runme, do

	% gcc demo.c utils.c ./yacsim.o -lm -o runme

To run the executable and put the output in a file named out, do

	% ./runme > out


## Little's Law

Little's Law is a law that describes the average number of people or items in a queue as a function of the rate at which items enter the queue, and the rate at which they have to wait before being able to leave. 

	L = Y x W

Where
L - the average number of items in a queueing system
Y - the average number of items arriving at the system per unit of time
W - the average waiting time an item spends in a queuing system

In the real world, this is particularly useful for determining the size of your waiting area. 


# References
