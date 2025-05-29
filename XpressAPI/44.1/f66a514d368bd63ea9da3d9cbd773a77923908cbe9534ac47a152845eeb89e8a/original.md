```
XPRS_bo_getbounds(bo, branch, maxbounds, bndtype, colind, bndval)::nbounds, bndtype, colind, bndval
```

Returns the bounds for a branch of a user branching object.

# Arguments

  * `bo::XPRSbranchobject`: The branching object to inspect.
  * `branch::Integer`: The number of the branch to get the bounds for.
  * `maxbounds::Integer`: Maximum number of bounds to return.
  * `bndtype::Union{XPRSallocatable,Nothing,AbstractVector{Cchar}}`: Character array of length `maxbounds` where the types of bounds will be returned: LLower bound. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `colind::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Integer array of length `maxbounds` where the column indices will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `bndval::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of length `maxbounds` where the bound values will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.

# Return values

  * `nbounds::Int32`: Location where the number of bounds for the given branch should be returned.
  * `bndtype::Union{Nothing,AbstractVector{Cchar}}`: Character array of length `maxbounds` where the types of bounds will be returned: LLower bound.
  * `colind::Union{Nothing,AbstractVector{Int32}}`: Integer array of length `maxbounds` where the column indices will be returned.
  * `bndval::Union{Nothing,AbstractVector{Float64}}`: Double array of length `maxbounds` where the bound values will be returned.

See also the documentation of the correponding function [XPRS*bo*getbounds](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRS_bo_getbounds.html) in the C API.
