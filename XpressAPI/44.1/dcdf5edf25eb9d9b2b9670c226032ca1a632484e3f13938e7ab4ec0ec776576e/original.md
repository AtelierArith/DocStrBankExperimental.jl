```
XPRS_HEUREMPHASIS
```

Branch and Bound: This control specifies an emphasis for the search w.r.t. (integer)

primal heuristics and other procedures that affect the speed of convergence of the primal-dual gap. For problems where the goal is to achieve a small gap but not neccessarily solving them to optimality, it is recommended to set `HEUREMPHASIS` to 1. This setting triggers many additional heuristic calls, aiming for reducing the gap at the beginning of the search, typically at the expense of an increased time for proving optimality.

Default value: `-1`

Values: -1 : Optimizer default strategy. 0 : Disables all heuristics. 1 : Focus on reducing the primal-dual gap in the early part of the search. 2 : Extremely aggressive search heuristics.
