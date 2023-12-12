---
title: 'MultiPrecisionArrays.jl: A Julia package for iterative refinement'
tags:
  - Julia
  - mathematics
  - numerical analysis
  - linear equations
authors:
  - name: C. T. Kelley
    orcid: 0000-0003-2791-0648
#    affiliation: 1
affiliations:
  - name: North Carolina State University, Raleigh NC, USA
#    index: 1
date: 18 July 2023
bibliography: paper.bib
---

# Summary

[MultiPrecisionArrays.jl](https://github.com/ctkelley/MultiPrecisionArrays.jl) provides data structures and
solvers for several variations of iterative refinement (IR). IR can speed up an LU matrix factorization 
by factoring a low precision copy and using the low precision factorization in a residual correction loop.
The additional storage cost is the low precision copy, so IR is at time vs storage tradeoff. IR is an old
algorithm and a good account of the classical theory is in @higham:1996 .

# Statement of need

Who cares?

# Mathematics

This package will make solving dense systems of linear equations faster by using the LU factorization and IR. It is limited to LU for now. A very generic description of this for solving a linear systrem $A x = b$ is

$A x = b$

__IR(A, b)__

- $x = 0$

- $r = b$
  
- Factor $A = LU$ in a lower precision
  
- While $\|| r \||$ is too large
  
  - $d = (LU)^{-1} r$
    
  - $x = x + d$
    
  - $r = b - Ax$
    
- end

In Julia, a code to do this would solve the linear system $A x = b$ in double precision by using a
factorization in a lower precision, say single, within a residual correction iteration. This means that one would need
to allocate storage for a copy of $A$ in the lower precision and factor that copy. Then one has to determine what the line
$d = (LU)^{-1} r$ means. Do you cast $r$ into the lower precison before the solve or not? __MultiPrecisionArrays.jl__ provides
data structures and solvers to manage this. The __MPArray__ structure lets you preallocate $A$, the low precision copy, and the residual $r$.
The factorizations factor the low-precision copy and the solvers use that factorization and the original high-precision matrix to run
the while loop in the algorithm.

IR is a perfect example of a storage/time tradeoff.
To solve a linear system $A x = b$ in $R^N$ with IR,
one incurs the storage penalty of making a low
precision copy of $A$ and reaps the benefit of only having to
factor the low precision copy.

# Test citations

@kelley:2022b is a book. @kelley:2022a is a paper.

@kelley:2023a is the newest paper

The package lives here @kelley2023b

# References
