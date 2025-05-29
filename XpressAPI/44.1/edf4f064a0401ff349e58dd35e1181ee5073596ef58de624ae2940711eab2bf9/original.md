```
XPRS_HEURDIVESOFTROUNDING
```

Branch and Bound: Enables a more cautious strategy for the diving heuristic, where it tries to push binaries and integer variables to their bounds using the objective, instead of directly fixing them. (integer)

This can be useful when the default diving heuristics fail to find any feasible solutions.

Default value: `-1`

Values: -1 : Automatic selection. 0 : Do not use soft rounding. 1 : Cautious use of the soft rounding strategy. 2 : More aggressive use of the soft rounding strategy.
