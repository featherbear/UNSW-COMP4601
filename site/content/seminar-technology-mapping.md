+++
date = 2022-07-13T02:27:34Z
hiddenFromHomePage = false
postMetaInFooter = false
title = "Seminar: Technology Mapping"
[flowchartDiagrams]
enable = false
options = ""
[sequenceDiagrams]
enable = false
options = ""

+++
> Technology mapping is the process in which boolean logic is transformed into circuit components

# Why

* Area usage - we want to minimise usage as to not waste resources
* Delay - we want to minimise delay as to run a solution quickly (especially over many iterations)
* Placement and Routability - We want to be able to physically fit the design on a board

***

Most algorithms prioritise one of the considerations over the other.. how can we create an optimal solution that achieves the best over all considerations

***

# Direct Acyclic Graph (DAG) model

![](/uploads/snipaste_2022-07-13_12-31-43.jpg)

* Node - Logic gate
* Directed Edge - Signal flow

***

# FlowMap

Algorithm to produce a depth-minimsed solution which is delay optimised in polynomial time

![](/uploads/snipaste_2022-07-13_12-33-52.jpg)  
![](/uploads/snipaste_2022-07-13_12-35-53.jpg)

## Phase 1: Compute a label for all the nodes

![](/uploads/snipaste_2022-07-13_12-36-35.jpg)  
![](/uploads/snipaste_2022-07-13_12-38-06.jpg)

## Phase 2: Generate K-LUT

![](/uploads/snipaste_2022-07-13_12-38-15.jpg)

***

# FlowMap Improvements

`K` - number of inputs to the LUT

`K-feasible cut` - Best way to cut the tree (cutting max K lines)

?

***