---
publish: false
---

2025-09-22 21:56

Status:

Tags:

## High Performance Computer Architecture
1. In Project1C, we do not squash the instruction immediately after the Branch. This is okay if we wrongly predict a branch taken, in which the instruction will need to be executed. However, if we do take the branch, why would we opt to still execute the instruction instead of squashing it? I feel like this would force constraints on our Instruction Set Architecture. 
**Answer:** 
# References
