```
XPRSgetbasisval(prob, row, col)::rowstat, colstat
```

Returns the current basis status for a specific column or row.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `row::Integer`: Row index to get the row basis status for.
  * `col::Integer`: Column index to get the column basis status for.

# Return values

  * `rowstat::Int32`: Integer pointer where the value of the row basis status will be returned.
  * `colstat::Int32`: Integer pointer where the value of the column basis status will be returned.

See also the documentation of the correponding function [XPRSgetbasisval](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetbasisval.html) in the C API.
