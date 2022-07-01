+++
date = 2022-06-09T12:27:36Z
hiddenFromHomePage = false
postMetaInFooter = false
title = "AXI4-Stream Interfaces"
[flowchartDiagrams]
enable = false
options = ""
[sequenceDiagrams]
enable = false
options = ""

+++
> To reach optimal performance implementation of this design, the data for each channel is processed in parallel, with dedicated hardware for each channel.  
>   
> The key to understanding how best to perform this optimization is to recognize that the  
> channels in the input and output arrays lend themselves to cyclic partitioning. Cyclic  
> partitioning basically means each array element is, in turn, sorted into a different partition.