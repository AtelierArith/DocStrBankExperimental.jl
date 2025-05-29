```
XPRSnlpsetinitval(prob, nvars, colind, initial)::prob
```

Set the initial value of a variable

# Arguments

  * `prob::XPRSprob`: The current SLP problem.
  * `nvars::Integer`: Number of variables for which the initial value is to be set.
  * `colind::AbstractVector{Integer}`: Array of length `nvars` with index of the column for which the initial value is provided.
  * `initial::AbstractVector{Number}`: Array of length `nvars` with the initial value.

# Return value

  * `prob::XPRSprob`: The current SLP problem.

See also the documentation of the correponding function [XPRSnlpsetinitval](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSnlpsetinitval.html) in the C API.
