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

## Day 4 - GLS, Blocking vs Non-Blocking and Synthesis-Simulation Mismatch<br />
### GLS,Sythesis-Simulation Mismatch and Blocking/Non-Blocking Statements<br />
#### About GLS<br />
#### Types of GLS<br />
#### Synthesis Simulation Mismatch
### LABS
#### Lab Part-1  GLS and Synthesis-Simulation Mismatch<br />
#### Lab Part-2  Synth-Sim Mismatch for Blocking Statement<br />


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


#### LABS
#### Aim  : Taking different design, analysing them at RTL level , synthesizing & Verifying them with GLS
#### Input Required: 
1) For RTL sims 
-> RTL Design : <verilog_model.v>
-> Testbench  : <testbench_verilog_model.v>
2) For Synthesis & GLS
-> Liberty File 
-> Primitive 
-> Standard Cell Verilog Model

### Lab Part-1 - GLS and Synthesis-Simulation Mismatch<br />

#### Design 1: Mux implement using Ternary Operator 

<img src="Images/L4_1_0_RTL_Ternary_Operator_Mux.PNG">

#### Figure 4.1.1 Verilog Model<br /> 

when sel is 1 , output y will have value from i1 
when sel is 0 , output y will have value from io
<br /> 
<br /> 
<br /> 

<img src="Images/L4_1_1_Open_GTK.PNG">

#### Figure 4.1.2 Performing Simulation <br /> 

iverilog command is used to dump the VCD (value change dump) & VCD is analysed using GTKwave
<br /> 
<br />
<br /> 

<img src="Images/L4_1_2_Waveform.PNG">

#### Figure 4.1.3 Output Waveform<br /> 

Above waveform clearly shows the the expected values at y when sel is changing 
<br /> 
<br /> 
<br /> 

<img src="Images/L4_1_3_Synthesis_step_2.PNG">

#### Figure 4.1.4 Synthesis<br /> 

Invoking yosys for synthesis & reading the input files 
<br /> 
<br />
<br /> 

<img src="Images/L4_1_4_Synthesi_step_3.PNG">

#### Figure 4.1.5 Synthesis<br /> 

After synthesis is performed , it reports with the cell(type&number) that is taken to build netlist
<br /> 
<br />
<br /> 

<img src="Images/L4_1_5_Synthesis_Step_4.PNG">

#### Figure 4.1.6 Synthesis<br /> 

Dumping the netlist & displaying the implementing design
Hence we can see that 2X1 is implemented using nand,or & invertor 
<br /> 
<br />
<br /> 

<img src="Images/L4_1_6_NL_TB_in_GTK.PNG">

#### Figure 4.1.7 GLS<br /> 

Performing GLS using primitives & verilog models for standard cell using the netlist dump at previous step with the same testbench which was used for RTL simulation 
<br /> 
<br />
<br /> 

<img src="Images/L4_1_7_GLS_output.PNG">

On comparing the RTL & NL waveform it correctly matches 

#### Figure 4.1.8 GLS Output<br /> 
<br /> 
<br /> 
*Note*: Above waveform matches with the waveform at RTL level which verifies the design is implemented correctly
<br /> 
<br /> 
#### Design 2: Bad Mux  

<img src="Images/L4_2_0_RTL_Bad_Mux.PNG">

#### Figure 4.2.1 Verilog Model<br /> 

Mux sensitivity list has sel which means the output will be changing only if there is a change in selection line
Hence the change in input if sel if not changing will not be reflected.
<br /> 
<br />
<br /> 

<img src="Images/L4_2_1_Open_GTK.PNG">

#### Figure 4.2.2 Performing Simulation<br /> 

iverilog command is used to dump the VCD (value change dump) & VCD is analysed using GTKwave
<br /> 
<br />
<br /> 

<img src="Images/L4_2_2_Waveform.PNG">

#### Figure 4.2.3 Waveform<br /> 

Waveform clearly shows that change in output depends only on change in sel & if change in io is no reflected 
<br /> 
<br />
<br /> 

<img src="Images/L4_2_3_Synthesis_Step_1.PNG">

#### Figure 4.2.4 Synthesis<br /> 

Invoking yosys for synthesis & reading the input files 
<br /> 
<br />
<br /> 

<img src="Images/L4_2_4_Synthesis_Step_2.PNG">

#### Figure 4.2.5 Synthesis<br /> 

After synthesis is performed , it reports with the cell(type&number) that is taken to build netlist
<br /> 
<br />
<br /> 

<img src="Images/L4_2_5_Synthesis_Step_5.PNG">

#### Figure 4.2.6 Synthesis<br /> 

Dumping the netlist & displaying the implementing design
<br /> 
<br />
<br /> 

<img src="Images/L4_2_6_NL_TB_in_GTK.PNG">

#### Figure 4.2.7 GLS<br /> 

Performing GLS using primitives & verilog models for standard cell using the netlist dump at previous step with the same testbench which was used for RTL simulation 
<br /> 
<br />
<br /> 

<img src="Images/L4_2_7_GLS_output.PNG">

#### Figure 4.2.8 GLS Output<br /> 

Above waveform correctly shows the behaviour of MUX but on comparison with the waveform at RTL level we see there is a mismatch.
Here the change in Io is clearly seen at the output if if the sel of the MUX is not changing but when it comes to RTL level due to wrong sensitivity list the output of the MUX is only changing at sel
<br /> 
<br /> 
*Note* : Above lab experiments shows that wrong sensitivity list can cause GLS simulation mismatch
<br /> 
<br /> 
#### Lab Part-2  Synth-Sim Mismatch for Blocking Statement<br />
<br /> 
<br /> 
#### Design 3: Blocking Caveat Design    

<img src="Images/L4_3_0_RTL_blocking_caveat.PNG">

#### Figure 4.3.1 Verilog Model<br /> 

Above is the example of blocking statements used in the RTL design 
<br /> 
<br />
<br /> 

<img src="Images/L4_3_1_Open_GTK.PNG">

#### Figure 4.3.2 Performing Simulation<br /> 

iverilog command is used to dump the VCD (value change dump) & VCD is analysed using GTKwave
<br /> 
<br />
<br />

<img src="Images/L4_3_2_Waveform.PNG">

#### Figure 4.3.3 Waveform<br /> 

O/p is wrong , D cannot be 1 , so clearly it is looking at past values. Looking as if there is a flop here
<br /> 
<br />
<br />

<img src="Images/L4_3_3_Synthesis_Step_1.PNG">

#### Figure 4.3.4 Synthesis<br /> 

Invoking yosys for synthesis & reading the input files 
<br /> 
<br />
<br /> 

<img src="Images/L4_3_4_Synthesis_Step_2.PNG">

#### Figure 4.3.5 Synthesis<br /> 

After synthesis is performed , it reports with the cell(type&number) that is taken to build netlist
<br /> 
<br />
<br /> 

<img src="Images/L4_3_5_Sythesis_Step_5.PNG">

#### Figure 4.3.6 Synthesis<br /> 

After synthesis is performed , it reports with the cell(type&number) that is taken to build netlist
<br /> 
<br />
<br /> 

<img src="Images/L4_3_6_NL_TB_in_GTK.PNG">

#### Figure 4.3.7 GLS<br /> 

Performing GLS using primitives & verilog models for standard cell using the netlist dump at previous step with the same testbench which was used for RTL simulation 
<br /> 
<br />
<br /> 

<img src="Images/L4_3_7_Synthesis_output.PNG">

#### Figure 4.3.8 GLS Output<br /> 

@RTL level : a=0,b=0,c=1 O/p d=1
@NL level  : a=0,b=0,c=1 O/p d=0 which clearly shows that the there is a GLS mismatch
<br />
<br /> 
*Note* : Above lab experiment shows that block statements can cause GLS mismatch. hence it recommended to use non-blocking statement
<br />
<br /> 
#### Design 4: Shift Register using Non-Blocking Statment  

<img src="Images/L4_4_Shift_reg_3.PNG">

#### Figure 4.4.1<br /> 

<img src="Images/L4_4_Shift_reg_3_results.PNG">

#### Figure 4.4.2<br /> 
<br />
<br /> 
#### Design 5: Shift Register using Blocking Statment  

<img src="Images/L4_4_Shift_reg_4.PNG">

#### Figure 4.5.1<br /> 

<img src="Images/L4_4_Shift_reg_4_results.PNG">

#### Figure 4.5.2<br /> 
<br />
<br /> 
*Note* : Above 2 lab experiment shows how blocking & non-blocking statements can cause hardware change
<br />
<br /> 









