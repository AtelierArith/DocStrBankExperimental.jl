```
XPRS_FORCEPARALLELDUAL
```

Dual simplex: specifies whether the dual simplex solver should always use the parallel simplex algorithm. (integer)

By default, when using a single thread, the dual simplex solver will execute a dedicated sequential simplex algorithm.

Default value: `0`

Values: 0 : Disabled. 1 : Enabled. Force the dual simplex solver to use the parallel algorithm.
