---
title: Dynamic Programming
publish: true
date created: 2026-06-19
---
# Floyd’s Algorithm for Shortest Paths
- A common problem encountered by air travelers is the determination of the shortest way to fly from one city to another when a direct flight does not exist.

- In a directed graph, a path is a sequence of vertices such that there is an edge from each vertex to its successor.

- If a graph contains a cycle, it is cyclic.

- A path is called simple if it never passes through the same vertex twice.

- The length of a path in a weighted graph is the sum of the weights on the pathو in an unweighted graph it is simply the number of edges in the path.

- A shortest path must be a simple path.

- The Shortest Paths problem is an optimization problem.

- There can be more than one candidate solution to an instance of an optimization problem. Each candidate solution has a value associated with it, and a solution to the instance is any candidate solution that has an optimal value. Depending on the problem, the optimal value is either the minimum or the maximum. In the case of the Shortest Paths problem, a candidate solution is a path from one vertex to another, the value is the length of the path, and the optimal value is the minimum of these lengths.

- Brute-Force: worse than exponential-time. We encounter this same situation in many optimization problems. That is, the obvious algorithm that considers all possibilities is exponential-time or worse. Our goal is to find a more efficient algorithm.
- Using dynamic programming, we create a cubic-time algorithm for the Shortest Paths problem. First we develop an algorithm that determines only the lengths of the shortest paths. After that we modify it to produce shortest paths as well. We represent a weighted graph containing n vertices by an array W where
	![[floyd-pic1.png]]

- D(k) \[i] \[j] = length of a shortest path from vi to vj using only vertices in the set {v1, v2,… , vk } as intermediate vertices.
![[floyd-pic2.png]]

![[floyd-pic3.png]]

- two cases are considered after this that you should read in the book. page 127.

![[floyd-pic4.png]]

- the algorithm:
![[floyd-pic5.png]]

- $\Theta(n^3)$
- Algorithm with creating the shortest path.

![[floyd-pic6.png]]

- algorithm to print the shortest path: $\Theta(n)$

![[floyd-pic7.png]]

- Recall the convention established in Chapter 2 of making only variables, whose values can change in the recursive calls, inputs to recursive routines. Therefore, the array P is not an input to path. If the algorithm were implemented by defining P globally, and we wanted a shortest path from vq to vr, the top-level call to path would be as follows:
	path (q , r) ;
	Given the value of P in Figure 3.5, if the values of q and r were 5 and 3,
	respectively, the output would be v1 v4.
# The Traveling Salesperson Problem
- Suppose a salesperson is planning a sales trip that includes 20 cities. Each city is connected to some of the other cities by a road. To minimize travel time, we want to determine a shortest route that starts at the salesperson’s home city, visits each of the cities once, and ends up at the home city. This problem of determining a shortest route is called the Traveling Salesperson problem.

- A tour (also called a Hamiltonian circuit) in a directed graph is a path from a vertex to itself that passes through each of the other vertices exactly once.

- An optimal tour in a weighted, directed graph is such a path of minimum length.

- The Traveling Salesperson problem is to find an optimal tour in a weighted, directed graph when at least one tour exists.

- Notice that if vk is the first vertex after v1 on an optimal tour, the subpath of that tour from vk to v1 must be a shortest path from vk to v1 that passes through each of the other vertices exactly once. This means that the principle of optimality applies, and we can use dynamic programming.
![[dp-pic1.png]]

![[TSP-pic2.png]]

- Length of an optimal tour = $\underset{2\leq j\leq n}{\text{minimum}} \left( W[1][j] + D[v_j][V - \{v_1, v_j\}] \right)$
and in general for $i \ne 1$ abd $v_i$ not in A,
![[TSP-pic3.png]]

- The algorithm:
![[TSP-pic4.png]]

- time complexity: $\Theta(n2^n)$

![[TSP-pic5.png]]

- Do example 3.11 page 154, for better understanding. 
![[TSP-pic6.png]]
![[TSPpic7.png]]
