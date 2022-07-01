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

![](/uploads/snipaste_2022-07-01_00-10-53.jpg)

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

***

## Bit-width Optimisation

See [here](../bitwidth-optimisation)

***

## Task Pipelining

When each stage is described as an independent task with all stages being interlinked in a  
pipeline, then these stages can be executing concurrently on different data sets. Such a hardware optimisation is task pipelining.

* Rather than waiting for the first task to complete all the required function calls, the second task can commence after the first task has only finished the first function call.
* The first task continues to execute each stage in the pipeline in order, followed by the remaining tasks in order
* Once the pipeline is full all sub-functions would be executing concurrently, each operating on different input data

> Requires each stage to be implemented with independent hardware.  
> Sufficient storage is also needed to contain the intermediate computations

e.g. see [related](../fast-fourier-transform#task-pipelining)  
![](/uploads/snipaste_2022-07-01_00-03-16.jpg)

![](/uploads/snipaste_2022-07-01_00-03-47.jpg)

^ Can use both `dataflow` directive for coarse, and `pipeline` for fine optimisations

![](/uploads/snipaste_2022-07-01_00-07-49.jpg)

> If we find a critical path that cannot be sped up anymore; then we could potentially "de"-optimise other functions to perform favour slower performance albeit less resource requirements; than for the functions to perform quickly (but being blocked by the critical path function), with higher resource requirements.

![](/uploads/snipaste_2022-07-01_00-10-02.jpg)

> Pipelining the function unrolls all the loops within it, and thus greatly increases the area. If the objective is to get the highest possible performance with no regard for area, this may be the best optimization to perform.
>
> When pipelining nested loops, it is generally best to pipeline the inner-most loop. Typically, High-Level Synthesis can generally flatten the loop nest automatically (allowing the outer loop to simply feed the inner loop).