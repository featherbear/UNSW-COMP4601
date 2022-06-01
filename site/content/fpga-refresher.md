+++
date = 2022-06-01T02:38:38Z
hiddenFromHomePage = false
postMetaInFooter = false
title = "FPGA Refresher"
[flowchartDiagrams]
enable = false
options = ""
[sequenceDiagrams]
enable = false
options = ""

+++
![](/uploads/snipaste_2022-06-01_12-38-01.jpg)

The FPGA composes of an arrangement of slices and routing components

![](/uploads/snipaste_2022-06-01_12-41-51.jpg)  
Modern FPGAs have additional specific resources for speeding up certain operations.  
e.g. DSP slices, block RAM, microprocessors, AXI interfaces, high-speed transceivers, clock managers, etc..

#### DSP Slice

![](/uploads/snipaste_2022-06-01_12-44-21.jpg)

#### Block RAM

![](/uploads/snipaste_2022-06-01_12-47-36.jpg)

> What if you write different data into both ports to the same destination?

#### Memory Choices

![](/uploads/snipaste_2022-06-01_12-50-38.jpg)

#### Design Bases

* Core-based Design Methodology
  * Custom cores + other provided cores
* Platform-based Design Methodology
  * Standard design templates that combine a stable, verified composition of standard cores and IO cores targetting a particular board
  * Enabled a programmer to integrate algorithms (aka 'roles') provided by a platform (aka 'shell').