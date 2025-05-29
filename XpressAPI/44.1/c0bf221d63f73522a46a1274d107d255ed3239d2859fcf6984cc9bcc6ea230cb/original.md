```
XPRScalcsolinfo(prob, solution, duals, property)::value
```

Calculates the required property of a solution, like maximum infeasibility of a given primal and dual solution.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `solution::AbstractVector{Number}`: Double array of length COLS that holds the solution.
  * `duals::AbstractVector{Number}`: Double array of length ROWS that holds the dual solution.
  * `property::Integer`: Defined the property to be calculated.

# Return value

  * `value::Float64`: Pointer to a double where the calculated value is returned.

See also the documentation of the correponding function [XPRScalcsolinfo](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRScalcsolinfo.html) in the C API.
