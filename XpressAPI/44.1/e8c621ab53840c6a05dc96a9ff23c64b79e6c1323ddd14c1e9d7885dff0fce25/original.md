```
XPRS_INDPRELINBIGM
```

During presolve, indicator constraints will be linearized using a BigM coefficient whenever that BigM coefficient is small enough. (double)

This control defines the largest BigM for which the original constraint will be replaced by the linearized version. If the BigM is larger than INDPRELINBIGM but smaller than INDLINBIGM, the linearized row will be added but the original indicator constraint is kept as a numerically stable way to check feasibility.

Default value: `100.0`

Domain: [0,+INF]
