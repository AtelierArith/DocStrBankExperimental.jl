```
XPRSgetobjn(prob, objidx, objcoef, first, last)::objcoef
```

For a given objective function, returns the objective coefficients for the columns in a given range.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `objidx::Integer`: Index of the objective function whose coefficients to return.
  * `objcoef::Union{XPRSallocatable,AbstractVector{Float64}}`: Double array of length `last-first+1` where the objective function coefficients are to be placed. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you.
  * `first::Integer`: First column in the range.
  * `last::Integer`: Last column in the range.

# Return value

  * `objcoef::AbstractVector{Float64}`: Double array of length `last-first+1` where the objective function coefficients are to be placed.

See also the documentation of the correponding function [XPRSgetobjn](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetobjn.html) in the C API.
