```
XPRS_PWLNONCONVEXTRANSFORMATION
```

This control specifies the reformulation method for piecewise linear constraints at the beginning of the search. (integer)

Note that the chosen formulation will only be used if MIP entities are necessary but not if presolve detected that a convex reformulation is possible. Furthermore, the binary formulation will only be applied to piecewise linear constraints with bounded input variable, otherwise the SOS2-formulation will be used.

Default value: `-1`

Values: -1 : Automatic. 0 : Use a formulation based on SOS2-constraints. 1 : Use a formulation based on binary variables.
