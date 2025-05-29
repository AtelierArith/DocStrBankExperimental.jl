```
XPRSslpgetrowstatus(prob, row)::status
```

Retrieve the status setting of a constraint

# Arguments

  * `prob::XPRSprob`: The current SLP problem.
  * `row::Integer`: The index of the matrix row whose data is to be obtained.

# Return value

  * `status::Int32`: Address of an integer holding a bitmap to receive the status settings.

See also the documentation of the correponding function [XPRSslpgetrowstatus](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpgetrowstatus.html) in the C API.
