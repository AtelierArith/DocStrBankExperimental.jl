```
XPRSgetstrcontrol(prob, control)::value
```

Returns the value of a given string control parameters.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `control::Integer`: Control parameter whose value is to be returned.

# Return value

  * `value::AbstractString`: Pointer to a string where the value of the control (plus null terminator) will be returned.

See also the documentation of the correponding function [XPRSgetstrcontrol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetstrcontrol.html) in the C API.
