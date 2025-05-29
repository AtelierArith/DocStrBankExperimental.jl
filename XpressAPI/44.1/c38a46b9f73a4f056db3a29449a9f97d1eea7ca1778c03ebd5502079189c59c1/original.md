```
XPRScalcslacks(prob, solution, slacks)::slacks
```

Calculates the row slack values for a given solution.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `solution::AbstractVector{Number}`: Double array of length COLS that holds the solution to calculate the slacks for.
  * `slacks::Union{XPRSallocatable,AbstractVector{Float64}}`: Double array of length ROWS in which the calculated row slacks are returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you.

# Return value

  * `slacks::AbstractVector{Float64}`: Double array of length ROWS in which the calculated row slacks are returned.

See also the documentation of the correponding function [XPRScalcslacks](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRScalcslacks.html) in the C API.
