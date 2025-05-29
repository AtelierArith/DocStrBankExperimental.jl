```
XPRSslpgetrowinfodouble(prob, type, row)::info
```

Get current row information.

# Arguments

  * `prob::XPRSprob`: The current SLP problem
  * `type::Integer`: Type of information (see below)
  * `row::Integer`: Index of the row whose information is to be handled

# Return value

  * `info::Float64`: Address of information to be set or retrieved

See also the documentation of the correponding function [XPRSslpgetrowinfo](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpgetrowinfo.html) in the C API.
