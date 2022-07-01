+++
date = 2022-06-30T09:12:13Z
hiddenFromHomePage = false
postMetaInFooter = false
title = "Discrete Fourier Transform"
[flowchartDiagrams]
enable = false
options = ""
[sequenceDiagrams]
enable = false
options = ""

+++
* Represent a periodic signal as a sum of sinusoids
  * Transforms a fixed number of signal samples (i.e. discrete) in the time domain to a discrete signal in the frequency domain
  * Allows for advanced filtering and modulation techniques, as well as fast large integer and polynomial multiplication
* Essentially a matrix-vector multiplication, where the matrix is a fixed set of coefficients

***

![](/uploads/snipaste_2022-06-30_19-17-31.jpg)

* `N` real values, signal represented by `g[]` (time domain)
* `N/2 + 1` complex values, signal represented by `G[]` (frequency domain)
  * `G = S·g`
  * `S` is the matrix which our discrete time signals are multiplied by
    * // Columns represent fractional rotations //

## Visualisation (8 point DFT)

![](/uploads/snipaste_2022-06-30_19-26-24.jpg)

* Symmetry e.g. `s[i][j] = s[j][i]`

***

# Matrix Multiplication Implementation

![](/uploads/snipaste_2022-06-30_19-31-30.jpg)

> [**Read more here**](../../matrix-multiplication)

***

# Baseline

![](/uploads/snipaste_2022-06-30_20-13-13.jpg)

Notes

* `N = 256` means that `SIZE = 256 * 256 = a big value`
* This implementation is not ideal for HLS
  * `cos` and `sin` are slow!
    * Maybe we could use [CORDIC](../cordic) 🤔

## Schedule

![](/uploads/snipaste_2022-06-30_20-20-43.jpg)

## Architecture

![](/uploads/snipaste_2022-06-30_20-21-16.jpg)

# Optimisation

![](/uploads/snipaste_2022-06-30_20-21-56.jpg)

* Floating point operations is expensive and requires many pipeline stages
* Pipelining reduces the impacts of these high-latency operations
* However, the loop carry dependency of `temp_real` and `temp_imag` limits the achievable `II` when pipelining the inner loop

## Optimisation - Loop Interchange

> e.g. swap `i` and `j`

Accumulate independent values

![](/uploads/snipaste_2022-06-30_20-26-20.jpg)

## Optimisation - Lookups for Sin and Cos

![](/uploads/snipaste_2022-06-30_20-26-43.jpg)

## Optimisation - Interface

![](/uploads/snipaste_2022-06-30_20-27-43.jpg)