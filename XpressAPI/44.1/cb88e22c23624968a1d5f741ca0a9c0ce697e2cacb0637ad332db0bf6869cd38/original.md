```
XPRSslpsetdetrow(prob, nvars, colind, rowind)::prob
```

Set the determining row of a variable

# Arguments

  * `prob::XPRSprob`: The current SLP problem.
  * `nvars::Integer`: The number of variables for which determining rows are set.
  * `colind::AbstractVector{Integer}`: Array of length `nvars` with the index of the column for which the determining row is set.
  * `rowind::AbstractVector{Integer}`: Array of length `nvars` with the index of the determining row.

# Return value

  * `prob::XPRSprob`: The current SLP problem.

See also the documentation of the correponding function [XPRSslpsetdetrow](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpsetdetrow.html) in the C API.
