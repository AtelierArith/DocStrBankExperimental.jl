```
XPRSiisnext(prob)::status
```

Continues the search for further Irreducible Infeasible Sets (IIS), or calls XPRSiisfirst (IIS) if no IIS has been identified yet.

# Arguments

  * `prob::XPRSprob`: The current problem.

# Return value

  * `status::Int32`: The status after the search: 0success; 1no more IIS could be found, or problem is feasible if no XPRSiisfirst call preceded; 2on error (when the function returns nonzero).

See also the documentation of the correponding function [XPRSiisnext](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSiisnext.html) in the C API.
