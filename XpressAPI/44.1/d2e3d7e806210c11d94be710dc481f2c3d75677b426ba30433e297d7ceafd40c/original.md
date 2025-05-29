```
XPRSsetstrcontrol(prob, control, value)::prob
```

Used to set the value of a given string control parameter.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `control::Integer`: Control parameter whose value is to be set.
  * `value::Union{Nothing,AbstractString}`: A string containing the value to which the control is to be set (plus a null terminator).

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSsetstrcontrol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSsetstrcontrol.html) in the C API.
