+++
date = 2022-07-27T03:10:39Z
hiddenFromHomePage = false
postMetaInFooter = false
title = "Seminar: Packet Processing"
[flowchartDiagrams]
enable = false
options = ""
[sequenceDiagrams]
enable = false
options = ""

+++
* FPGAs are fast and dynamic

***

# Packet Parsing Language

* High-level languages for describing FPGA circuits - high throughputs (400 Gbps)
* Protocol-agnostic
* Domain-specific - no loops or other control-flow - only simple arithmetic and if/then/else

![](/uploads/snipaste_2022-07-27_13-14-06.jpg)

***

# Packet Parsing Architecture

* Uses the cut-through forwarding method (as compared to store-and-forward)
* Heavily pipelined

## Stages

Each stage consumes \[header type\], \[data offset\], \[partial key\]

![](/uploads/snipaste_2022-07-27_13-21-36.jpg)

![](/uploads/snipaste_2022-07-27_13-21-54.jpg)