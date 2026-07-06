---
title: Branch and Bound
publish: true
date created: 2026-06-19
---
- The differences are that the branch-and-bound method (1) does not limit us to any particular way of traversing the tree and (2) is used only for optimization problems.

- the branch-and-bound algorithm developed here is an improvement on the backtracking algorithm.

- A branch-and-bound algorithm computes a number (bound) at a node to determine whether the node is promising. The number is a bound on the value of the solution that could be obtained by expanding beyond the node. If that bound is no better than the value of the best solution found so far, the node is nonpromising. Otherwise, it is promising. Because the optimal value is a minimum in some problems and a maximum in others, by “better” we mean smaller or larger, depending on the problem. As is the case for backtracking algorithms, branch-and-bound algorithms are ordinarily exponential-time (or worse) in the worst case. However, they can be very efficient for many large instances.

- Related to the backtracking method of Knapsack 0-1, Besides using the bound to determine whether a node is promising, we can compare the bounds of promising nodes and visit the children of the one with the best bound.

- The implementation of the approach is a simple modification of another methodical approach called breadth-first search with branch-and-bound pruning.best-first search with branch-and-bound pruning.

# Illustrating Branch-and-Bound with the 0-1 Knapsack Problem
I couldn't understand the book on this part so I used AI to teach myself. 
### Knapsack 0-1 using backtracking
**Without Pruning/Bounding**:
First we make the state space tree. We will try to find the best solution which is the maximum profit. In the tree, for each object, we have 2 options. 1 is for choosing the object and 0 is for not choosing the object (to put it in the knapsack). If we choose the object, we write down the sum of the profits so far.(current object's profit plus the profits of the previous objects.) We do the same for the weight as well. When we want to choose an object, if the total weight exceeds the weight of the knapsack, we can't choose this object and we cross this node. We continue by choosing the 0 branch and try to consider other objects. If we reach a leaf, and total weight isn't more than the weight of the knapsack, we have a solution. We do a depth-first-search. We explore the include branch first. We continue searching all the branches to find the maximum profit among all feasible solutions. 

**With pruning/Bounding**:
Without pruning, the backtracking method would check all the $2^n$ nodes. Therefore we use branch and bound:

- We compute an upper bound on the profit that can be achieved using a node.

- if the upper bound is less than the current profit, we prune the branch. 

- **Bounding** = Calculating the **maximum possible profit** you could ever get from a node (even in the best-case scenario).

- **Pruning** = If that maximum possible profit **≤ current best profit**, stop exploring that branch immediately.

- For any node (where you've already decided on some items), you need to compute the **maximum profit you could still achieve** from the remaining items.

  ```
	  Bound = Current Profit + 
        (Profit of all fully taken remaining items) + 
        (Fraction of next item that fits)
  ```

- Items should be sorted by **profit/weight ratio** (descending) for the bound calculation! This ordering ensures the algorithm can get a tight upper bound on the potential profit of a node, which is key to effective pruning.

### Knapsack 0-1 using Branch-and-Bound
We consider 2 strategies. 
1. **BFS (breadth-First-Search) with branch and bound pruning:**
	Explore the tree **level by level** (like BFS), but **prune** any node whose upper bound can't beat the best solution found so far.
2. **Best-First Search with Branch-and-Bound Pruning:**
	 Always explore the node with the **highest upper bound** first. Use a **priority queue (max-heap)** where the priority is the bound value.
	 After visiting all the children of a given node, we can look at all the promising, unexpanded nodes and expand beyond the one with the best bound.In this way, we often arrive at an optimal solution more quickly than if we simply proceeded blindly in a predetermined order.
	 The implementation of best-first search consists of a simple modification to breadth-first search. Instead of using a queue, we use a priority queue. The priority queue **does NOT** change the tree structure or reorder nodes in the tree. Instead, it changes the **order in which we EXPLORE** the already-existing tree nodes.
	 so in best-first, it means after we make the state space tree, we calculate the bound of the nodes, and we stat by root, which has the most bound. then between include and exclude, we check which one has the higher bound and we choose it, then we check its children to see which one has the higher bound and we repeat this process until we reach a leaf. (we might reach a leaf, not neccessirly) which will be a candidate key. We continue exploring the nodes 'cause you might find a better solution. we only stop when the **next node's bound ≤ our current best solution**. 1. When we finish exploring one path, we **look at the heap**. We Go to the MOST PROMISING Node Anywhere. **We don't go back to the previous level, and we don't go back to the start.** Instead, we look at our **heap (to-do list)** and pick the **most promising node** from ANYWHERE in the tree that we haven't explored yet.  So after we are down a path, we pick a node from the priority queue and if it can beat our best solution so far, we continue it. else we prune it.

So for Knapsack problem we had several solutions:
- backtracking without pruning. $O(2^n)$
- branch and bound with DFS. (backtracking with pruning)$O(n \times 2^n)$
- branch and bound with BFS. $O(n \times 2^n)$
- branch and bound with Best-First search.(explores fewer nodes.) $O(n × 2ⁿ × log n)$
- DP $(O(n \times w)$)
- Greedy $O(nlogn)$

# The Traveling Salesperson Problem
- An obvious state space tree for this problem is one in which each vertex other than the starting one is tried as the first vertex (after the starting one) at level 1, each vertex other than the starting one and the one chosen at level 1 is tried as the second vertex at level 2, and so on.
- I watched Abdul Bari for this.