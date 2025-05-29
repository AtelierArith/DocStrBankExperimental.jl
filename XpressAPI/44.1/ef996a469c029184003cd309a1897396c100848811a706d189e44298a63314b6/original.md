```
XPRS_bo_store(bo)::status
```

Adds a new user branching object to the Optimizer's list of candidates for branching.

This function is available only through the callback function set by XPRSaddcboptnode.

# Arguments

  * `bo::XPRSbranchobject`: The new user branching object to store.

# Return value

  * `status::Int32`: The returned status from checking the provided branching object: 0The object was accepted successfully.

See also the documentation of the correponding function [XPRS*bo*store](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRS_bo_store.html) in the C API.
