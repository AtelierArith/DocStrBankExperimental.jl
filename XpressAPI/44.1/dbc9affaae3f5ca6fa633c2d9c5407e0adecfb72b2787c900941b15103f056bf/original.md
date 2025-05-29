```
XPRS_CONFLICTCUTS
```

Branch and Bound: Specifies how cautious or aggressive the optimizer should be when searching for and applying conflict cuts. (integer)

Conflict cuts are in-tree cuts derived from nodes found to be infeasible or cut off, which can be used to cut off other branches of the search tree.

Default value: `-1`

Values: -1 : Automatic. 0 : Disable conflict cuts. 1 : Cautious application of conflict cuts. 2 : Medium application of conflict cuts. 3 : Aggressive application of conflict cuts.
