```
XPRSaddobj(prob, ncols, colind, objcoef, priority, weight)::prob
```

Appends an objective function with the given coefficients to a multi-objective problem.

The weight and priority of the objective are set to the given values.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `ncols::Integer`: Number of objective function coefficient elements to add.
  * `colind::AbstractVector{Integer}`: Integer array of length `ncols` containing the indices of the columns whose objective coefficients will change.
  * `objcoef::AbstractVector{Number}`: Double array of length `ncols` giving the new objective function coefficients.
  * `priority::Integer`: The priority for the objective function.
  * `weight::Float64`: The weight for the objective function.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSaddobj](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSaddobj.html) in the C API.
