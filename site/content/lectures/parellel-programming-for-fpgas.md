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

#### How to we improve performance?

* Parallelisation
  * + Pipelining
* Larger bus size
* Higher clock speed
* Better algorithms with better time efficiency