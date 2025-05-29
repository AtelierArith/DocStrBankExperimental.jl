```
XPRSgetobj(prob, objcoef, first, last)::objcoef
```

Returns the objective function coefficients for the columns in a given range.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `objcoef::Union{XPRSallocatable,AbstractVector{Float64}}`: Double array of length `last-first+1` where the objective function coefficients are to be placed. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you.
  * `first::Integer`: First column in the range.
  * `last::Integer`: Last column in the range.

# Return value

  * `objcoef::AbstractVector{Float64}`: Double array of length `last-first+1` where the objective function coefficients are to be placed.

See also the documentation of the correponding function [XPRSgetobj](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetobj.html) in the C API.
