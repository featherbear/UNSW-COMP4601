+++
date = 2022-07-27T02:24:05Z
hiddenFromHomePage = false
postMetaInFooter = false
title = "Seminar: Graph Processing using FPGAs"
[flowchartDiagrams]
enable = false
options = ""
[sequenceDiagrams]
enable = false
options = ""

+++
# Accelerating Large-Scale Single-Source Shortest Path

## Bellman-Ford Algorithm

![](/uploads/snipaste_2022-07-27_12-27-50.jpg)

## Single-Source Shortest Path (SSSP)

Maximises data parallelism

Efficient data forwarding scheme to handle data hazards in the pipelined architecture

***

![](/uploads/snipaste_2022-07-27_12-29-24.jpg)

***

![](/uploads/snipaste_2022-07-27_12-30-17.jpg)

***

![](/uploads/snipaste_2022-07-27_12-43-59.jpg)

Higher parallelism = higher resource utilisation

![](/uploads/snipaste_2022-07-27_12-44-40.jpg)

Higher graph size = lower clock rate

# High-throughput and Energy-efficient Graph Processing

* Optimise the data layout for an edge-centric design

## Edge-Centric Graph Processing

* Scatter phase - Message is broadcasted to find the destination
* Gather phase - Update node value

***

# Data Layout and Power Optimisation