```
XPRStunerwritemethod(prob, methodfile)::prob
```

This function writes the current tuner method to a given file or prints it to the console.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `methodfile::Union{Nothing,AbstractString}`: The method file name, to which the tuner will write the current tuner method.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRStunerwritemethod](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRStunerwritemethod.html) in the C API.
