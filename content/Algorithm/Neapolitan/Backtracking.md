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
- To summarize, backtracking consists of doing a depth-first search of a state space tree, checking whether each node is promising, and, if it is nonpromising, backtracking to the node’s parent. This is called pruning the state space tree, and the subtree consisting of the visited nodes is called the pruned state space tree.

![[backtracking-pic1.png]]

- The root of the state space tree is passed to checknode at the top level. A visit to a node consists of first checking whether it is promising. If it is promising and there is a solution at the node, the solution is printed. If there is not a solution at a promising node, the children of the node are visited. The function promising is different in each application of backtracking. We call it the promising function for the algorithm.
- A backtracking algorithm is identical to a depth-first search, except that the children of a node are visited only when the node is promising and there is not a solution at the node.
- A computer implementation of the recursive algorithm accomplishes backtracking by popping the activation record for a nonpromising node from the stack of activation records.
- In some backtracking algorithms a solution can be found before reaching a leaf in the state space tree.
- Notice that a backtracking algorithm need not actually create a tree. Rather, it only needs to keep track of the values in the current branch being investigated. This is the way we implement backtracking algorithms. We say that the state space tree exists implicitly in the algorithm because it is not actually constructed.
- A more efficient algorithm:
![[backtracking-pic2.png]]


- # The Sum-of-Subsets Problem


# Graph Coloring


# The 0-1 Knapsack Problem