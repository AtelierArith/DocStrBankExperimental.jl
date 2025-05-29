```
XPRSslpchgcascadenlimit(prob, col, limit)::prob
```

Set a variable specific cascade iteration limit

# Arguments

  * `prob::XPRSprob`: The current SLP problem.
  * `col::Integer`: The index of the column corresponding to the SLP variable for which the cascading limit is to be imposed.
  * `limit::Integer`: The new cascading iteration limit.

# Return value

  * `prob::XPRSprob`: The current SLP problem.

See also the documentation of the correponding function [XPRSslpchgcascadenlimit](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpchgcascadenlimit.html) in the C API.
