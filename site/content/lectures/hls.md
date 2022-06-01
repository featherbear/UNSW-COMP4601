+++
date = 2022-06-01T03:06:11Z
hiddenFromHomePage = false
postMetaInFooter = false
title = "HLS"
[flowchartDiagrams]
enable = false
options = ""
[sequenceDiagrams]
enable = false
options = ""

+++
# Example - FIR Filter

A Finite Impulse Response filter performs a convolution on an input sequence with a fixed set of coefficients

The HLS tool will analyse the code and produce a functionally equivalent RTL circuit

Note: This course doesn't go in detail of how the transpilation works - but is beneficial to understand to take advantage of memory layouts, pipelines, etc

![](/uploads/snipaste_2022-06-01_13-07-11.jpg)

***

Vivado HLS generates an optimised, but largely sequential architecture 

* Loops and branches are transformed into control logic
* Conceptually similar to the execution of a RISC processor
  * But the program needs to be converted to an FSM in the RTL rather than being fetched from memory
* A sequential architecture tends to limit the number of functional units in a design with a focus on resource sharing over massive parallelism

> The modern FPGAs can only operate at 1GHz speeds

***

![](/uploads/snipaste_2022-06-01_13-20-07.jpg)  
Critical Path: 1 mult + 1 adder  
Task Latency: 4 cycles

![](/uploads/snipaste_2022-06-01_13-20-51.jpg)  
Critical Path: 1 mult + 2 adder  
Task Latency: 1 cycle