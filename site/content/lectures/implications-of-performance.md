+++
date = 2022-06-08T01:23:22Z
draft = true
hiddenFromHomePage = false
postMetaInFooter = false
title = "Implications of Performance"
[flowchartDiagrams]
enable = false
options = ""
[sequenceDiagrams]
enable = false
options = ""

+++
**There is no good rule to pick the optimal target clock frequency.**

> For this course: start with a clock period of 10ns

HLS will attempt to optimise clock count as well as optimise clock speed.

***

## Operational Chaining

The high-level synthesiser will look at the functions and attempt to reduce the number of clock cycles required by possibly increasing the clock frequency

## Code Hoisting

Code optimisation to refactor redundant / uncommon code paths.

![](/uploads/snipaste_2022-06-08_11-30-38.png)

## Loop Fission

Split a loop into multiple loops. This therefore allows the loops to be treated independently (and can run in parallel)

![](/uploads/snipaste_2022-06-08_11-32-14.png)

## Loop Unrolling

By default, HLS synthesis `for` loops sequentially; creating a data path that executes sequentially for each iteration of the loop. Replicate the loop body \[within the same loop\] and split the tasks.

![](/uploads/snipaste_2022-06-08_11-38-19.png)

We can insert the directive `#pragma HLS unroll factor=2` to automate this.

If we don't specify a `factor` argument, the loop will be unrolled completely - This **maximises the hardware resource usage** (and takes a long time to synthesise). The bounds of the loop need to be statically defined (i.e. during compile time).

> something something exit check?