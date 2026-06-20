---
title: "Algorithms: Efficiency, Analysis, and Order"
publish: true
date created: 2026-06-14
---
# Analysis Of Algorithms
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

- An average-case analysis is valuable because it tells us how much time the algorithm would take when used many times on many different inputs.

- In general, a complexity function can be any function that maps the positive integers to the nonnegative reals. When not referring to the time complexity or memory complexity for some particular algorithm, we will usually use standard function notation, such as f(n) and g(n), to represent complexity functions


- The time complexity of an algorithm sometimes depends on the data structure used to implement

## Applying the Theory
- When applying the theory of algorithm analysis, one must sometimes be aware of the time it takes to execute the basic operation, the overhead instructions, and the control instructions on the actual computer on which the algorithm is implemented. By “overhead instructions” we mean instructions such as initialization instructions before a loop. The number of times these instructions execute does not increase with input size. By “control instructions” we mean instructions such as incrementing an index to control a loop. The number of times these instructions execute increases with input size. The basic operation, overhead instructions, and control instructions are all properties of an algorithm and the implementation of the algorithm. They are not properties of a problem. This means that they are usually different for two different algorithms for the same problem.


## Analysis of Correctness
- analysis of an algorithm means an efficiency analysis in terms of either
time or memory.
# Order
- Linear-time-algorithms: like n and 100n. Their time complexities are linear in the input size n.
- Quadratic-time-algorithms: like $n^2$, their time complexities are quadratic in the input size n.
- any linear-time algorithm is eventually more efficient than any quadratic-time algorithm.
## An Intuitive Introduction to Order
- pure quadratic: contains no linear term.
- complete quadratic: contains a linear term.

	The values of the other
	terms eventually become insignificant compared with the value of the quadratic term.
	
	Therefore, although the function is not a pure quadratic function, we can classify it with the pure quadratic functions.
- If a function is a member of the set Θ($n^2$), we say that the function is order of $n^2$.
- When an algorithm’s time complexity is in Θ($n^2$), the algorithm is called a
quadratic-time algorithm or a Θ($n^2$) algorithm.
- We will call these sets complexity categories.

![[order-pic1.png]]

In this ordering, if f(n) is in a category to the left of the category containing g(n), then
f(n) eventually lies beneath g(n) on a graph.
- We stress that there is more information in knowing a time complexity exactly than in simply knowing its order. There are times when it is quite difficult to determine the time complexities exactly. Therefore, we are sometimes content to determine only the order.
## A Rigorous Introduction to Order
asymptotic behavior of a function. (they are concerned only with eventual behavior.)
### big O
- Definition: For a given complexity function f(n), O(f(n)) is the set of complexity functions g(n) for which there exists some positive real constant c and some nonnegative integer N such that for all n ≥ N,
$$g(n) \leq c \times f(n)$$
- if g(n) ∈ O(f(n)), we say that g(n) is big O of f(n).
- We say that “big O” puts an asymptotic upper bound on a function.
 
![[order-pic2.png]]

- there is no unique N or unique c.
- This last example makes a crucial point about “big O.” A complexity function need not have a quadratic term to be in O($n^2$). It need only eventually lie beneath some pure quadratic function on a graph. Therefore, any logarithmic or linear complexity function is in O($n^2$). Similarly, any logarithmic, linear, or quadratic complexity function is in O($n^3$), and so on.

![[order-pic3.png]]
## Using a Limit to Determine Order