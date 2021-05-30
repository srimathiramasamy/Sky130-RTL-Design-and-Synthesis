# Sky130-RTL-Design-and-Synthesis
This is a doccumentation of the five day workshop on "RTL DESIGN USING VERILOG USING SKY130 TECHNOLOGY"
This repository includes the design and synthesis of RTL codes with the use of tools such as iverilog, yosys and gtkwave.

![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/Capture.PNG)

## Table of contents
-[DAY 1](#DAY-1)
* [LAB SETUP](#LAB-SETUP)
* [gtkwave waveform viewer](#gtkwave-waveform-viewer)
* [Simulator iverilog](#Simulator-iverilog)
* [YOSYS](#YOSYS)
* [LIBRARY FILES](#LIBRARY-FILES)


















 ## DAY 1
 The first day of the workhop covers the simaulation part of the RTL design alonng with the brief description about the usage of the tools such as iverilog, gtkwave and yosys. It also provides the detailed note on the sky130 library used. 
 There are many open source tools available for the front-end RTL design. The list of tools used in this repo are mentioned below

## LAB SETUP
 
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
 
 
 ## gtkwave waveform viewer
 
 The tool for viewing the waveform is gtkwaveform viewer, where the window pops up containing the stimulus where the functionality of the RTL design can be justified.
 
 ![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/gtk1.PNG)
 
 files present in the directories cloned
 
 ![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/1.4.PNG)
 ![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/1.5.PNG)
 
 sky130 library will be used for the synthesis
 
 verilog files conatins all the source and the testbench files which will be used for the lab
 
 [github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/1.6.PNG)
 [github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/1.7.PNG)

## Simulator iverilog
   Design is the set of verilog codes which intends to meet the specifications. The testbench is the setup appied to the desing with a set of test vector to check working of thedesign module.
   Simulator plays an important role in verifying the design by providing the different input stimulus to the design at different times to check the proper fuunctioning of the RTL code as mentioned in the specifications.  THere are various verilog simulators availabe such as 
* iverilog
* Modelsim
* Questa Sim
* Xilinx Simulator (XSIM)
* MPSim
* ISE Simulator

In this repo we have used the "IVERILOG" for out RTL code simulation.

### Working of the simulator
 It mainly relays on the change in the input. If there are is no change in the input test vector then there will be no chnage in the output, the simulator will not eveluate the output in this condition.
 
 ![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/123.PNG)
 
 The primary inputs given to the testbench where the design is instantiated from the stimulus generator and the outputs are verified by the stimulus observer, the testbench doesnot have primary input and primary output
 
 ### iverilog simulation flow
 
 The output of the simulator is a .vcd file where vcd stands for value change dump. The simulator looks for changes in the input testvector hence the format .vcd occurs.
 
 ![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/2.PNG)
 
 ### LAB
  
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

##YOSYS

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

## LIBRARY FILES
.lib is the collection of all the standard cell. contains various versions of the same gates (slow, fast, medium speed). It will be rich enough to implement any logic function. The requirement of different flavors of gates is due to the combinational delay of the logic circuit determines the speed of the circuit.

![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/2.2.PNG)

tclk > the propagation of flop a + combinational delay + setup time of flop b
fclk=1/tclk

tclk is the minimum clk period needed and fclk will be the maximum clk frequency. For the maximum performance the delay should be minimum, this can be acheived by faster cells which eliminates the requirement of the medium and slow cells.

### Requirement of Slow cells 

To ensure the absence of hold related time issues in the flop b there is requiremtn of slow cells, where the delay should be minimum. Thus we require fast cells to meet the performance and slow cells to meet the hold. The load in the circuits is the capacitor, the faster the charging and the discharging the faster the circuit operates.
* wider transistors provide low delay - more area and power consumption
* narrow transistors provide more delay - less area and power consumption

more use of slow cells - sluggish performcne
more use of fast cells - hold violationns

## DAY - 2

 
### Hierachial and flat synthesis

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

## FLIPFLOP CODING STYLES



![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/3331.PNG)

![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/3.1.PNG)

![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/3.2.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/3.3.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/3.4.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/3.5.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/3.6.PNG)
![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/3.7.PNG)


### OPTMIZATIONS OF DESING MODULES

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

## LAB FOR for Sequential Optimizations for unused inputs

