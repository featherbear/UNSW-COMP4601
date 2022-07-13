+++
date = 2022-07-13T01:52:24Z
draft = true
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