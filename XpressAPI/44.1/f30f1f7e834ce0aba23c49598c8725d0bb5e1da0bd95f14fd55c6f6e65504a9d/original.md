```
XPRS_BARREFITER
```

Newton barrier: After terminating the barrier algorithm, further refinement steps can be performed. (integer)

Such refinement steps are especially helpful if the solution is near to the optimum and can improve primal feasibility and decrease the complementarity gap. It is also often advantageous for the crossover algorithm. `BARREFITER` specifies the maximum number of such refinement iterations.

Default value: `0`

Domain: 0~+INF
