```
XPRSbasisstability(prob, type, norm, scaled)::value
```

Calculates various measures for the stability of the current basis, including the basis condition number.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `type::Integer`: 0Condition number of the basis.
  * `norm::Integer`: 0Use the infinity norm.
  * `scaled::Integer`: If the stability values are to be calculated in the scaled, or the unscaled matrix.

# Return value

  * `value::Float64`: Pointer to a double, where the calculated value is to be returned.

See also the documentation of the correponding function [XPRSbasisstability](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSbasisstability.html) in the C API.
