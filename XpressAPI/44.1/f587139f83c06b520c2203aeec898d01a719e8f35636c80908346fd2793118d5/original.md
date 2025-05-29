```
XPRSrhssa(prob, nrows, rowind, lower, upper)::lower, upper
```

Returns upper and lower sensitivity ranges for specified right hand side (RHS) function coefficients.

If the RHS coefficients are varied within these ranges the current basis remains optimal and the reduced costs remain valid.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `nrows::Integer`: The number of RHS coefficients for which sensitivity ranges are required.
  * `rowind::AbstractVector{Integer}`: Integer array of length `nrows` containing the indices of the rows whose RHS coefficients sensitivity ranges are required.
  * `lower::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of length `nrows` where the RHS lower range values are to be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `upper::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of length `nrows` where the RHS upper range values are to be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.

# Return values

  * `lower::Union{Nothing,AbstractVector{Float64}}`: Double array of length `nrows` where the RHS lower range values are to be returned.
  * `upper::Union{Nothing,AbstractVector{Float64}}`: Double array of length `nrows` where the RHS upper range values are to be returned.

See also the documentation of the correponding function [XPRSrhssa](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSrhssa.html) in the C API.
