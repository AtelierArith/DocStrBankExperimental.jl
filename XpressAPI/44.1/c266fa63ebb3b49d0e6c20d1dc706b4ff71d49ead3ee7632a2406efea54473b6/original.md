```
XPRSgetdblcontrol(prob, control)::value
```

Retrieves the value of a given double control parameter.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `control::Integer`: Control parameter whose value is to be returned.

# Return value

  * `value::Float64`: Pointer to the location where the control value will be returned.

See also the documentation of the correponding function [XPRSgetdblcontrol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetdblcontrol.html) in the C API.
