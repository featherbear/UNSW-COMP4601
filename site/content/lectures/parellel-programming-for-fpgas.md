+++
date = 2022-06-01T01:50:07Z
draft = true
hiddenFromHomePage = false
postMetaInFooter = false
title = "Parellel Programming for FPGAs"
[flowchartDiagrams]
enable = false
options = ""
[sequenceDiagrams]
enable = false
options = ""

+++
* VHDL and Verilog are used to specify design at RTL (register transfer level)
  * RTL -> Logic that leads to a final value
* HLS (High-level Synthesis) allows for the generation of RTL designs through high level code (i.e. C code). We don't need to include specific registers or cycles

### How to we improve performance?

* Parallelisation
  * Pipelining
* Larger bus size
* Higher clock speed
* Better algorithms with better time efficiency

### HLS

> \[C program\] --HLS--> \[RTL VHDL/Verilog\]

* Analyses and exploits concurrency in the algorithm
* Inserts registers as necessary to limit critical paths and achieve a desired clock frequency
* Generates control logic for data paths
* Implements interfaces to connect to the rest of the system
* Maps data onto storage elements to balance resource usage and bandwidth
* Maps computations onto logic elements using a combination of automatic and user-specific automations

#### Advantages

* Can deal with a variety of interfaces
  * DMA
  * Streaming
  * On-chip memory
* Can perform advanced optimisations to create efficient implementations
  * Pipelining
  * Memory partitioning
  * Bit-width optimisation

#### Limitations

* Can't handle arbitrary code
* Software components may be difficult to implement in hardware
  * Dynamic memory
  * Recursion
  * Standard libraries
  * System calls

#### Requirements

* A function in C / C++ / SystemC
* Target FPGA device
* Desired clock period
* Implementation directives
* (optional) A testbench

#### Some Tools

![](/uploads/snipaste_2022-06-01_12-13-29.jpg)

***

### Vivado HLS Input Functions

* No dynamic memory (i.e. no `malloc`, `free`)
* Limited pointer usage*
* System calls not supported
  * (Can be used in the testbench, since it's not synthesised)
* Limited use of other standard libraries
  * Some work
* No function pointers or virtual functions
* No recursive function calls
* Interface must be precisely defined

### Vivado HLS Output Functions

* Synthesisable VHDL or Verilog
  * Not human readable
* Simulations based on the testbench
* Static analysis of the performance and resource usage
* Metadata at the boundaries of a design