+++
date = 2022-06-30T09:56:50Z
hiddenFromHomePage = false
postMetaInFooter = false
title = "Array Partitioning"
[flowchartDiagrams]
enable = false
options = ""
[sequenceDiagrams]
enable = false
options = ""

+++
![](/uploads/snipaste_2022-06-30_19-57-55.jpg)

> `#pragma HLS array_partition ...`

* Factor - how many splits
* Modes
  * `block` - \[1-4\], \[5-9\]
  * `cyclic` - \[1,3,5,7,9\], \[2,4,6,8\]
  * `complete` - \[1\], \[2\], \[3\], ...
* `dim`(ension)- which part of the variable

Notes

* Cyclic is good for parallel sequential access
* Complete will use the max resources (since it fully splits everything)

![](/uploads/snipaste_2022-06-30_20-02-06.jpg)

***

![](/uploads/snipaste_2022-06-30_20-03-49.jpg)

> Task latency = `size + 5`

***

# Aside: Dual-port RAM

![](/uploads/snipaste_2022-06-30_20-07-27.jpg)  
For instances where there are only two accesses, we could get away with using a dual-port ram and not need to partition the array completely.

> If we are using a partitioning factor of f=2, we only have at most 2^f = 2^2 = 4 IOs (assuming using dual-port), provided we keep `II=1`
>
> Larger factors would require muxes and incur an increased `II`