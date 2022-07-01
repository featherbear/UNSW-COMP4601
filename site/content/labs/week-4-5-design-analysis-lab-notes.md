+++
date = 2022-06-30T16:10:02Z
hiddenFromHomePage = false
postMetaInFooter = false
title = "Week 4/5 Design Analysis Lab Notes"
[flowchartDiagrams]
enable = false
options = ""
[sequenceDiagrams]
enable = false
options = ""

+++
> Read [Identifying Performance Bottlenecks](../../identifying-performance-bottlenecks)

***

# Note about Pipelining

> Tutorial page 120

Even though we pipelined the inner nested loop; the write operation could not be flattened into the inner loop.  
We need to pipeline the outer loop instead - and **unroll the inner loop instead**

![](/uploads/snipaste_2022-07-01_02-09-46.jpg)

* Will increase the area usage

***

# Final Results

![](/uploads/snipaste_2022-07-01_02-48-32.jpg)

We've a <125 cycle interval; though we used 8x more FFs, and 2x more LUTs