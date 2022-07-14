+++
date = 2022-07-14T21:22:32Z
hiddenFromHomePage = false
postMetaInFooter = false
title = "Loop Carry Dependence affecting Initiation Interval"
[flowchartDiagrams]
enable = false
options = ""
[sequenceDiagrams]
enable = false
options = ""

+++
![](/uploads/snipaste_2022-07-15_07-22-09.jpg)

Lines 30 and 29 cannot occur simultaneously, likewise with 35 and 34.

This is because if `i == reversed` we will have a WAW (write after write) hazard, since it is possible for `i` to be equal to `reversed` (see line 26)