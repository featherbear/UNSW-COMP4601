+++
date = 2022-07-27T01:11:00Z
hiddenFromHomePage = false
postMetaInFooter = false
title = "Seminar: Neural Network Accelerators"
[flowchartDiagrams]
enable = false
options = ""
[sequenceDiagrams]
enable = false
options = ""

+++
![](/uploads/snipaste_2022-07-27_11-12-14.jpg)

![](/uploads/snipaste_2022-07-27_11-12-49.jpg)  

# Layers

## Convolutional Layer

* Main building block
* Contains a sets of filters (mathematical kernels), whose parameters are learned throughout the training

## Normalisation Layer

* Normalises the output, to avoid overfitting
* Prevents small changes of parameters amplifying 

![](/uploads/snipaste_2022-07-27_11-16-32.jpg)

## Pooling Layer

* Sliding 2D filter that summarises the features within a region
* Reduces the dimensions of a feature map

## Fully Connected Layer

![](/uploads/snipaste_2022-07-27_11-19-07.jpg)

***

# Applications

Neural networks are CPU-heavy, so an FPGA designed implementation is cost effective

![](/uploads/snipaste_2022-07-27_11-20-38.jpg)

***

# Maths

![](/uploads/snipaste_2022-07-27_11-23-24.jpg)

Throughput (IPS) = (Number of units * frequency * utilisation ratio) / work

Latency = Concurrency / throughput

* Can increase performance by decreasing accuracy
* Increase energy efficiency?

***

# Model Compression Methods

## Data Quantization

Convert values into quantised values

> i.e. Changing a floating point value into an 8-bit integer

### Linear Quantization

> 1. Dynamic-precision data quantization

Different layers have different precision requirements

* Analyse data distribution
* Propose multiple solutions with different bit-width combinations
* Choose the best solution

![](/uploads/snipaste_2022-07-27_11-27-11.jpg)

> 2. Hybrid Quantization

Keep the first and last layers as the same datatype

Intermediary layers change in type

### Non-Linear Quantization

Lookup table / hashtable

***

# Hardware Design - Acceleration

## Computational Unit Level

e.g. Low bit-width, fast convolutional algorithm

### Binarized Neural Network

* Turn values into binary
* Convolutional and FC layers can be expressed as binary operations - XnorPopcount
* Slight loss of accuracy
  * Some techniques use a gain term to restore the accuracy

### Factorised Dot Product

For non-linear quantisation, if the range of values is small, and the number of possible weights is less than the kernel size - then we can **Add > Multiply** instead of **Multiply > Add**

### Fast Convolution Algorithms

> DFT, FFT, <u>**Winograd**</u>

Convolutions can be expressed as a matrix multiplication!

Image2Column - Convert convolution into a matrix multiplication

![](/uploads/snipaste_2022-07-27_11-39-01.jpg)

Winograd Multiplication - Fast multiplication algorithm

![](/uploads/snipaste_2022-07-27_11-39-09.jpg)

## Layer Level

> Network structure optisations

Loop parameters, data transfer optimisations

## System Design level

Roofline model