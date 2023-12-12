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
solvers for several variations of iterative refinement (IR).

What is iterative refinement?

# Statement of need

Who cares?

# Mathematics

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

# Test citations

@kelley:2022b is a book. @kelley:2022a is a paper.

@kelley:2023a is the newest paper

The package lives here @kelley2023b

# References
