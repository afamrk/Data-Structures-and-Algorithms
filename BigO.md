# Table of Contents
- [Runtimes of Common Big-O Functions](#runtimes-of-common-big-o-functions)
- [Amortization](#amortization)
- [Big-O Complexity Chart](#big-o-complexity-chart)
- [Common Data Structure Operations](#common-data-structure-operations)
- [Array Sorting Algorithms](#array-sorting-algorithms)

## Runtimes of Common Big-O Functions

Here is a table of common Big-O functions:
Big-O | Name
- | -
1 | Constant
log(n)  | Logarithmic
n   | Linear
nlog(n) | Log Linear
n^2 | Quadratic
n^3 | Cubic
2^n | Exponential
O(n!) | factorial

## Amortization
Amortized complexity analysis is most commonly used with data structures that have state that persists between operations. The basic idea is that an expensive operation can alter the state so that the worst case cannot occur again for a long time, thus amortizing its cost.

> Let T1, T2, …, Tk be the complexities of a sequence of operations on a data structure. The amortized complexity of a single operation in this sequence is (T1 + T2 + …+ Tk) / k.

[Read more](https://yourbasic.org/algorithms/amortized-time-complexity-analysis/ "Amortized time complexity
")

## Big-O Complexity Chart
[![Big-O Complexity Chart](/images/bigo_chart.JPG)](https://www.bigocheatsheet.com/)

## Common Data Structure Operations
[![Common Data Structure Operations](/images/ds_bigo.JPG)](https://www.bigocheatsheet.com/)

## Array Sorting Algorithms
[![Array Sorting Algorithms](/images/sort_bigo.JPG)](https://www.bigocheatsheet.com/)

