```
XPRS_bo_addbounds(bo, branch, nbounds, bndtype, colind, bndval)::Nothing
```

Adds new bounds to a branch of a user branching object.

# Arguments

  * `bo::XPRSbranchobject`: The user branching object to modify.
  * `branch::Integer`: The number of the branch to add the new bounds for.
  * `nbounds::Integer`: Number of new bounds to add.
  * `bndtype::AbstractVector{Cchar}`: Character array of length `nbounds` indicating the type of bounds to add: LLower bound.
  * `colind::AbstractVector{Integer}`: Integer array of length `nbounds` containing the column indices for the new bounds.
  * `bndval::AbstractVector{Number}`: Double array of length `nbounds` giving the bound values.

See also the documentation of the correponding function [XPRS*bo*addbounds](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRS_bo_addbounds.html) in the C API.
