```
XPRSgetdualray(prob, ray)::ray, hasray
```

Retrieves a dual ray (dual unbounded direction) for the current problem, if the problem is found to be infeasible.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `ray::Union{XPRSallocatable,AbstractVector{Float64}}`: Double array of length ROWS to hold the ray. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you.

# Return values

  * `ray::AbstractVector{Float64}`: Double array of length ROWS to hold the ray.
  * `hasray::Int32`: This variable will be set to 1 if the Optimizer is able to return a dual ray, 0 otherwise.

See also the documentation of the correponding function [XPRSgetdualray](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetdualray.html) in the C API.
