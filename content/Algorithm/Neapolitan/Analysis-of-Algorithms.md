---
title: Analysis of Algorithms
publish: true
date created: 2026-06-14
---
## Complexity Analysis
- We analyze the algorithms efficiency by determining the number of times some basic operation is done as a function of the size of the input.

- When the input to an algorithm is a graph, we often measure the size of the input i terms of both the number of vertices and the number of edges. (we can consider 2 parameters)

- Sometimes n is not the size, but is the input itself. For example in Fibonachi a reasonable measure of the size of the input is the number of symbols used to encode n. (using binary representation, the input size will be the number of bits it takes to encode n, which is $\lfloor lgn \rfloor + 1$)

- _basic operation_: we pick some instruction or group of instructions such that the total work done by the algorithm is roughly proportional to the number of times this instruction or group of instructions is done. We call this instruction or group of instructions the basic operation in the algorithm.

- _time complexity analysis_: In general, a time complexity analysis of an algorithm is the determination of how many times the basic operation is done for each value of the input size.

- we ordinarily do not include the instructions that make up the control structure. For example, we do not include the instructions that increment and compare the index in order to control the passes through the while loop. =1

- Assignment instructions = 1.

- Comparison instructions = 1.

- _T(n)_: When the basic operation is always done the same number of times for every instance of size n, T(n) is defined as the number of times the algorithm does the basic operation for an instance of size n. T(n) is called the every-case time complexity of the algorithm, and the determination of T(n) is called an every-case time complexity analysis.

- _W(n)_: W(n) is defined as the maximum number of times the algorithm will ever do its basic operation for an input size of n. So W(n) is called the worst-case time complexity of the algorithm, and the determination of W(n) is called a worst-case time complexity analysis. If T(n) exists, then clearly W(n) = T(n).

- _A(n)_: A(n) is defined as the average (expected value) of the number of times the algorithm does the basic operation for an input size of n (see Section A.8.2 in Appendix A for a discussion of average). A(n) is called the average-case time complexity of the algorithm, and the determination of A(n) is called an average-case time complexity analysis. As is the case for W(n), if T(n) exists, then A(n) = T(n).

- _B(n)_: For a given algorithm, B(n) is defined as the minimum number of times the algorithm will ever do its basic operation for an input size of n. So B(n) is called the best-case time complexity of the algorithm, and the determination of B(n) is called a best-case time complexity analysis. As is the case for W(n) and A(n), if T(n) exists, then B(n) = T(n).



- The time complexity of an algorithm sometimes depends on the data structure used to implement