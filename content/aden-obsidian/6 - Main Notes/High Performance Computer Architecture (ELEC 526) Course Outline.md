
Tags:  [[High Performance Computer Architecture]] [[Courses]]

## Overview and Learning Outcomes

The goal of this course is to provide students with an advanced understanding of the architecture and implementation of modern HPC systems.

The students will be able to 

  1. Describe the handling of data and control dependencies in high-performance uniprocessors
  2. Design a microarchitecture for pipelined and dynamically scheduled out-of-order processors
  3. Implement simulation models of high-performance pipelined processors
  4. Analyze the behavior of non-blocking and lockup-free caches 
  5. Describe the problems of cache coherence in multiprocessor systems
  6. Implement and analyze the behavior of snooping and directory-based cache coherence protocols   
  7. Describe the problems of memory ordering and strong and weak consistency in multiprocessors
  8. Describe the implementation of virtual memory and its interaction with the cache hierarchy
  9. Describe architectural support for synchronization including transactional memory
10. Describe the architecture of modern storage and network systems for datacenter computing
11. Have familiarity with elements of datacenter computing and system virtualization concepts

## Homework & Projects

There are 5-7 homework assignments.

Projects will involve implementing C programming-based simulation models, running simulation experiments, and analyzing results.

## Topics

1. **Processor**
		a. Instruction Level Parallelism
			1. Simple Static Pipelining
			2. Dynamically-scheduled pipeline processors
			3. Superscaler, VLIW
		b. Data Parallelism
			4. SIMD, Vector and Stream Processors, GPGPUs
		c. Thread Level Parallelism
			5. Multithreaded Processors
			6. Multi Cores
			7. NUMA and multiprocessor processors
			8. Clusters
		d. Domain-specific Accelerators
			9. GPU, TPU, SDN, Compute-In-Storage, others
2. Memory
		a. Uniprocessor Caches
			1. Organizations and Addressing
			2. Lockup Free Caches
			3. Multi-level Cache hierarchy
		b. Multiprocessor Caches
			4. Cache Coherence
			5. Snooping and Directory Protocols
			6. MSI, MSEI, MSEOI, MESIF protocols
		c. Memory Orderings and Memory Consistency Models
		d. Virtual Memory
			7. Demand Paging
			8. TLB and Page Walks
			9. Processor Caches and Virtual Memory
			10. Virtual and Physical Caches
		e. Emerging Memory Devices
			11. NVM, HBM, PIM, others
3. Synchronization
		a. Spin Locks
		b. Sleep Locks
		c. Lock-Free Synchronization
		d. Transactional Memory
4. I/O and Storage
		a. Bandwidth, Latency, Topology
		b. Scalable Networks : Clos, Butterfly, Fat Trees
		c. PCIe, CXL, RDMA (InfiniBand, RoCE)
		d. Distributed storage architectures: Reliability, RAID, Erasure Codes
5. System Resource Virtualization (Software Defined Everything)
		a. Sharing vs Isolation
		b. Resource Virtualization Techniques
		c. Resource Scheduling
# Lecture Notes

[[High Performance Computer Architecture Lecture 1]]
# References

![[Elec 526 Syllabus 2025.pdf]]