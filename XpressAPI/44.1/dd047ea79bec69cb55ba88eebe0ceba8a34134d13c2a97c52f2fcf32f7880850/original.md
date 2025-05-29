```
XPRSfeaturequery(feature)::status
```

Checks if the provided feature is available in the current license used by the optimizer.

# Arguments

  * `feature::Union{Nothing,AbstractString}`: The feature string to be checked in the license.

# Return value

  * `status::Int32`: Return status of the check, a value of 1 indicates the feature is available.

See also the documentation of the correponding function [XPRSfeaturequery](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSfeaturequery.html) in the C API.
