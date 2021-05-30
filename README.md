# Sky130-RTL-Design-and-Synthesis
This is a doccumentation of the five day workshop on "RTL DESIGN USING VERILOG USING SKY130 TECHNOLOGY"
This repository includes the design and synthesis of RTL codes with the use of tools such as iverilog, yosys and gtkwave.

![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/Capture.PNG)

## Table of contents
--[DAY 1](#DAY-1)
* [LAB SETUP](#LAB-SETUP)
* [gtkwave waveform viewer](#gtkwave-waveform-viewer)
* [Simulator iverilog](#Simulator-iverilog)
* [YOSYS](#YOSYS)
* [LIBRARY FILES](#LIBRARY-FILES)

--[DAY 2](#DAY-2)
* [HIERACHIAL AND FLAT SYNTHESIS](#HIERACHIAL-AND-FLAT-SYNTHESIS)
* [FLIP FLOP CODING STYLES](#FLIP-FLOP-CODING-STYLES)

--[DAY 3](#DAY-3)
* [COMBINATIONAL LOGIC OPTIMIZATION](#COMBINATIONAL-LOGIC-OPTIMIZATION)
* [SEQUENTIAL LOGIC OPTIMIZATION](#SEQUENTIAL-LOGIC-OPTIMIZATION)
* [SEQUENTIAL LOGIC OPTIMIZATION FOR UNUSED OUTPUTS](#SEQUENTIAL-LOGIC-OPTIMIZATION-FOR-UNUSED-OUTPUTS)

--[DAY 4](#DAY-4)
* [GLS SYNTHESIS AND SIMULATION MISMATCH](#GLS-SYNTHESIS-AND-SIMULATION-MISMATCH)
* [GLS LAB](#LAB-GLS)

--[DAY 5](#DAY-5)
* [IF CASE CONSTRUCTS](#IF-CASE-CONSTRUCTS)
* [LAB FOR IF CASE](#LAB-FOR-IF-CASE)
* [FOR LOOP AND FOR GENERATE](#FOR-LOOP-AND-FOR-GENERATE)
* [LAB FOR LOOP AND FOR GENERATE](#LAB-FOR-LOOP-AND-FOR-GENERATE)

--[ACKNOWLEDGEMENT](#ACKNOWLEDGEMENT)

 ## DAY 1
 The first day of the workhop covers the simaulation part of the RTL design alonng with the brief description about the usage of the tools such as iverilog, gtkwave and yosys. It also provides the detailed note on the sky130 library used. 
 There are many open source tools available for the front-end RTL design. The list of tools used in this repo are mentioned below

### LAB SETUP
 
 * create a directory called 'VLSI' in the home path
 * install the vsdflow
 a directory called vsdflow is created and the required files are clones  
 
```
 mkdir VLSI
 cd VLSI
 ls
```
 
 * git clone 
 ```
 git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorksop.git
 ```
directory sky130RTLDesignAnd SynthesisWorshop gets created

files present in the directory

 
 ![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/1.1.PNG)
 
 
 ### gtkwave waveform viewer
 
 The tool for viewing the waveform is gtkwaveform viewer, where the window pops up containing the stimulus where the functionality of the RTL design can be justified.
 
 ![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/gtk1.PNG)
 
 files present in the directories cloned
 
 ![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/1.4.PNG)
 ![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/1.5.PNG)
 
 sky130 library will be used for the synthesis
 
 verilog files conatins all the source and the testbench files which will be used for the lab
 
 ![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/1.6.PNG)
 ![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/1.7.PNG)

### Simulator iverilog
   Design is the set of verilog codes which intends to meet the specifications. The testbench is the setup appied to the desing with a set of test vector to check working of thedesign module.
   Simulator plays an important role in verifying the design by providing the different input stimulus to the design at different times to check the proper fuunctioning of the RTL code as mentioned in the specifications.  THere are various verilog simulators availabe such as 
* iverilog
* Modelsim
* Questa Sim
* Xilinx Simulator (XSIM)
* MPSim
* ISE Simulator

In this repo we have used the "IVERILOG" for out RTL code simulation.

#### Working of the simulator
 It mainly relays on the change in the input. If there are is no change in the input test vector then there will be no chnage in the output, the simulator will not eveluate the output in this condition.
 
 ![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/123.PNG)
 
 The primary inputs given to the testbench where the design is instantiated from the stimulus generator and the outputs are verified by the stimulus observer, the testbench doesnot have primary input and primary output
 
 #### iverilog simulation flow
 
 The output of the simulator is a .vcd file where vcd stands for value change dump. The simulator looks for changes in the input testvector hence the format .vcd occurs.
 
 ![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/2.PNG)
 
 #### LAB
  
  list of verilog files available for lab
  
  ![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/1.6.PNG)
  
  ```
  ls // views all the files present in the current working directory
  ```
  
  * simulation of the RTL code
  
 ![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/1.9.PNG)
 ```
  iverilog designfile testbenchfile
  ls
  ./a.out
 ```
 * gtkwaveform viewer
The inputs and the outputs can be dragged and dropped in the viewer. To see the entire observation on the single window click zoomfit. To look for the transition of the signal use the arrow for forward and the backward transitions. This can be used for the evaluation of the design.
 
 ![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/1.10.PNG)
 
 ```
gtkwave testbenchfile.vcd
```
 
 ![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/gtk1.PNG)
  
  The waveform viewer depicts the functionality of the desing with respect to the stimulus provided.
  
  we have used the multipler code for the simulation.If there is select output follows input1 and if there is no select the output folows input0
  
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/1.12.PNG)
  
  Testbench for the multiplexer : the testbench instantiates the design
  dut stands for design under test
  
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/1.11.PNG)

### YOSYS

Synthesizer is the tool which converts the RTL to the netlist. In this flow we use yosys as the synthesizer.

![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/Y1.PNG)

The design along with the library file is given to the synthesizer tool and the netlist is generated from it.
Netlist is the representation of the design in terms of standard cell in the .lib, the design is made into gates and the connections are made into gates

To verify the synthesis output - provide the netlist along with the testbench to the iverilog (verilog simulator) and check the .vcd file with the gtkwaveform viewer to monitor the functionality of the design, the functionality should remain the same as the ouput RTL simulation.
The primary inputs and the ouput remains same thus the same testbench can be used.

![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/2.1.PNG)
commands -
* invoke yosys
* read the library with the relative path
* read the design (successfully done should come)
* synth -top moduletosynthesis
* generate the netlist (abc -converts the RTL to gate specified in the library)
* show - graphical version of the logic realized
```
yosys
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd_tt_025C_1v80.lib
read_verilog designmodule.v
synth -top modulename
abc -liberty ../my_lib/lib/sky130_fd_sc_hd_tt_025C_1v80.lib
show
exit
```

fd-foundary
tt - typical
025C-temperature
1v80-voltage
PVT - Process Voltage Temperature

!github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/1.13.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/1.14.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/1.15.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/1.16.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/1.17.PNG)
provides the informantion regarding the internal wires, memory, inputs and the ouputs
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/1.18.PNG)

mux realied in terms of the library mentioned.

![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/22.PNG)

### LIBRARY FILES
.lib is the collection of all the standard cell. contains various versions of the same gates (slow, fast, medium speed). It will be rich enough to implement any logic function. The requirement of different flavors of gates is due to the combinational delay of the logic circuit determines the speed of the circuit.

![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/2.2.PNG)

tclk > the propagation of flop a + combinational delay + setup time of flop b
fclk=1/tclk

tclk is the minimum clk period needed and fclk will be the maximum clk frequency. For the maximum performance the delay should be minimum, this can be acheived by faster cells which eliminates the requirement of the medium and slow cells.

#### Requirement of Slow cells 

To ensure the absence of hold related time issues in the flop b there is requiremtn of slow cells, where the delay should be minimum. Thus we require fast cells to meet the performance and slow cells to meet the hold. The load in the circuits is the capacitor, the faster the charging and the discharging the faster the circuit operates.
* wider transistors provide low delay - more area and power consumption
* narrow transistors provide more delay - less area and power consumption

more use of slow cells - sluggish performcne
more use of fast cells - hold violationns

## DAY - 2

 
### HIERACHIAL AND FLAT SYNTHESIS

* submodule2

![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/31.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/40.PNG)
```
gedit multiple_module.v
```
submodule1 - and gate
submodule2 - or gate
multiple module -instantiation of submodules
* multiple module
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/32.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/33.PNG)

```
yosys
read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd_tt_025C_1v80.lib
read_verilog multiple_module.v
synth -top multiple_module
abc -liberty ../my_lib/lib/sky130_fd_sc_hd_tt_025C_1v80.lib
show
exit
```
```
write_verilog -noattr multiple_module_hier.v
gedit multiple_module_hier.v
```
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/34.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/35.PNG)

The hierachail desing is preserved.
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/hie.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/37.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/38.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/39.PNG)


```
flaten
```

![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/36.PNG)

### FLIP FLOP CODING STYLES



![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/3331.PNG)

![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/3.1.PNG)

![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/3.2.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/3.3.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/3.4.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/3.5.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/3.6.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/3.7.PNG)


### COMBINATIONAL LOGIC OPTIMIZATION

![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/4.1.PNG)

![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/4.2.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/4.3.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/4.4.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/4.5.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/4.6.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/4.7.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/4.8.PNG)

![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/4.9.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/4.10.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/4.11.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/4.12.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/4.13.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/4.14.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/4.15.PNG)

![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/4.16.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/4.17.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/4.18.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/4.19.PNG)

### SEQUENTIAL LOGIC OPTIMIZATION

dff_const1 - flop present, reset (when reset occurs q=0, else q=1)
removal of reset does not sets q=1 it waits for the clk
(it does not act like inverter)

dff_const2 - flop present, if reset occurs (acts as set) q=1, d also tied to 1, if reset removed it remains in logic 1 after clock it sustains in logic 1

dff_const3 - two flops preset (same clk and reset), q=1'b1 on reset, q1=1'b0 on reset and on else part d logic defined q=q1, q1=q

##### LAB SIMULATION
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/3.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/4.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/5.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/6.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/7.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/8.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/9.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/10.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/11.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/12.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/13.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/14.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/15.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/16.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/17.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/18.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/19.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/20.PNG)


### SEQUENTIAL LOGIC OPTMIZATION FOR UNUSED OUPUTS

reset - goes to 0 otherwise it is a upcouter ( 000 - 111 )
it is a three bit up - conter
senses only one output other two are unsued 
there is only on flop present

counter_opt2
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/21.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/22.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/23.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/24.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/25.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/26.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/27.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/28.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/29.PNG)


## DAY 4

GLS stands for gate level simulation. RTL code validated by testing as per the specifications. 
Run the testbench in the GLS with the netlist as the design under test, as the netlist wil be fit in the place of the RTL code as both meets the same.

Why run GLS?
To verify the logical correctness of the design after synthesis
During simulation there is notion of timing, but for the desing to work the timing playa a key role it should be met.
The GLS should be run with the delay annotation.

#### GLS USING IVERILOG

The desing is the netlist, we need to read the gate level verilog models in addtion to the regular steps in the part of simulation including the design, testbench, gtkwave form viewer.

### GLS SYNTHESIS AND SIMULATION MISMATCH

Major reasons are
* missing sensitivity list
* blocking and non - blocking assignments
* non - standard verilog coding

#### MISSING SENSITIVITY LIST

In verilog simulator works based on activity of the change in the inputs, no activity the output is not evaluated. 
In a MUX is evaluated only when the select is changing it also concerns the process,
when the select is low activity on input0
when the select is high activity on input1
during RTL simulation it looks like a latch as the entire process depends on the select  line in the mux.
 The correct way of the code is :
 
 ```
 module mux(input i0, input i1, input sel,output reg y)
 always@(*)
 begin
 if(sel)
 y=i1;
 else
 y=i0;
 end
 endmodule
 ```
#### BLOCKING AND NON - BLOCKING ASSIGNMENTS

The blocking and non - blocking comes under picture when we use always block.
Blocking statement - It executes in the order of statement written.
Non - Blocking statement - it is mostly parallel evaluation of the statements. It executes the RHS and assigns to the LHS, the order does'nt matters here.


### GLS LAB
Requiremnet - 
* netlist
* verilog models
* testbench
Working of the ternary operator
```
<condition>?(true>:<false>
assign y=sel?i0:i1; //implement the mux

```

![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/l41.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/l42.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/l43.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/l44.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/l45.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/l46.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/l47.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/l48.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/l49.PNG)

![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/4b1.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/4b2.PNG)


## DAY 5

### IF CASE CONSTRUCTS
If statement is mainly used to create priority logc

```
if(condtion1)
code
elseif(condition2)
code
else
code
```
the condition1 has the most priority followed by the seconf condition

if - danger/caution
* inferrred latches (latches are not intended)
this occurs due to bad coding styles (incmplete if statements)

```
if(c1)
y=a;
elseif(c2)
y=b;
.
.
```
if neither the consitons does not happen it tries to retain the values of the output thus the latches are inferred in such cases.

### LAB FOR IF CASE

```
module incomp_if (input i0 , input i1 , input i2 , output reg y);
always @ (*)
begin
	if(i0)
		y <= i1;
end
endmodule
```
it is a d latch (positive latch)

```
module incomp_if2 (input i0 , input i1 , input i2 , input i3, output reg y);
always @ (*)
begin
	if(i0)
		y <= i1;
	else if (i2)
		y <= i3;

end
endmodule
```

```
read_liberty -lib /my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog incomp_if.v
synth -top incmp_if
abc -liberty lib /my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```


```
module comp_case (input i0 , input i1 , input i2 , input [1:0] sel, output reg y);
always @ (*)
begin
	case(sel)
		2'b00 : y = i0;
		2'b01 : y = i1;
		default : y = i2;
	endcase
end
endmodule
```

depending on the select the values are assigned, there occurs a latchign condtion

```
module incomp_case (input i0 , input i1 , input i2 , input [1:0] sel, output reg y);
always @ (*)
begin
	case(sel)
		2'b00 : y = i0;
		2'b01 : y = i1;
	endcase
end
endmodule
```

### FOR LOOP AND FOR GENERATE

* for loop - used inside always
* generate followed by for loop - used outside always
Generate for loop is used for instantiate the hardware multiple times. The plain for loop used in always is used for evaluating expressions

### LAB FOR LOOP AND FOR GENERATE

```
module mux_generate (input i0 , input i1, input i2 , input i3 , input [1:0] sel  , output reg y);
wire [3:0] i_int;
assign i_int = {i3,i2,i1,i0};
integer k;
always @ (*)
begin
for(k = 0; k < 4; k=k+1) begin
	if(k == sel)
		y = i_int[k];
end
end
endmodule
```

demux in terms of case and loop statements

```
module demux_case (output o0 , output o1, output o2 , output o3, output o4, output o5, output o6 , output o7 , input [2:0] sel  , input i);
reg [7:0]y_int;
assign {o7,o6,o5,o4,o3,o2,o1,o0} = y_int;
integer k;
always @ (*)
begin
y_int = 8'b0;
	case(sel)
		3'b000 : y_int[0] = i;
		3'b001 : y_int[1] = i;
		3'b010 : y_int[2] = i;
		3'b011 : y_int[3] = i;
		3'b100 : y_int[4] = i;
		3'b101 : y_int[5] = i;
		3'b110 : y_int[6] = i;
		3'b111 : y_int[7] = i;
	endcase

end
endmodule

```

```
module demux_generate (output o0 , output o1, output o2 , output o3, output o4, output o5, output o6 , output o7 , input [2:0] sel  , input i);
reg [7:0]y_int;
assign {o7,o6,o5,o4,o3,o2,o1,o0} = y_int;
integer k;
always @ (*)
begin
y_int = 8'b0;
for(k = 0; k < 8; k++) begin
	if(k == sel)
		y_int[k] = i;
end
end
endmodule
```

There is no always statement here in the code, there are seven full adders instantiated here

```
module rca (input [7:0] num1 , input [7:0] num2 , output [8:0] sum);
wire [7:0] int_sum;
wire [7:0]int_co;

genvar i;
generate
	for (i = 1 ; i < 8; i=i+1) begin
		fa u_fa_1 (.a(num1[i]),.b(num2[i]),.c(int_co[i-1]),.co(int_co[i]),.sum(int_sum[i]));
	end

endgenerate
fa u_fa_0 (.a(num1[0]),.b(num2[0]),.c(1'b0),.co(int_co[0]),.sum(int_sum[0]));


assign sum[7:0] = int_sum;
assign sum[8] = int_co[7];
endmodule
```

From the five day worksop the RTL Design and Syntheis is very clear regarding all the theoretical concepts as well as the practical concepts. Concepts regarding the simulator, waveform viewer and synthsis are practically implmented in the lab sessions, along with various design modules and testbench. The generation of the netlist and the analysis of the standard library is implemented. It provided a analysis on the design module regarding the functionality and the timing.

##ACKNOWLEDGEMENT

1. Kunal Ghosh - Co-founder(VSD Corp. Pvt. Ltd)
2. Shon Taware - VSD Teaching Assistant
