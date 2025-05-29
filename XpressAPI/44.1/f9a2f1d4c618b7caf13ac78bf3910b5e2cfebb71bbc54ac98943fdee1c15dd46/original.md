```
XPRS_BARPRESOLVEOPS
```

Newton barrier: This controls the Newton-Barrier specific presolve operations. (integer)

Default value: `0`

Values are a bitset: bit 0 : Use standard presolve. bit 1 : Extra effort is spent in barrier specific presolve. bit 2 : Do full matrix eliminations (reduce matrix size).
