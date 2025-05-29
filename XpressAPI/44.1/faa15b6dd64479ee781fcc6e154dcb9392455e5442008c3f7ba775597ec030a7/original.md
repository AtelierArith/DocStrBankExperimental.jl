```
XPRS_DEFAULTALG
```

This selects the algorithm that will be used to solve LPs, standalone or during MIP optimization. (integer)

Default value: `1`

Values: 1 : Automatically determined. 2 : Dual simplex. 3 : Primal simplex. 4 : Newton barrier (or hybrid gradient, if BARALG=4 is set).
