+++
date = 2022-06-30T10:12:22Z
hiddenFromHomePage = false
postMetaInFooter = false
title = "Matrix Multiplication"
[flowchartDiagrams]
enable = false
options = ""
[sequenceDiagrams]
enable = false
options = ""

+++
## Implementation

![](/uploads/snipaste_2022-06-30_19-31-30.jpg)

## Default Synthesis

![](/uploads/snipaste_2022-06-30_19-33-28.jpg)

* Sequential architecture
* One multiplier
* One adder
* BRAM
* High task latency and task interval

## Unrolling the inner loop (dot product loop)

> Could also use the UNROLL directive, but for manual sake ...

![](/uploads/snipaste_2022-06-30_19-35-19.jpg)  
![](/uploads/snipaste_2022-06-30_19-35-59.jpg)

## Sequential implementation of the unrolled inner loop

![](/uploads/snipaste_2022-06-30_19-38-17.jpg)

* Could do multiplication in several stages, and therefore start adding in advanced
  * Note: A mux would be needed, and requires 1 LUT per bit

## Pipelined execution of the inner loop

![](/uploads/snipaste_2022-06-30_19-41-34.jpg)

Task latency -> `3*size + 3`

## Pipelined Operators (i.e. Multipliers)

> **Note: A bunch of different things within the FPGA are already pipelined**

![](/uploads/snipaste_2022-06-30_19-46-50.jpg)

Task Latency -> `3*size + 5`

Note: Higher latency, but less multipliers

## With Complete Array Partitioning

See [Array Partitioning](../array-partitioning)

Task Latency -> `size + 5`

Note: Very high resource count

## With Dual-Port RAM and Array Partitioning f=2

See [Array Partitioning](../array-partitioning)

For instances where there are only two accesses, we could get away with using a dual-port ram and not need to partition the array completely.

> If we are using a partitioning factor of f=2, we only have at most 2^f = 2^2 = 4 IOs (assuming using dual-port), provided we keep `II=1`
>
> Larger factors would require muxes and incur an increased `II`