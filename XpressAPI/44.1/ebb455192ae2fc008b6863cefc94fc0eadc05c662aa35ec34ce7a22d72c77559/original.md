```
XPRSgetdblattrib(prob, attrib)::value
```

Enables users to retrieve the values of various double problem attributes.

Problem attributes are set during loading and optimization of a problem.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `attrib::Integer`: Problem attribute whose value is to be returned.

# Return value

  * `value::Float64`: Pointer to a double where the value of the problem attribute will be returned.

See also the documentation of the correponding function [XPRSgetdblattrib](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetdblattrib.html) in the C API.
