```
XPRSdelpwlcons(prob, npwls, pwlind)::prob
```

Delete piecewise linear constraints from a problem.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `npwls::Integer`: Number of piecewise linear constraints to delete.
  * `pwlind::AbstractVector{Integer}`: An integer array of length `npwls` containing the piecewise linear constraints to delete.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSdelpwlcons](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSdelpwlcons.html) in the C API.
