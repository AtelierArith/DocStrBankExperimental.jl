```
XPRSsetdblcontrol(prob, control, value)::prob
```

Sets the value of a given double control parameter.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `control::Integer`: Control parameter whose value is to be set.
  * `value::Float64`: Value to which the control parameter is to be set.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSsetdblcontrol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSsetdblcontrol.html) in the C API.
