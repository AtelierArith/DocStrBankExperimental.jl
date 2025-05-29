```
XPRSchgrowtype(prob, nrows, rowind, rowtype)::prob
```

Used to change the type of a row in the matrix.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `nrows::Integer`: Number of rows to change.
  * `rowind::AbstractVector{Integer}`: Integer array of length `nrows` containing the indices of the rows.
  * `rowtype::AbstractVector{Cchar}`: Character array of length `nrows` giving the new row types: Lindicates a `<=` row; Eindicates an = row; Gindicates a `>=` row; Rindicates a range row; Nindicates a free row.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSchgrowtype](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSchgrowtype.html) in the C API.
