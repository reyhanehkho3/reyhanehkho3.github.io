---
title: Divide and Conquer
publish: true
date created: 2026-06-19
---
# The Divide-and-Conquer Approach
The divide-and-conquer design strategy involves the following steps:
1. Divide an instance of a problem into one or more smaller instances.
2. Conquer (solve) each of the smaller instances. Unless a smaller instance is sufficiently small, use recursion to do this.
3. If necessary, combine the solutions to the smaller instances to obtain the solution to the original instance.



# Strassen’s Matrix Multiplication Algorithm

- ![[Divide-pic1.png]]
  ![[Divide-pic2.png]]
  - When the matrices are sufficiently small, we multiply in the standard way.
  - ![[Divide-pic3.png]]
- M1, M2 through M7 are computed in the same way, and then the values of C11, C12, C21, and C22 are computed. They are combined to yield C.
- Algorithm: ![[Divide-pic5.png]]
- The value of threshold is the point at which we feel it is more efficient to use the standard algorithm than it would be to call procedure strassen recursively.
- $T(n) \in \Theta(n^{2.81})$ 
![[Divide-pic4.png]]
- the standard algorithm and Strassen’s algorithm for n a power of 2: If we ignore for the moment the overhead involved in the recursive calls, Strassen’s algorithm is always more efficient in terms of multiplications, and for large values of n, Strassen’s algorithm is more efficient in terms of additions/subtractions.
# When Not to Use Divide-and-Conquer
If possible, we should avoid divide-and-conquer in the following two cases:
1. An instance of size n is divided into two or more instances each almost of sizen.
2. An instance of size n is divided into almost n instances of size n/c, where c is a constant.
- The first one lead to an exponential-time algorithm. For example, the first case would be like Napoleon dividing an opposing army of 30,000 soldiers into two armies of 29,999 soldiers (if this were somehow possible). Rather than dividing his enemy, he has almost doubled their number! If Napoleon did this, he would have met his Waterloo much sooner.
- the secon leads to a $n^{\Theta(log n)}$.
- Neither of these is acceptable for large values of n
- Sometimes, on the other hand, a problem requires exponentiality, and in such a case there is no reason to avoid the simple divide-and-conquer solution.