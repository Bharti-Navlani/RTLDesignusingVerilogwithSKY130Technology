# RTLDesignusingVerilogwithSKY130Technology

<img src="Images/RTLDesignusingVerilogwithSKY130Technology.PNG">

# 5 Days Workshop on "Basic RTL Verilog Design and Synthesis Using Sky130PDKs" 

This workshop covers the topics from fundamental to cirtical issues faced by RTL Designers & Synthesis Engineers in VLSI Industry <br />
The course bascially includes following 3 Major Parts <br />
* Verilog Coding Guidelines , Writing Testbench & Validating the Design as per Specification <br />
* Converting Logic in Synthesizable Design & Optimization <br />
* Validating the Synthesized Design to Match as per Specification <br />

# Table of Contents

## Day 1 - Introduction to Verilog RTL design and Synthesis
Introduction to open-source simulator iverilog<br />
Labs using iverilog and gtkwave<br />
Introduction to Yosys and Logic synthesis<br />
Labs using Yosys and Sky130 PDKs<br />

## Day 2 - Timing libs, hierarchical vs flat synthesis and efficient flop coding styles
Introduction to timing .libs<br />
Hierarchical vs Flat Synthesis<br />
Various Flop Coding Styles and optimization<br />

## Day 3 - Combinational and sequential optimizations
Introduction to optimizations<br />
Combinational logic optimizations<br />
Sequential logic optimizations<br />
Sequential optimzations for unused outputs<br />

## Day 4 - GLS, Blocking vs Non-Blocking and Synthesis-Simulation Mismatch
### GLS,Sythesis-Simulation Mismatch and Blocking/Non-Blocking Statements<br />
### Lab 4.1 - GLS and Synthesis-Simulation Mismatch<br />
### Lab 4.2 - Synth-Sim Mismatch for Blocking Statement<br />


## Day 4 - GLS, Blocking vs Non-Blocking and Synthesis-Simulation Mismatch
### GLS,Sythesis-Simulation Mismatch and Blocking/Non-Blocking Statements<br />

#### About GLS
When RTL gets synthesised to Netlist , it is expected to have same functionality in netlist also.

To Ensure RTL & Netlist functionality are matching 
* First level of check : Logical Equivalence Check (LEC) is performed between RTL & Netlist which reports if there is any mismatch
* Second Level of check : Gate Level Simulation (GLS) which means running the testbench with netlist as design under test
Since the  functionality of the RTL & Netlist is expected to be same , hence same testbench is used to run both at RTL & Netlist level

All functional mismatch are not identified by LEC , Hence Second level of check GLS is required  

#### Types of GLS
1) Zero Delay : Zero delay simulation means simulating the netlist without annotating any timing data
2) Unit Delay : Simulation with assumption that all elements in the design have unit delay
3) SDF /Timing Simulation : Actual Delay Simulation

#### Synthesis Simulation Mismatch

Synthesis Simulation Mismatch can be because of following reasons : -
1) Missing Sensitivity List
2) Blocking vs Non-Blocking Assigments
3) Non Standard Verilog Coding 















