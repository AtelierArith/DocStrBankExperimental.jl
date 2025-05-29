```
XPRSgetcutslack(prob, cutind)::slack
```

Used to calculate the slack value of a cut with respect to the current LP relaxation solution.

The slack is calculated from the cut itself, and might be requested for any cut (even if it is not currently loaded into the problem).

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `cutind::Ptr{Cvoid}`: Pointer of the cut for which the slack is to be calculated.

# Return value

  * `slack::Float64`: Double pointer where the value of the slack is returned.

See also the documentation of the correponding function [XPRSgetcutslack](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetcutslack.html) in the C API.
