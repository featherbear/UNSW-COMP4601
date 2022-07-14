+++
date = 2022-07-14T08:25:22Z
hiddenFromHomePage = false
postMetaInFooter = false
title = "Streaming Interfaces"
[flowchartDiagrams]
enable = false
options = ""
[sequenceDiagrams]
enable = false
options = ""

+++
> In a streaming interface, the values must be accessed in sequential order.  
> If there are multiple accesses to the same addresses, a streaming interfaces cannot be used.

We may need to internally cache values to ensure that a design does not re-read a port (since a FIFO interface aka queue only goes forwards)