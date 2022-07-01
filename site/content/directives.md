+++
date = 2022-06-08T02:18:16Z
hiddenFromHomePage = false
postMetaInFooter = false
title = "Directives"
[flowchartDiagrams]
enable = false
options = ""
[sequenceDiagrams]
enable = false
options = ""

+++
# Note

## Destination

* Use \[Source File\] to add the pragmas inline to the source code
* Use \[Directive File\] to add the pragmas into the solution's `directives.tcl` constraints file

![](/uploads/snipaste_2022-06-08_12-19-31.png)

## Interface Directive

![](/uploads/snipaste_2022-06-09_20-45-03.jpg)

> For block-level I/O protocols, the return argument is used to specify the block-level interface. This is true even if the function has no return argument in the source code.

Note: The RTL CoSimulation feature requires a block-level I/O protocol to sequence the test bench and RTL design for CoSimulation automatically. Any attempt to use RTL CoSimulation results in an error

***

# Pipeline Directive

![](/uploads/snipaste_2022-06-09_22-33-59.jpg)

* When the top-level of the design is a loop, you can use the pipeline rewind option. This informs Vivado HLS that when implemented in RTL, this loop runs continuously (with no end of function and function re-start cycles).

***

# Task Pipelining

`#pragma HLS dataflow`