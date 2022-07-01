+++
date = 2022-06-09T09:04:21Z
hiddenFromHomePage = false
postMetaInFooter = false
title = "Misc notes"
[flowchartDiagrams]
enable = false
options = ""
[sequenceDiagrams]
enable = false
options = ""

+++
* latency for N inputs: L = loop_latency + (N-1) * initialize_interval

# Pipeline

![](/uploads/snipaste_2022-07-01_02-06-40.jpg)

???

Pipelining the function unrolls all the loops within it, and thus greatly increases the area. If the objective is to get the highest possible performance with no regard for area, this may be the best optimization to perform.

When pipelining nested loops, it is generally best to pipeline the inner-most loop. Typically, High-Level Synthesis can generally flatten the loop nest automatically (allowing the outer loop to simply feed the inner loop).  