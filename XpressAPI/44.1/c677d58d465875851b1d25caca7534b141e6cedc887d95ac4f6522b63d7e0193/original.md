```
XPRScalcobjn(prob, objidx, solution)::objval
```

Calculates the objective value of the given objective function in a multi-objective problem.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `objidx::Integer`: Index of the objective function to calculate.
  * `solution::AbstractVector{Number}`: Double array of length `COLS` that holds the solution, or `nothing` to use the current solution.

# Return value

  * `objval::Float64`: Pointer to a double in which the calculated objective value is returned.

See also the documentation of the correponding function [XPRScalcobjn](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRScalcobjn.html) in the C API.
