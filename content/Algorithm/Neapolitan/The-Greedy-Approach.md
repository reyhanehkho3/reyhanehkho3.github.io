---
title: The Greedy Approach
publish: true
date created: 2026-06-18
---
# Minimum Spanning Trees

- there is no guarantee that a given greedy algorithm always yields an optimal solution.
- A selection procedure chooses the next item to add to the set. The selection is performed according to a greedy criterion that satisfies some locally optimal consideration at the time.
- A feasibility check determines if the new set is feasible by checking whether it is possible to complete this set in such a way as to give a solution to the instance. (?)
- A solution check determines whether the new set constitutes a solution to the instance. 

**Consider the problem of removing edges from a connected, weighted, undirected graph G to form a subgraph such that all the vertices remain connected and the sum of the weights on the remaining edges is as small as possible.**
- A subgraph with minimum weight must be a tree, because if a subgraph were not a tree, it would contain a simple cycle, and we could remove any edge on the cycle, resulting in a connected graph with a smaller weight.
## Spanning Tree
- A spanning tree for G is a connected subgraph that contains all the vertices in G and is a tree.(doesn't contain cycles)
	 So for a spanning tree:
		-It must include **all the vertices** of the original graph G.
		- It must be **connected** (there's a path between every pair of vertices).
		- It must have **no cycles** (which means if G has n vertices, the spanning tree will have exactly n−1 edges).
- A connected subgraph of minimum weight must be a spanning tree
## Minimum Spanning Tree
- Minimum Spanning Tree has the minimum total weight.
- A graph can have more than one minimum spanning tree.
- Brute-force will be worse than exponential. So we'll use Greedy for this.
- A spanning tree T for G has the same vertices V as G, but the set of edges of T is a subset F of E. We will denote a spanning tree by T = (V , F).Our problem is to find a subset F of E such that T = (V , F) is a minimum spanning tree for G.
- The algorithm:
![[sapnningTreeAlgo.png]]
- The locally optimal property is not unique. We investigate 2 greey algorithms for this problem. Prim's and Kruskal's. Each uses a different locally optimal property.
- Both Prim’s and Kruskal’s algorithms always produce minimum spanning trees.

### Prim's Algorithm
- Prim’s algorithm starts with an empty subset of edges F and a subset of vertices Y initialized to contain an arbitrary vertex. We will initialize Y to {v1}. A vertex nearest to Y is a vertex in V −Y that is connected to a vertex in Y by an edge of minimum weight. The vertex that is nearest to Y is added to Y and the edge is added to F. The process of adding nearest vertices is repeated until Y = V.
- The algorithm:
![[prim's-algo.png]]
- The selection procedure and feasibility check are done together because taking the new vertex from V − Y guarantees that a cycle is not created.
- In computer, we represent a weighted graph by its adjacency matrix.
![[prim-pic1.png]]
![[prim-pic2.png]]
![[prim-pic3.png]]
- As vertices are added to Y , these two arrays are updated to reference the new vertex in Y nearest to each vertex outside of Y . To determine which vertex to add to Y , in each iteration we compute the index for which distance[i] is the smallest. We call this index vnear. The vertex indexed by vnear is added to Y by setting distance[vnear] to −1.
- Prim's Algorithm:
![[prim-pic4.png]]

- Time complexity: $\theta(n^2)$
- There is a theorem to prove that prim's algorithm always produces a minimum spanning tree, if you want to check, page 183.

### Kruskal's Algorithm
- Kruskal’s algorithm for the Minimum Spanning Tree problem starts by creating disjoint subsets of V , one for each vertex and containing only that vertex. It then inspects the edges according to nondecreasing weight (ties are broken arbitrarily). If an edge connects two vertices in disjoint subsets, the edge is added and the subsets are merged into one set. This process is repeated until all the subsets are merged into one set.
- Algorithm:

![[kruskals-pic1.png]]
![[kruskal-pic2.png]]
- The while loop is exited when there are n−1 edges in F, because there are n − 1 edges in a spanning tree.
- Worst case: $\Theta(n^2 \log n)$
- The proof that kruskal's always produces an optimal solution is on page 188.
### Which one?
For a graph whose number of edges m is near the low end of these limits (the graph is very sparse), Kruskal’s algorithm is Θ(n lg n), which means that Kruskal’s algorithm should be faster. However, for a graph whose number of edges is near the high end (the graph is highly connected), Kruskal’s algorithm is Θ(n2 lg n), which means that Prim’s algorithm should be faster.

# Dijkstra’s Algorithm for Single-Source Shortest Paths
- This algorithm is similar to Prim’s algorithm for the Minimum Spanning Tree problem. We initialize a set Y to contain only the vertex whose shortest paths are to be determined. For focus, we say that the vertex is v1. We initialize a set F of edges to being empty. First we choose a vertex v that is nearest to v1, add it to Y , and add the edge < v1, v > to F. (By < v1, v > we mean the directed edge from v1 to v.) That edge is clearly a shortest path from v1 to v. Next we check the paths from v1 to the vertices in V − Y that allow only vertices in Y as intermediate vertices. A shortest of these paths is a shortest path (this needs to be proven). The vertex at the end of such a path is added to Y , and the edge (on the path) that touches that vertex is added to F. This procedure is continued until Y equals V , the set of all vertices. At this point, F contains the edges in shortest paths. The following is a high-level algorithm for this approach.

![[dijkstra-pic1.png]]

- touch[i] =index of vertex v in Y such that the edge <v, vi> is the last edge on the current shortest path from v1 to vi using only vertices in Y as intermediates.
- length[i] = length of the current shortest path from v1 to vi using only vertices in Y as intermediates.

![[dijkstra-pic2.png]]

- Using priority queue, **O(E log V)** (where E is the number of roads and V is the number of cities/nodes)
# The Greedy Approach versus Dynamic Programming: The Knapsack Problem
### A Greedy Approach to the 0-1 Knapsack Problem
- steal the items with the largest profit per unit weight first.
- we order the items in nonincreasing order according to profit per unit weight, and select them in sequence. An item is put in the knapsack if its weight does not bring the total weight above W.
### A Greedy Approach to the Fractional Knapsack Problem
Similar ti the algorithm in 0-1.
- Our greedy algorithm never wastes any capacity in the Fractional Knapsack problem as it does in the 0-1 Knapsack problem.
### A Dynamic Programming Approach to the 0-1 Knapsack Problem
- the proof that the principle of optimality applies:
	 If we can show that the principle of optimality applies, we can solve the 0-1 Knapsack problem using dynamic programming. To that end, let A be an optimal subset of the n items. There are two cases: either A contains itemn or it does not. If A does not contain itemn, A is equal to an optimal subset of the first n − 1 items. If A does contain itemn, the total profit of the items in A is equal to pn plus the optimalprofit obtained when the items can be chosen from the first n − 1 items under the restriction that the total weight cannot exceed W − wn. Therefore, the principle of optimality applies.