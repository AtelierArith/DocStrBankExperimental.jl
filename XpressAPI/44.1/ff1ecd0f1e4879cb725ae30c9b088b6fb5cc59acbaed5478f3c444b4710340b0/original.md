```
XPRS_bo_validate(bo)::status
```

Verifies that a given branching object is valid for branching on the current branch-and-bound node of a MIP solve.

The function will check that all branches are non-empty, and if required, verify that the branching object can be presolved.

# Arguments

  * `bo::XPRSbranchobject`: A branching object.

# Return value

  * `status::Int32`: The returned status from checking the provided branching object: 0The object is acceptable.

See also the documentation of the correponding function [XPRS*bo*validate](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRS_bo_validate.html) in the C API.
