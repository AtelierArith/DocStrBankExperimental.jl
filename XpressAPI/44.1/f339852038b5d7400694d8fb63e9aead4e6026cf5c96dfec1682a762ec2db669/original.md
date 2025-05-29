```
XPRS_bo_addrows(bo, branch, nrows, ncoefs, rowtype, rhs, start, colind, rowcoef)::Nothing
```

Adds new constraints to a branch of a user branching object.

# Arguments

  * `bo::XPRSbranchobject`: The user branching object to modify.
  * `branch::Integer`: The number of the branch to add the new constraints for.
  * `nrows::Integer`: Number of new constraints to add.
  * `ncoefs::Integer`: Number of non-zero coefficients in all new constraints.
  * `rowtype::AbstractVector{Cchar}`: Character array of length `nrows` indicating the type of constraints to add: LLess than type.
  * `rhs::AbstractVector{Number}`: Double array of length `nrows` containing the right hand side values.
  * `start::AbstractVector{Integer}`: Integer array of length `nrows` containing the offsets of the `colind` and `rowcoef` arrays of the start of the non zero coefficients in the new constraints.
  * `colind::AbstractVector{Integer}`: Integer array of length `ncoefs` containing the column indices for the non zero coefficients.
  * `rowcoef::AbstractVector{Number}`: Double array of length `ncoefs` containing the non zero coefficient values.

See also the documentation of the correponding function [XPRS*bo*addrows](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRS_bo_addrows.html) in the C API.
