Testbenches are written in HDL and used to test modules across many clock cycles. Waveform viewers use these to simulate behavior and assist with verification. Below is an example of a testbench for an AND gate.

	module my_and_tb();
	reg in_a, in_b;
	wire out_c;
	// create an AND instance
	my_and U1(.c (out_c), .a (in_a), .b (in_b));
	initial 
	begin 
	in_a = 0;
	in_b = 0;
	#5 //5 clock cycles
	in_a = 1;
	in_b = 0;
	#5
	in_a = 0;
	in_b = 1;
	#5
	in_a = 1;
	in_b = 1;
	#5
	in_a = 0;
	in_b = 0;
	#5
	$dumpfile ("my_and_tb.vcd");
	$dumpvars;
	$display("\t\t in_a,\t in_b,\t out_c");  
	$stop;  
	end  
	endmodule

The idea is to create a high-level interface, create an instance of the cell under test, provide stimulus and timing information, and allow for display.