+++
date = 2022-07-13T01:52:24Z
hiddenFromHomePage = false
postMetaInFooter = false
title = "Seminar: Architectural Synthesis"
[flowchartDiagrams]
enable = false
options = ""
[sequenceDiagrams]
enable = false
options = ""

+++
# Scope

* State Machines
* Component Connectivity

***

# I/O

* Input
  * Resources
  * Constraints
  * Sequencing Graph
* Output
  * Source
  * Schedule
  * RTL

***

# Sequencing Graphs

Node-like tree which describes the structure

# Building blocks in Architectural Synthesis

* Functional Resources
* Memory Resources
* Interface Resources

## Constraints

* Interface constraints - e.g. format and timing of I/O data transfers
* Implementation constraints - e.g. area and latency

***

# Scheduling (temporal synthesis)

Planning when each operation will run

# Binding (spatial synthesis)

Planning of which resources should be assigned or co-assigned (for resource efficiency) to what operations

***

# Optimisation Problems

![](/uploads/snipaste_2022-07-13_11-55-53.jpg)

Unbounded nodes have an arbitrary delay which prevent synthesis from accurate scheduling it within the design. The design can be partitioned into different steps to try maximise the efficiency where possible

***

* Aggressively optimises for II (#cycles) - i.e. throughput
* _Then_ optimises for latency (#cycles)
* _Then_ optimises for area

***

# A blank timeslot?

![](/uploads/snipaste_2022-07-13_12-06-45.jpg)

It's pipelined, and allows us to tile it!

***

# Data-path Designs

* Bus-oriented
* Macro-cell based
* Array based

***

# Control Unit Synthesis

* Microcode - instructions that tell the control unit how to operate
  * Each codeword is `log n` bits?
  * 