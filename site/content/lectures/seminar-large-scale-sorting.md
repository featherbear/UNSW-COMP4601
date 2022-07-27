+++
date = 2022-07-27T01:46:38Z
hiddenFromHomePage = false
postMetaInFooter = false
title = "Seminar: Large-Scale Sorting"
[flowchartDiagrams]
enable = false
options = ""
[sequenceDiagrams]
enable = false
options = ""

+++
# Rationale

Large data - more computations to sort - slow.

FPGAs have potential for tailored design and parallelism

***

# Hardware Basics of Sorting

![](/uploads/snipaste_2022-07-27_11-48-36.jpg)

***

# Types of Sorts

## Insertion sort

> Time Complexity: O(n^2)

![](/uploads/snipaste_2022-07-27_11-49-41.jpg)

Issue - the architecture would not allow fast and large implementations with many comparators because the input signal has to be broadcasted to all comparator instances

**not good for large sets**

## Bucket Sort

> Time Complexity: O(n^2)

Divide and conquer, based on a pivot point

## Merge Sort

> Time Complexity: O(n log(n))

![](/uploads/snipaste_2022-07-27_11-52-45.jpg)

### FIFO-based Merge Sort

![](/uploads/snipaste_2022-07-27_11-52-59.jpg)

We can cascade several sorters  
![](/uploads/snipaste_2022-07-27_11-52-56.jpg)

> Each cascade will double the required memory resources