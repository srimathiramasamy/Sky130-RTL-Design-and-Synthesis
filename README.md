# Sky130-RTL-Design-and-Synthesis
This is a doccumentation of the five day workshop on "RTL DESIGN USING VERILOG USING SKY130 TECHNOLOGY"
This repository includes the design and synthesis of RTL codes with the use of tools such as iverilog, yosys and gtkwave.

![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/Capture.PNG)

## Table of contents
- [DAY -1 ](#Day -1)
  * [Simulator - iverilog](#SImulator - iverilog)
  * [LAP SETUP](#LAB SETUP)
  * [gtkwave](#gtkwave)
  * [sky130 libraries](#sky130-libraries)
  * [yosys](#yosys)
- [DAY -2 ](#Modelling-Techniques)
  * [Sensitivity List for Combinational Logic](#Sensitivity-List-for-Combinational-Logic)
  * [Modelling Flip Flops](#Modelling-Flip-Flops)
- [DAY -3 ](#Synthesis-Techniques)
  * [Hierarchial Synthesis](#Hierarchial-Synthesis)
  * [Flat Synthesis](#Flat-Synthesis)
  * [Submodule Level Synthesis](#Submodule-Level-Synthesis)
- [DAY -4](#Beauty-of-Optimizations)
  * [Synthesizing Multipliers](#Synthesizing-Multipliers)
  * [Combinational Logic Optimization](#Combinational-Logic-Optimization)
  * [Sequential Logic Optimization](#Sequential-Logic-Optimization)
  * [Unuesd Output Optimization](#Unuesd-Output-Optimization)
- [DAY -5](#Gate-Level-Simulation-(GLS))
  * [Incomplete Sensitivity List](#Incomplete-Sensitivity-List)
  * [Blocking Assignments](#Blocking-Assignments)
 
 ## DAY -1
 The first day of the workhop covers the simaulation part of the RTL design alonng with the brief description about the usage of the tools such as iverilog, gtkwave and yosys. It also provides the detailed note on the sky130 library used. 
 There are many open source tools available for the front-end RTL design. The list of tools used in this repo are mentioned below

## LAB SETUP
 
 *create a directory called 'VLSI' in the home path
 *install the vsdflow
 a directory called vsdflow is created and the required files are clones  
 
 $mkdir VLSI
 $cd VLSI
 $ls
 
 *git clone 
 
 $git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorksop.git
 
directory sky130RTLDesignAnd SynthesisWorshop gets created

files present in the directory

 
 ![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/1.1.PNG)
 
 
 ##gtkwave - waveform viewer
 
 The tool for viewing the waveform is gtkwaveform viewer, where the window pops up containing the stimulus where the functionality of the RTL design can be justified.
 
 ![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/gtk1.PNG)
 
 files present in the directories cloned
 
 ![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/1.4.PNG)
 ![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/1.5.PNG)
 
 sky130 library will be used for the synthesis
 
 verilog files conatins all the source and the testbench files which will be used for the lab
 
 [github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/1.6.PNG)
 [github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/1.7.PNG)

## Simulator - iverilog
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
  
  [github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/1.6.PNG)
  
  $ls // views all the files present in the current working directory
  
  *simulation of the RTL code
  
 [github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/1.9.PNG)
 
 $iverilog designfile testbenchfile
 $ls
 $./a.out
 
 *gtkwaveform viewer
 
 [hithub-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/1.10.PNG)
 
 $gtkwave testbenchfile.vcd
 
 
 
 
 
