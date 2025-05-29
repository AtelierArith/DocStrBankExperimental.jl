```
XPRSgetmipsolval(prob, col, row)::x, slack
```

**Deprecated**Use XPRSgetsolution and XPRSgetslacks instead.

Used to obtain a single solution value of the last MIP solution that was found.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `col::Integer`: Column index of the variable for which to return the solution value.
  * `row::Integer`: Row index of the constraint for which to return the solution value.

# Return values

  * `x::Float64`: Double pointer where the value of the primal variable will be returned.
  * `slack::Float64`: Double pointer where the value of the slack variable will be returned.

See also the documentation of the correponding function [XPRSgetmipsolval](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetmipsolval.html) in the C API.
