```
XPRSmaxim(prob, flags)::prob
```

**Deprecated**XPRSlpoptimize or XPRSmipoptimize should be used instead.

Begins a search for the optimal LP solution.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `flags::Union{Nothing,AbstractString}`: Flags to pass to `XPRSmaxim` (`MAXIM`) or `XPRSminim` (`MINIM`).

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSmaxim](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSmaxim.html) in the C API.
