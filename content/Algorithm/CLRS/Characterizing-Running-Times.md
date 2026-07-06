---
title: Characterizing Running Times
publish: true
date created: 2026-07-05
---
### O-notation, $\Omega$-notation, and $\Theta$-notation
- The order of growth of the running time of an algorithm gives a simple way to characterize the algorithm’s efficiency and also allows us to compare it with alternative algorithms.
- Asymptotic efficiency: That is, we are concerned with how the running time of an algorithm increases with the size of the input in the limit, as the size of the input increases without bound.
- O -notation characterizes an upper bound on the asymptotic behavior of a function. In other words, it says that a function grows no faster than a certain rate, based on the highest-order term.
- $\Omega$-notation characterizes a lower bound on the asymptotic behavior of a function. In other words, it says that a function grows at least as fast as a certain rate, based -as in O -notation-on the highest-order term.
- $\Theta$-notation characterizes a tight bound on the asymptotic behavior of a function. It says that a function grows precisely at a certain rate, based-once again-on the highest-order term. Put another way, $\Theta$-notation characterizes the rate of growth of the function to within a constant factor from above and to within a constant factor from below. These two constant factors need not be equal.
### Asymptotic notation: formal definitions
![[clrs-pic1.png]]
The definitions are the same as in Neapolitan.
![[clrs-pic3.png]]

![[clrs-pic2.png]]

![[clrs-pic4.png]]

![[clrs-pic5.png]]

### Standard notations and common functions
some math shit. 