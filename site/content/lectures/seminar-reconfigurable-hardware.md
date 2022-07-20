+++
date = 2022-07-20T01:51:14Z
hiddenFromHomePage = false
postMetaInFooter = false
title = "Seminar: Reconfigurable Hardware"
[flowchartDiagrams]
enable = false
options = ""
[sequenceDiagrams]
enable = false
options = ""

+++
# Hardware

* Coupling
* Granularity
  * For a 3-bit operation
    * 3-bit device will be great
    * 8-bit device will have overhead
  * For an 8-bit operation
    * 3-bit device will be inefficient
    * 8-bit device will be great
* Heterogeneous Arrays
  * Base versions of multipliers
* Routing resources
* Segmented pathing with switch boxes to emulate longer wires

  ![](/uploads/snipaste_2022-07-20_11-55-38.jpg)
* Hierarchical pathing

  ![](/uploads/snipaste_2022-07-20_11-56-01.jpg)
* Structured dimensions
  * One dimension designs are simpler and faster
    * Routing abit harder
    * Better for simpler connections
  * Two dimension designs are more complex (more placement options?
    * Routing easier
* Multi-FPGA systems
  * Mesh - better computation
  * Crossbar / SPLASH 2 - better speed