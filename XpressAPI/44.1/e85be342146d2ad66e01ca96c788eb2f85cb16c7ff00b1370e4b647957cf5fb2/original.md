```
XPRS_TREEMEMORYLIMIT
```

A soft limit, in megabytes, for the amount of memory to use in storing the branch and bound search tree. (integer)

This doesn't include memory used for presolve, heuristics, solving the LP relaxation, etc. When set to 0 (the default), the optimizer will calculate a limit automatically based on the amount of free physical memory detected in the machine. When the memory used by the branch and bound tree exceeds this limit, the optimizer will try to reduce the memory usage by writing lower-rated sections of the tree to a file called the "tree file". Though the solve can continue if it cannot bring the tree memory usage below the specified limit, performance will be inhibited and a message will be printed to the log.

Default value: 0 (calculate limit automatically)

Domain: 0~+INF
