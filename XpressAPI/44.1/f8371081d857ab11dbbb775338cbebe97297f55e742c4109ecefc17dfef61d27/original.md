```
XPRS_MIPRELCUTOFF
```

Branch and Bound: Percentage of the incumbent value to be added to the value of the objective function when an integer solution is found, to give the new value of CURRMIPCUTOFF. (double)

The effect is to cut off the search in parts of the tree whose best possible objective function would not be substantially better than the current solution. The control `MIPRELSTOP` provides a similar functionality but works in a different way.

Default value: `1.0E-04`

Domain: [-INF,+INF]
