---
title: Dynamic Programming
publish: true
date created: 2026-06-19
---
# Floyd’s Algorithm for Shortest Paths
- In a directed graph, a path is a sequence of vertices such that there is an edge from each vertex to its successor.
- If a graph contains a cycle, it is cyclic.
- A path is called simple if it never passes through the same vertex twice.
- The length of a path in a weighted graph is the sum of the weights on the pathو in an unweighted graph it is simply the number of edges in the path.
- A shortest path must be a simple path.
- The Shortest Paths problem is an optimization problem.
- There can be more than one candidate solution to an instance of an optimization problem. Each candidate solution has a value associated with it, and a solution to the instance is any candidate solution that has an optimal value. Depending on the problem, the optimal value is either the minimum or the maximum. In the case of the Shortest Paths problem, a candidate solution is a path from one vertex to another, the value is the length of the path, and the optimal value is the minimum of these lengths.
- Brute-Force: worse than exponential-time.
# The Traveling Salesperson Problem
