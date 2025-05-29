```
XPRStuneprobsetfile(prob, setfile, ifmip, sense)::prob
```

This function begins a tuner session for a set of problems.

The tuner will solve the problems multiple times while evaluating a list of control settings and promising combinations of them. When finished, the tuner will select and set the best control setting on the problems.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `setfile::Union{Nothing,AbstractString}`: A plain text file which contains a list of problem filenames.
  * `ifmip::Integer`: -1to automatically determine whether to solve the problem set as LP or MIP; 0to force the tuner to tune the problem set as LP; 1to force the tuner to tune the problem set as MIP.
  * `sense::Integer`: 0to automatically determine the sense of each problem; 1to force the tuner to minimize each problem; -1to force the tuner to maximize each problem.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRStuneprobsetfile](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRStuneprobsetfile.html) in the C API.
