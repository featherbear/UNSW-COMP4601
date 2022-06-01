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

# The modern FPGAs can only operate at 1GHz speeds? Why use a FPGA then????

Think of performance in 'task time in seconds' rather than clock speed.  
Higher clock speeds do not mean that it is faster.

In FPGA designs we can parallelise things more than a generic CPU instruction can.  
_See below_

***

## One Tap Per Clock

![](/uploads/snipaste_2022-06-01_13-20-07.jpg)  
Critical Path: 1 mult + 1 adder  
Task Latency: 4 cycles

## One Sample Per Clock

![](/uploads/snipaste_2022-06-01_13-20-51.jpg)  
Critical Path: 1 mult + 2 adder  
Task Latency: 1 cycle

***

# Speed Limits

The task interval is limited by **recurrences** (feedback loops) and **resource limits**

Recurrence - where a computation by a component depends on the previous computation by the same component

* i.e. see the above multiplier and adder example
* These limit the throughput even when pipelining

It's important to restructure the code to maximise the performance of the HLS tool.