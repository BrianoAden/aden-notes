1. Talk about Snake ASIC
	a. Talk about how we went through the entire design flow
	b. Talk about how we used dual phase clocking to prevent clock skew errors between sequential flip flops
		i. Talk about WHY we chose this 
			a. easy
	c. Talk about how we ran into an error with Synthesis where we didn't initialize our shift registers so they weren't being driven correctly
	d. Talk about how we learned structured design
		i. **Hierarchy**: Divide a system into smaller modules to be developed easier
		ii. **Regularity**: Create modules using set design rules, to maintain consistency and alleviate the debugging process as much as possible. Also, reuse modules wherever possible.
		iii. **Modularity**: Develop well-formed interfaces between modules so we can increase our level of abstraction and treat them as black boxes.
		iv. **Locality**: Physical and temporal
	e. Talk about FSMs and Datapaths
	f. Talk about how we wrote testbenches to test our design
	g. Talk about how we used cell library from OK State. 0.5 um process
	h. Talk about how we developed our code behaviorally, to allow for the synthesis tool to perform optimization
	i. Talk about how we used a density of 0.8, since we saw that some of our cells were seriously overlapping at 0.9.