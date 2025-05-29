```
XPRSloadlp64(prob, probname, ncols, nrows, rowtype, rhs, rng, objcoef, start, collen, rowind, rowcoef, lb, ub)::prob
```

Enables the user to pass a matrix directly to the Optimizer, rather than reading the matrix from a file.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `probname::Union{Nothing,AbstractString}`: A string of up to MAXPROBNAMELENGTH characters containing a names for the problem.
  * `ncols::Integer`: Number of structural columns in the matrix.
  * `nrows::Integer`: Number of rows in the matrix (not including the objective).
  * `rowtype::AbstractVector{Cchar}`: Character array of length `nrows` containing the row types: Lindicates a `<=` constraint; Eindicates an = constraint; Gindicates a `>=` constraint; Rindicates a range constraint; Nindicates a nonbinding constraint.
  * `rhs::AbstractVector{Number}`: Double array of length `nrows` containing the right hand side coefficients of the rows.
  * `rng::AbstractVector{Number}`: Double array of length `nrows` containing the range values for range rows.
  * `objcoef::AbstractVector{Number}`: Double array of length `ncols` containing the objective function coefficients.
  * `start::AbstractVector{Integer}`: Integer array containing the offsets in the `rowind` and `rowcoef` arrays of the start of the elements for each column.
  * `collen::AbstractVector{Integer}`: Integer array of length `ncols` containing the number of nonzero elements in each column.
  * `rowind::AbstractVector{Integer}`: Integer array containing the row indices for the nonzero elements in each column.
  * `rowcoef::AbstractVector{Number}`: Double array containing the nonzero element values; length as for `rowind`.
  * `lb::AbstractVector{Number}`: Double array of length `ncols` containing the lower bounds on the columns.
  * `ub::AbstractVector{Number}`: Double array of length `ncols` containing the upper bounds on the columns.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSloadlp64](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSloadlp64.html) in the C API.
