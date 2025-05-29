```
XPRS_PRESOLVE
```

This control determines whether presolving should be performed prior to starting the main algorithm. (integer)

Presolve attempts to simplify the problem by detecting and removing redundant constraints, tightening variable bounds, etc. In some cases, infeasibility may even be determined at this stage, or the optimal solution found.

Default value: `1`

Values: -1 : Presolve applied, but a problem will not be declared infeasible if primal infeasibilities are detected. The problem will be solved by the LP optimization algorithm, returning an infeasible solution, which can sometimes be helpful. 0 : Presolve not applied. 1 : Presolve applied. 2 : Presolve applied, but redundant bounds are not removed. This can sometimes increase the efficiency of the barrier algorithm. 3 : Presolve is applied, and bounds detected to be redundant are always removed.
