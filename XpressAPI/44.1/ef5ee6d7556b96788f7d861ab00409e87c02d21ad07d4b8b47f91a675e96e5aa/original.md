```
XPRSalter(prob, filename)::prob
```

Alters or changes matrix elements, right hand sides and constraint senses in the current problem.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `filename::Union{Nothing,AbstractString}`: A string of up to MAXPROBNAMELENGTH characters specifying the file to be read.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSalter](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSalter.html) in the C API.
