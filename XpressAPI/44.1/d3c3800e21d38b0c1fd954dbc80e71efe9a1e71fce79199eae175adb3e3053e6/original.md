```
XPRS_PRECONFIGURATION
```

MIP Presolve: determines whether binary rows with only few repeating coefficients should be reformulated. (integer)

The reformulation enumerates the extremal feasible configurations of a row and introduces new columns and rows to model the choice between these extremal configurations. This presolve operation can be disabled as part of the (advanced) IP reductions PRESOLVEOPS.

Default value: `-1`

Values: -1 : Automatically determined. 0 : Disable configuration presolving.
