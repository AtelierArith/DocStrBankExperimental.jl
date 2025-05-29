```
XPRSloadsecurevecs(prob, nrows, ncols, rowind, colind)::prob
```

Allows the user to mark rows and columns in order to prevent the presolve removing these rows and columns from the matrix.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `nrows::Integer`: Number of rows to be marked.
  * `ncols::Integer`: Number of columns to be marked.
  * `rowind::AbstractVector{Integer}`: Integer array of length `nrows` containing the rows to be marked.
  * `colind::AbstractVector{Integer}`: Integer array of length `ncols` containing the columns to be marked.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSloadsecurevecs](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSloadsecurevecs.html) in the C API.
