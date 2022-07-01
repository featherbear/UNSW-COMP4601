+++
date = 2022-06-20T03:31:50Z
hiddenFromHomePage = false
postMetaInFooter = false
title = "CORDIC"
[flowchartDiagrams]
enable = false
options = ""
[sequenceDiagrams]
enable = false
options = ""

+++
> [https://www.youtube.com/watch?v=4HxdV5xEe9k](https://www.youtube.com/watch?v=4HxdV5xEe9k "https://www.youtube.com/watch?v=4HxdV5xEe9k")

# Coordinate Rotation Digital Computer

* Technique to evaluate trigonometric, hyperbolic and other mathematical functions
  * Digit-by-digit algorithm that produces one additional digit of precision per iteration
  * We can tune the **accuracy** by modifying the number of iterations (time), or by increasing the number of resources
* Uses only addition, subtraction, bit-shifting and table lookups - hardware efficient

![](/uploads/cordic.gif)

***

Rotation a vector by an angle can be expressed as a matrix multiplication.  
By selecting specific values of 2, we can rely on basic binary operations to rotate the vector

> CORDIC **revolves around the idea of “rotating” the phase of a complex number, by multiplying it by a succession of constant values**. However, the multiples can all be powers of 2, so in binary arithmetic they can be done using just shifts and adds; no actual multiplier is needed.

\--> Cordic Phase - angle which we rotated :: arctan(2^-1) ???

> Unoptimised CORDIC algorithm  
> ![Unoptimised CORDIC algorithm](/uploads/snipaste_2022-06-20_13-36-11.jpg)

A scaling factor is inadvertently induced, so we need to compensate for it

***

![](/uploads/snipaste_2022-06-21_15-38-55.jpg)

***

## `float` values

Floats consume a large number of resources. When targetting FPGAs it is better to use fixed point arithmetic types to represent fractional numbers. The parameters are customised to suit the specific use case.

* Start with `float` type
* Then optimise after

## `ap_fixed<size, int_bits>` and `ap_ufixed<size, int_bits>`

* Also have a rounding mode - floor, ceil, trunc, round
* [https://docs.xilinx.com/r/en-US/ug1399-vitis-hls/Arbitrary-Precision-Fixed-Point-Data-Types](https://docs.xilinx.com/r/en-US/ug1399-vitis-hls/Arbitrary-Precision-Fixed-Point-Data-Types "https://docs.xilinx.com/r/en-US/ug1399-vitis-hls/Arbitrary-Precision-Fixed-Point-Data-Types")

***

# Fixed-point and Optimised CORDIC

![](/uploads/snipaste_2022-06-21_15-54-46.jpg)

***

# Optimisations

* Fixed point types
* Multiplications -> Bit Shifts
* Loop iterations
* Unrolling, pipelining, etc