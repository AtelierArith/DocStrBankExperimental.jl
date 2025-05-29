```
XPRSsetindicators(prob, nrows, rowind, colind, complement)::prob
```

Specifies that a set of rows in the matrix will be treated as indicator constraints during a tree search.

An indicator constraint is made of a `condition` and a `constraint`. The `condition` is of the type "`bin = value`", where `bin` is a binary variable and `value` is either 0 or 1. The `constraint` is any matrix row (may be linear, quadratic or general nonlinear). During tree search, a row configured as an indicator constraint is enforced only when condition holds, that is only if the indicator variable `bin` has the specified value. Note that every row may only get assigned a single indicator variable and term. If a row needs to be activated by multiple different terms, the row needs to be duplicated so that each term can be assigned to a distinct row. If the indicator variable should be changed, the old term needs to be deleted first (by calling XPRSdelindicators or by calling this function with a comps argument of 0) before assigning a new one.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `nrows::Integer`: The number of indicator constraints.
  * `rowind::AbstractVector{Integer}`: Integer array of length `nrows` containing the indices of the rows that define the constraint part for the indicator constraints.
  * `colind::AbstractVector{Integer}`: Integer array of length `nrows` containing the column indices of the indicator variables.
  * `complement::AbstractVector{Integer}`: Integer array of length `nrows` with the complement flags: 0not an indicator constraint (in this case the corresponding entry in the `colind` array is ignored); 1for indicator constraints with condition "`bin = 1`"; -1for indicator constraints with condition "`bin = 0`".

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSsetindicators](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSsetindicators.html) in the C API.
