```
XPRS_BIGMMETHOD
```

Simplex: This specifies whether to use the "Big M" method, or the standard phase I (achieving feasibility) and phase II (achieving optimality). (integer)

In the "Big M" method, the objective coefficients of the variables are considered during the feasibility phase, possibly leading to an initial feasible basis which is closer to optimal. The side-effects involve possible round-off errors due to the presence of the "Big M" factor in the problem.

Default value: `1`

Values: 0 : For phase I / phase II. 1 : If "Big M" method to be used.
