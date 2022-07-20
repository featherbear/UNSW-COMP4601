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

***

# Software

## Manual Systems

> Yes just design the FPGA chip yourself.

Better precision, but need advanced knowledge

## Automated Systems

Eh

***

## Stages

### Circuit Specification Stage

#### Manual

* Hand mapping of the blocks at gate level

#### Semi-Automated

* Using structural circuit description language
* Generic components
* Requires knowledge of the target

#### Automated

* Use a high level language (C, C++, Java)
* Specify the logic rather than the block design

### Mapping Stage

![](/uploads/snipaste_2022-07-20_12-03-38.jpg)

### Placement Stage

![](/uploads/snipaste_2022-07-20_12-03-59.jpg)  
![](/uploads/snipaste_2022-07-20_12-04-12.jpg)

### Routing Stage

![](/uploads/snipaste_2022-07-20_12-05-10.jpg)

***

![](/uploads/snipaste_2022-07-20_12-06-08.jpg)

***

## Circuit Libraries

![](/uploads/snipaste_2022-07-20_12-07-19.jpg)

## Circuit Generators

![](/uploads/snipaste_2022-07-20_12-07-56.jpg)

## Other Compiler Functionalities

* Partial evaluation
* Memory allocation
* Parallelisation
* 