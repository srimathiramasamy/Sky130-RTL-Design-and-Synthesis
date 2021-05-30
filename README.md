# Sky130-RTL-Design-and-Synthesis
This is a doccumentation of the five day workshop on "RTL DESIGN USING VERILOG USING SKY130 TECHNOLOGY"
This repository includes the design and synthesis of RTL codes with the use of tools such as iverilog, yosys and gtkwave.

![github-small](https://github.com/srimathiramasamy/Sky130-RTL-Design-and-Synthesis/blob/main/Capture.PNG)

## Table of contents
- [DAY -1 ](#Day -1)
  * [Simulator - iverilog](#SImulator - iverilog)
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
