+++
date = 2022-06-09T11:53:29Z
hiddenFromHomePage = false
postMetaInFooter = false
title = "Default Array HLS configuration"
[flowchartDiagrams]
enable = false
options = ""
[sequenceDiagrams]
enable = false
options = ""

+++
> Refer to chapter 4 - lab 3 - Implementing Arrays as RTL Interfaces

Here is a function with input array (i.e. `din_t d_i[N]`)

_![](/uploads/snipaste_2022-06-09_21-55-09.jpg)

Synthesizing array arguments to RAM ports is the default. You can control how these ports  
are implemented using a number of other options.

***

# Using a single-port or dual-port RAM interface

Vivado HLS automatically analyzes the design and selects the number of ports (either single or dual port) to maximize the data rate

## Single Port

> **Note: If you specify a dual-port RAM and Vivado HLS determines that only a single port is required,  
> it uses a single-port and will override the dual-port specification.**

![](/uploads/snipaste_2022-06-09_21-54-01.jpg)

## Dual Port (with required unroll)

The first thing you must do is unroll the for-loop and allow all internal operations to happen in  
parallel, otherwise there is no benefit in multiple ports: the rolled for-loop ensure only one  
data sample can be read (or written) at a time.

![](/uploads/snipaste_2022-06-09_22-02-37.jpg)

> > > > This allows input data to be processed faster - but with only one FIFO output.

By using a dual-port RAM interface, this design can accept input data at twice the rate of  
the previous design. Because the for-loop was unrolled, the logic in the loop is able to  
consume data at this rate. By default, each loop iteration is executed in turn. This  
implementation code limits the logic to one read on d_i in each iteration. Unrolling the  
loops allows more reads to be performed (but creates N copies of the logic). **However**, by  
using a single-port FIFO interface on the output the output data rate is the same as before.

***

# Using FIFO interfaces

## Without FIFO

![](/uploads/snipaste_2022-06-09_22-06-05.jpg)

## With FIFO

![](/uploads/snipaste_2022-06-09_22-02-37.jpg)

Different port usage

***

# Partitioning into discrete ports

> When partitioning output in blocks of 4, and inputs in blocks of 2

![](/uploads/snipaste_2022-06-09_22-08-56.jpg)

* The design has the standard clock, reset, and block-level I/O ports.
* Array argument d_o has been implemented as a four separate FIFO interfaces.
* Argument d_i has been implemented as two separate RAM interfaces, each of which  
  uses a dual-port interface. (If you see four separate RAM interfaces, confirm a partition  
  factor for d_i is two and not four).

## All discrete ports

![](/uploads/snipaste_2022-06-09_22-15-13.jpg)

***

# Comparison

![](/uploads/snipaste_2022-06-09_22-16-26.jpg)

![](/uploads/snipaste_2022-06-09_22-23-59.jpg)

## Dual Port No-FIFO vs Dual Port FIFO

Without the FIFO interface, there is a lower latency and interval (19 vs 33).  
Whilst there are less FFs being used (-0.86%), there are more LUTs used (+3.72%)

***

# On Array Partitioning

[Read here](../array-partitioning)