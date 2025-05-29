```
XPRSgetcallbackredcosts(prob, djs, first, last)::available, djs
```

Returns the reduced costs from the solution associated with the current callback.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `djs::Union{XPRSallocatable,AbstractVector{Float64}}`: Double array of length `last-first+1` where the reduced costs of the variables will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you.
  * `first::Integer`: First column whose reduced cost to return.
  * `last::Integer`: Last column whose reduced cost to return.

# Return values

  * `available::Int32`: This variable will be set to 1 if a dual solution is available.
  * `djs::AbstractVector{Float64}`: Double array of length `last-first+1` where the reduced costs of the variables will be returned.

See also the documentation of the correponding function [XPRSgetcallbackredcosts](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetcallbackredcosts.html) in the C API.
