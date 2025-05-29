```
XPRS_REFINEOPS
```

This specifies when the solution refiner should be executed to reduce solution infeasibilities. (integer)

The refiner will attempt to satisfy the target tolerances for all original linear constraints before presolve or scaling has been applied.

Default value: `19` (bits `0`, `1` and `4` are set)

Values are a bitset: bit 0 : Run the solution refiner on an optimal solution of a continuous problem. bit 1 : Run the solution refiner when a new solution is found during a tree search. The refiner will be applied to the presolved solution before any post-solve operations are applied. bit 3 : Run the solution refiner on each node of the MIP search. bit 4 : Run the solution refiner on an optimal solution before postsolve on a continuous problem. bit 5 : Apply the iterative refiner to refine the solution. bit 6 : Use higher precision in the iterative refinement. bit 7 : If set, the iterative refiner will use the primal simplex algorithm. bit 8 : If set, the iterative refiner will use the dual simplex algorithm. bit 9 : Refine MIP solutions such that rounding them keeps the problem feasible when reoptimized. bit 10 : Attempt to refine MIP solutions such that rounding them keeps the problem feasible when reoptimized, but accept integers solutions even if refinement fails.
