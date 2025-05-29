```
XPRS_HEURDEPTH
```

Branch and Bound: Sets the maximum depth in the tree search at which heuristics will be used to find MIP solutions. (integer)

It may be worth stopping the heuristic search for solutions after a certain depth in the tree search. A value of 0 signifies that heuristics will not be used. This control no longer has any effect and will be removed from future releases.

Default value: `-1`

Domain: 0~+INF
