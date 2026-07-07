---
title: Backtracking
publish: true
date created: 2026-06-19
---
# The Backtracking Technique
- Backtracking is used to solve problems in which a sequence of objects is chosen from a specified set so that the sequence satisfies some criterion. The classic example of the use of backtracking is in the n-Queens problem.

- Backtracking is a modified depth-first search of a tree (here “tree” means a rooted tree)
	- A preorder tree traversal is a depth-first search of the tree.
	- This means that the root is visited first, and a visit to a node is followed immediately by visits to all descendants of the node. Although a depth-first search does not require that the children be visited in any particular order, we will visit the children of a node from left to right.
	
- state space tree.
- Each path from the root to a leaf is a candidate solution.
- Backtracking is the procedure whereby, after determining that a node can lead to nothing but dead ends, we go back (“backtrack”) to the node’s parent and proceed with the search on the next child.

- We call a node nonpromising if when visiting the node we determine that it cannot possibly lead to a solution. Otherwise, we call it promising.

- To summarize, backtracking consists of doing a depth-first search of a state space tree, checking whether each node is promising, and, if it is nonpromising, backtracking to the node’s parent. This is called pruning the state space tree, and the subtree consisting of the visited nodes is called the pruned state space tree![[backtracking-pic1.png]]

- The root of the state space tree is passed to checknode at the top level. A visit to a node consists of first checking whether it is promising. If it is promising and there is a solution at the node, the solution is printed. If there is not a solution at a promising node, the children of the node are visited. The function promising is different in each application of backtracking. We call it the promising function for the algorithm.

- A backtracking algorithm is identical to a depth-first search, except that the children of a node are visited only when the node is promising and there is not a solution at the node.

- A computer implementation of the recursive algorithm accomplishes backtracking by popping the activation record for a nonpromising node from the stack of activation records.

- In some backtracking algorithms a solution can be found before reaching a leaf in the state space tree.

- Notice that a backtracking algorithm need not actually create a tree. Rather, it only needs to keep track of the values in the current branch being investigated. This is the way we implement backtracking algorithms. We say that the state space tree exists implicitly in the algorithm because it is not actually constructed.

- A more efficient algorithm:![[backtracking-pic2.png]]

# The Sum-of-Subsets Problem
- Specifically, in the Sum-of-Subsets problem, there are n positive integers (weights) wi and a positive integer W. The goal is to find all subsets of the integers that sum to W. ![[backtracking-pic3.png]]
- If we sort the weights in nondecreasing order before doing the search, there is an obvious sign telling us that a node is nonpromising. If the weights are sorted in this manner, then wi+1 is the lightest weight remaining when we are at the ith level. Let weight be the sum of the weights that have been included up to a node at level i. If There is another, less obvious sign telling us that a node is nonpromising. If, at a given node, adding all the weights of the remaining items to weight does not make weight at least equal to W, then weight could never become equal to W by expanding beyond the node. This means that if total is the total weight of the remaining weights, a node is nonpromising if $$weight \ + \ total \  < W$$
- Each path from the root to a leaf is a candidate solution.

- Algorithm: ![[backtracking-pic4.png]]
- some notes on page 245 which are worthy of consideration.

- even though the worst case is exponential, the algorithm can be efficient for many large instances.
# Graph Coloring
- The m-Coloring problem concerns finding all ways to color an undirected graph using at most m different colors, so that no two adjacent vertices are the same color. We usually call the m-Coloring problem a unique problem for each value of m.

- A graph is called planar if it can be drawn in a plane in such a way that no two edges cross each other.

- The m-Coloring problem for planar graphs is to determine how many ways the map can be colored, using at most m colors, so that no two adjacent regions are the same color.

- Algorithm: ![[backtracking-pic6.png]]
- ![[backtracking-pic7.png]]

# The 0-1 Knapsack Problem
## A Backtracking Algorithm for the 0-1 Knapsack Problem
- we back-track a little differently. If the items included up to a node have a greater total profit than the best solution so far, we change the value of the best solution so far. However, we may still find a better solution at one of the node’s descendants (by stealing more items). Therefore, for optimization problems we always visit a promising node’s children. ![[backtracking-pic5.png]]
- Next we apply this technique to the 0-1 Knapsack problem. First let’s look for signs telling us that a node is nonpromising. An obvious sign that a node is nonpromising is that there is no capacity left in the knapsack for more items. Therefore, if weight is the sum of the weights of the items that have been included up to some node, the node is nonpromising if $weight \ \geq W$.

- It is nonpromising even if weight equals W because, in the case of optimization problems, “promising” means that we should expand to the children.  We can use considerations from the greedy approach to find a less obvious sign. Recall that this approach failed to give an optimal solution to this problem in Section 4.5. Here we will only use greedy considerations to limit our search; we will not develop a greedy algorithm. To that end, we first order the items in nonincreasing order according to the values of pi/wi, where wi and pi are the weight and profit, respectively, of the ith item. Suppose we are trying to determine whether a particular node is promising. No matter how we choose the remaining items, we cannot obtain a higher profit than we would obtain if we were allowed to use the restrictions in the Fractional Knapsack problem from this node on. (Recall that in this problem the thief can steal any fraction of an item taken.) Therefore, we can obtain an upper bound on the profit that could be obtained by expanding beyond that node as follows. Let profit be the sum of the profits of the items included up to the node. Recall that weight is the sum of the weights of those items. We initialize variables bound and totweight to profit and weight, respectively. Next we greedily grab items, adding their profits to bound and their weights to totweight, until we get to an item that if grabbed would bring totweight above W. We grab the fraction of that item allowed by the remaining weight, and we add the value of that fraction to bound. If we are able to get only a fraction of this last weight, this node cannot lead to a profit equal to bound, but bound is still an upper bound on the profit we could achieve by expanding beyond the node. Suppose the node is at level i, and the node at level k is the one that would bring the sum of the weights above W. Then ![[backtracking-pic8.png]]
- Read example 5.6 on page 255 carefully. 
- Algorithm:![[backtracking-pic9.png]]
  ![[backtracking-pic10.png]]
- Recall that leaves in the state space tree are automatically nonpromising because their bounds cannot be greater than maxprofit. Therefore, we should not need a check for the terminal condition that i = n in function promising. Let’s confirm that our algorithm does not need to do this check. If i = n, bound does not change from its initial value profit. Because profit is less than or equal to maxprofit, the expression bound>maxprofit is false, which means that function promising returns false. Our upper bound does not change value as we repeatedly proceed to the left in the state space tree until we reach the node at level k. (This can he seen by looking again at the first few steps in Example 5.6.) Therefore, each time a value of k is established, we can save its value and proceed to the left without calling function promising until we reach the node at the (k − 1)st level. We know that the left child of this node is nonpromising because including the kth item would bring the value of weight above W . Therefore, we proceed only to the right from this node. It is only after a move to the right that we need to call function promising and determine a new value of k.


## Comparing the Dynamic Programming Algorithm and the Backtracking Algorithm for the 0-1 Knapsack Problem
![[backtracking-pic11.png]]