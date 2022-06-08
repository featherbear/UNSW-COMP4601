+++
date = 2022-06-08T02:22:53Z
hiddenFromHomePage = false
postMetaInFooter = false
title = "Bitwidth Optimisation"
[flowchartDiagrams]
enable = false
options = ""
[sequenceDiagrams]
enable = false
options = ""

+++
* Smaller operations may require fewer clock cycles to execute
* Operations split into smaller operations can be parallelised

If variables are 32 bits wide, then more primitive Boolean operations need to be performed than if they were 8 bits wide (consequently more resources are required)

More complicated logic typically also require more pipelining to achieve the same frequency

![](/uploads/snipaste_2022-06-08_12-27-54.png)