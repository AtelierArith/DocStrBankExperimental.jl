```
XPRSgetnlpsol(prob, x, slack, duals, djs)::x, slack, duals, djs
```

**Deprecated**Use XPRSgetsolution and related functions instead.

Obtain the current SLP solution values

# Arguments

  * `prob::XPRSprob`: The current SLP problem.
  * `x::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of length `XSLP_ORIGINALCOLS` to hold the values of the primal variables. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `slack::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of length `XSLP_ORIGINALROWS` to hold the values of the slack variables. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `duals::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of length `XSLP_ORIGINALROWS` to hold the values of the dual variables. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `djs::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of length `XSLP_ORIGINALCOLS` to hold the reduced costs of the primal variables. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.

# Return values

  * `x::Union{Nothing,AbstractVector{Float64}}`: Double array of length `XSLP_ORIGINALCOLS` to hold the values of the primal variables.
  * `slack::Union{Nothing,AbstractVector{Float64}}`: Double array of length `XSLP_ORIGINALROWS` to hold the values of the slack variables.
  * `duals::Union{Nothing,AbstractVector{Float64}}`: Double array of length `XSLP_ORIGINALROWS` to hold the values of the dual variables.
  * `djs::Union{Nothing,AbstractVector{Float64}}`: Double array of length `XSLP_ORIGINALCOLS` to hold the reduced costs of the primal variables.

See also the documentation of the correponding function [XPRSgetnlpsol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetnlpsol.html) in the C API.
