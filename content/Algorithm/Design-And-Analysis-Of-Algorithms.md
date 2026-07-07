---
title: Design And Analysis Of Algorithms - A Summery
publish: true
date created: 2026-07-06
---
## Strassen's Matrix Multiplication
- $O(n^{2.81})$

- Divide and Conquer. We divide the matrixes in 4 parts each and we perform the strassen's additions and multiplications on these 8 elements and will solve it for the smaller instances. Strassen uses 7 phrases to claculate the elements and that's why it's faster.

- without strassen's : $8T(n/2) + n^2$ if n > 2. 
  
  which is going to be $O(n^3)$

- With strassen: $7T(n/2) + n^2$ which is going to be $O(n^{2.81)}$
## Matrix Chain Multiplication
- $O(n^3)$

- DP.

- How to parantethize the multiplications of the matrixes to have the minimum number of multiplications. We also want to know where to put the parantetheses.

- We have 2 tables, m and s. We will write the multiplications in the m table and the place of the parathesis in the s table. We will use s to determine the optimal place of the parathesis.

- The formula: $m[i,j] = min \{m[i,k] + m[k+1, j] +d_{i-1} \times d_k \times d_j \}$ and $i \leq k < j$. $M[i][i] = 0$ 
## Floyd's Algorithms with DP
- $O(n^3)$

- all pair shortest path

- find the shortest path between every pair of vertices.

- we could apply dijkstra for each vertex which will give us $O(n^3)$. 

- for dp, we solve it by preparing matrices.  

- formula: $A^k[i,j] = min\{A^{k-1} [i,j], A^{k-1}[i,k] + A^{k-1}[k,j]\}$

- Neapolitan uses a companion matrix $P$ (where $P[i][j]$ stores the highest index intermediate vertex $k$ on the shortest path from $i$ to $j$).

- If $P[i][j] = 0$, there are no intermediate vertices (direct edge).
    
- If $P[i][j] = k$, you recursively print the path from $i$ to $k$, then print $k$, then recursively print the path from $k$ to $j$.
## TSP
vising every city with the shortest path and we wanna go back to the city we came from.
### TSP with DP:
- $O(n \times 2^n)$.

-  formula: $g(i,S) = min_{k \in S}\{ c_{ik} + g(k, S - \{k\})\}$

- bottom-up. 

### TSP with Branch-and-Bound:
- state space tree. (it's gonna look the same as the one in DP). The nodes are generated in level order. 

- first we have a matrix for the distances, then we will try to reduce it. It means that in every column and every row, we find the minimum, subtract the values by that number and then we will add the minimums together. (at least the cost of tour will be this number). That would be the cost for the first node which is 1. Now we have the matrix for node 1.  We have an upper bound which is infinity at first. (it's the cost. once we reach a leaf, we'll update it.)

- now we go to the second node, which is the child of node 1. node 2. the first row and the second column will become infinity. When we go to 2 from 1, we can't go back to it, so we make the <2,1> as infinity. We again reduce the matrix. (which was for node 1). The cost of this node will be the c(1,2) (from our initial matrix) plus the reduced amount of the initial matrix plus the reduced amount from the reduced matrix of the this matrix. (the initial matrix is the for the node we came from and the current matrix is for the node we're currently at). after writing down the cost of the children of 1, we choose the one that has the minimum cost and continue it. (least cost branch-and-bound, we explore the children of the minimum one. after calculating the children's cost, we compare the costs through out the tree and continue with the minimum one). When we reach the leaf, we update the upper bound(it's infinity at first) and write down the cost of the leaf. Then we check the nodes that are greater than the upper and prune them.


## Prim's Algorithm (Greedy)
- $O(n^2)$

- ### Spanning Tree:
subgraph of a graph, includes all the vertices and doesn't create a cycle. has n -1 edges. Two ways to find the minimum spanning tree: Prim's and Kruskal's. We find the spanning tree for connected graphs.

- We add nodes to our set, by taking the minimum edge connected to the vertices we have in our set. (we wouldn't create a cycle 'cuase we never look at the edges where both endpoints are already in the set.)
## Kruskal's Algorithm (Greedy)
- $O(E log E)$
n^2 logn
- In sparse trees: $O(n log n)$ (also using min heap)

- We order the edges, start with the minimum, if it doesn't create a cycle we add it. 
## Dijkstra
- $O(elogn)$ (binary heap) where e is the number of roads and n is the number of cities. or n^2 using an array.

- Greedy.

- Single source shortest path problem.

- Updating the distances is called relaxation.
	```
	if (d[u] + c(u, v) < d[v])
		d[v] = d[u] + c(u, v)
	```

- at first, we try to write down the distances from v1, if there is a direct edge we write it. No direct edge = infinity. Then we choose the shortest one and go to that node. Then we calculate the distance of the path going from that node and choose the shortest one and update the distance for the node we are going to.  

- After you finish relaxing the neighbors of your current node, your next step is to look at **the entire set of unvisited nodes** and pick the one with the smallest current distance. (a node might have a lesser cost from the previous steps)

- 1. **Repeatedly pick** the unvisited node with the **globally minimum** cost.

2. From that node, **relax** all the edges to the nodes you can go to (its neighbors).
## Knapsack 0-1
### Greedy:
- $O(nlogn)$

- we order the items based on the profit/weight ratio. We take the biggest item each time.(the one with the highest profit by weight) The greedy method wouldn't always give us the optimal solution. We take an item as long as it doesn't exceed the weight. When we place an item, we subtrack it form the capacity and then we go to choose the next item.

### DP:
If we want to check all the states, it's gonna be $O(2^n)$. 
- $O(nW)$. n items and W is the number of columns. So nW.

- We have a table called V. 
![[summer-1.png]]

- The formula: $V[i,w] = max\{V[i-1,w], V[i-1,w-w[i]] + P[i]\}$
### Refined DP:
- $\Theta(2^n)$

- W can be as large as n!. So we want to improve the DP algorithm. We don't have to compute every entry. We go backward to see which entries we need and we stop when n =1 or $w \leq 0$. 
###  Backtracking:
- $O(2^n)$

- we don't order the items. It's like brute force.

- with pruning:  If that maximum possible profit **≤ current best profit**, stop exploring that branch immediately.
### Branch-And-Bound
- we order the items.
#### BFS:
- $O(n \times 2^n)$

#### Best-First:
- $O(n \times 2^n \times log n)$ 

#### Without pruning:
- $O(n \times 2^n)$

## n-queen with Backtracking

- state space tree.

- We have a start and the children would be the elements of a row. Queens can't be in the same row, column or diagonal.

## The sum-of-subsets problem with backtracking

- if $weight \ + \ totalRemaining \  < W$ the node is nonpromising.

-  The goal is to find all subsets of the integers that sum to W. 

- 0-1.

## Graph Coloring with Backtracking

- We have a start and then the children will be the colors. Each level is for a vertex. We prune a branch if 2 adjacent nodes have the same colors. 


## Huffman Code
- Greedy.

- $O(n logn)$

- Compression technique. It is used for reducing the size of data. 

- imagine we have a message. The size would be based of bits. 

![[summery-2.png]]