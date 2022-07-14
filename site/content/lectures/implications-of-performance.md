+++
date = 2022-06-08T01:23:22Z
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

The high-level synthesiser will look at the functions and attempt to reduce the number of clock cycles required by possibly increasing the clock frequency.

As we lengthen the clock period ---> slower clock frequency, then we can pack more functionality per cycle.

***

## Code Hoisting

Code optimisation to refactor redundant / uncommon code paths.

![](/uploads/snipaste_2022-06-08_11-30-38.png)

***

## Loop Fission

Split a loop into multiple loops. This therefore allows the loops to be treated and optimised independently <s>(and can run in parallel)</s>

![](/uploads/snipaste_2022-06-08_11-32-14.png)

***

## Loop Unrolling

By default, HLS synthesis `for` loops sequentially; creating a data path that executes sequentially for each iteration of the loop. Replicate the loop body \[within the same loop\] and split the tasks.

![](/uploads/snipaste_2022-06-08_11-38-19.png)

We can insert the directive `#pragma HLS unroll factor=2` to automate this.

If we don't specify a `factor` argument, the loop will be unrolled completely - This **maximises the hardware resource usage** (and takes a long time to synthesise). The bounds of the loop need to be statically defined (i.e. during compile time).

> something something exit check?

***

## Loop Pipelining

Overlapping of executions (where possible).  
We can use the directive `#pragma HLS pipeline II=2` which will attempt to achieve an `II` of 2. If we don't specify the `II` argument, `II` will attempt to be minimised

![](/uploads/snipaste_2022-06-08_12-06-17.png)

***

# Loop Performance Metrics

* Iteration latency - number of cycles it takes to perform one iteration of the loop body
* Loop latency - number of cycles to complete the entire execution PLUS one to determine if the loop is finished / or a writeback
  * Vivado HLS defines the loop latency prior to writeback
* Initiation interval (`II`)- number of cycles before the next iteration of the loop can start
  * A higher II value can potentially increase the maximum operating frequency (fMAX) without a decrease in throughput

***

## Bit-width Optimisation

See [here](../bitwidth-optimisation)

***

# Loop Interchange / Pipeline-interleaved Processing

Switching loop variable usage around to reduce repeated lookups

See [here](../discrete-fourier-transform/#optimisation---loop-interchange)

***

# Function Pipelining

When pipelining a function, all loops contained in the function are unrolled, which is a requirement for pipelining

Pipelining loops gives you an easy way to control resources, with the option of partially unrolling the design to meet performance.

***

# False Dependencies

> For operations to block RAM (i.e. two ported), we must alternate between reads and writes as long as `x0` and `x1` are independent - in order to complete the operation.

What if they are not actually independent? For instance, we might know that the source of data never produces two consecutive pieces of data that actually have the same bin. What do we do now? If we could give this extra information to the HLS tool, then it would be able to read at location `x1` while writing at location `x0` because it could guarantee that they are different addresses. In Vivado® HLS, this is done using the dependence directive.

![](/uploads/snipaste_2022-07-15_00-19-09.jpg)

> To overcome this deficiency, you can use the DEPENDENCE directive to provide Vivado HLS with additional information about the dependencies.