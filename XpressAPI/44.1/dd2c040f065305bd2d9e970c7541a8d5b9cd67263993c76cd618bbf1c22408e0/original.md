```
XPRS_BARALG
```

This control determines which barrier algorithm is used to solve the problem. (integer)

Default value: `-1`

Values: -1 : Determined automatically. 0 : Unused. 1 : Use the infeasible-start barrier algorithm. 2 : Use the homogeneous self-dual barrier algorithm. 3 : Start with 2 and optionally switch to 1 during the execution. 4 : Use the hybrid gradient algorithm.
