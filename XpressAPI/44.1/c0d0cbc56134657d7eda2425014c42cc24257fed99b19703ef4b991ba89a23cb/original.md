```
XPRSiisstatus(prob, nrows, ncols, suminfeas, numinfeas)::niis, nrows, ncols, suminfeas, numinfeas
```

Returns statistics on the Irreducible Infeasible Sets (IIS) found so far by XPRSiisfirst (IIS), XPRSiisnext (IIS `-n`) or XPRSiisall (IIS `-a`).

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `nrows::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Number of rows in the IISs. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `ncols::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Number of bounds in the IISs. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `suminfeas::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: The sum of infeasibilities in the IISs after the first phase simplex. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `numinfeas::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: The number of infeasible variables in the IISs after the first phase simplex. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.

# Return values

  * `niis::Int32`: The number of IISs found so far.
  * `nrows::Union{Nothing,AbstractVector{Int32}}`: Number of rows in the IISs.
  * `ncols::Union{Nothing,AbstractVector{Int32}}`: Number of bounds in the IISs.
  * `suminfeas::Union{Nothing,AbstractVector{Float64}}`: The sum of infeasibilities in the IISs after the first phase simplex.
  * `numinfeas::Union{Nothing,AbstractVector{Int32}}`: The number of infeasible variables in the IISs after the first phase simplex.

See also the documentation of the correponding function [XPRSiisstatus](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSiisstatus.html) in the C API.
