+++
date = 2022-07-13T02:49:53Z
hiddenFromHomePage = false
postMetaInFooter = false
title = "Seminar: FPGA Routing"
[flowchartDiagrams]
enable = false
options = ""
[sequenceDiagrams]
enable = false
options = ""

+++
> FPGA Routing is a way of deciding the amount of area used by wire segments and programmable switches as compared to area consumed by logic blocks. A

Allows logic block I/O to be connected to a larger circuit

Long paths - propagation delays

# Goals for efficient routing

* Get it all routed
* Avoid congestion
* Minimal delay

# Problems

Lack of routing resources. Whilst we could use routing trees, these trees become a critical path and become a source of resource constraints in themselves.

"Rip-up and retry" algorithm proposed - but the success of a route is dependent on both the choice of which nets are routed, but also the order of rerouting

**Other variations**

* blame factor
* global router
* delay

***

# Coarse Graph Expansion Algorithm (CGE)

## Background Information

![](/uploads/snipaste_2022-07-13_12-55-58.jpg)  
![](/uploads/snipaste_2022-07-13_12-59-06.jpg)

### Cost Function Design

![](/uploads/snipaste_2022-07-13_13-08-30.jpg)

## A routing conflict

![](/uploads/snipaste_2022-07-13_12-57-38.jpg)

## Algorithm - LocusRoute Global Routing

![](/uploads/snipaste_2022-07-13_12-59-47.jpg)

Notes: "two point connection" = logic block

### Post operation

We need to choose the best wiring segment to implement the connection

## Detailed Routing

![](/uploads/snipaste_2022-07-13_13-02-31.jpg)  
![](/uploads/snipaste_2022-07-13_13-03-05.jpg)  
![](/uploads/snipaste_2022-07-13_13-04-29.jpg)

## Connection Formation

![](/uploads/snipaste_2022-07-13_13-05-46.jpg)

![](/uploads/snipaste_2022-07-13_13-10-08.jpg)

## Controlling Capacity

![](/uploads/snipaste_2022-07-13_13-10-54.jpg)

## Pruning Algorithm

![](/uploads/snipaste_2022-07-13_13-12-04.jpg)  
![](/uploads/snipaste_2022-07-13_13-12-47.jpg)

***

# Iterative Approach to Design

![](/uploads/snipaste_2022-07-13_13-13-17.jpg)

* Start with small value parameters, if not possible / timeout, then increase parameters

***

# Pathfinder Algorithm

![](/uploads/snipaste_2022-07-13_13-17-15.jpg)

![](/uploads/snipaste_2022-07-13_13-18-57.jpg)

The global router instructs the signal router to select a path from a source to a sink.  
Creates a MST tree (hence shortest paths)

## Slack Ratio

![](/uploads/snipaste_2022-07-13_13-20-25.jpg)  
Ratio = `Longest path used by the resource` : `Longest path in the graph`

Ratio \~= 1 -> Higher priority since it is more of a critical path

***

## Cost Function

![](/uploads/snipaste_2022-07-13_13-22-18.jpg)  
`A_ij` = Slack ratio from `i` to `j`

***

## Negotiated Congestion/Delay (NCD) Pseudocode

![](/uploads/snipaste_2022-07-13_13-24-43.jpg)

***

![](/uploads/snipaste_2022-07-13_13-27-32.jpg)