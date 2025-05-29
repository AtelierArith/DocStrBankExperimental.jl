```
XPRSgetlastbarsol(prob, x, slack, duals, djs)::x, slack, duals, djs, status
```

Used to obtain the last barrier solution values following optimization that used the barrier solver.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `x::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of length ORIGINALCOLS where the values of the primal variables will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `slack::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of length ORIGINALROWS where the values of the slack variables will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `duals::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of length `ORIGINALROWS` where the values of the dual variables (cBTB-1) will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `djs::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of length `ORIGINALCOLS` where the reduced cost for each variable (cT-cBTB-1A) will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.

# Return values

  * `x::Union{Nothing,AbstractVector{Float64}}`: Double array of length ORIGINALCOLS where the values of the primal variables will be returned.
  * `slack::Union{Nothing,AbstractVector{Float64}}`: Double array of length ORIGINALROWS where the values of the slack variables will be returned.
  * `duals::Union{Nothing,AbstractVector{Float64}}`: Double array of length `ORIGINALROWS` where the values of the dual variables (cBTB-1) will be returned.
  * `djs::Union{Nothing,AbstractVector{Float64}}`: Double array of length `ORIGINALCOLS` where the reduced cost for each variable (cT-cBTB-1A) will be returned.
  * `status::Int32`: Status of the last barrier solve.

See also the documentation of the correponding function [XPRSgetlastbarsol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetlastbarsol.html) in the C API.
