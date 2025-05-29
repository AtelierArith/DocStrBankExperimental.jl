```
XPRSslpgetrowwt(prob, row)::weight
```

Get the initial penalty error weight for a row

# Arguments

  * `prob::XPRSprob`: The current SLP problem.
  * `row::Integer`: The index of the row whose weight is to be retrieved.

# Return value

  * `weight::Float64`: Address of a double precision variable to receive the value of the weight.

See also the documentation of the correponding function [XPRSslpgetrowwt](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpgetrowwt.html) in the C API.
