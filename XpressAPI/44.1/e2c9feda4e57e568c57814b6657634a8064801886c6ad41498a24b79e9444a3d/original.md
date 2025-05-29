```
XPRS_CRASH
```

Simplex: This determines the type of crash used when the algorithm begins. (integer)

During the crash procedure, an initial basis is determined which is as close to feasibility and triangularity as possible. A good choice at this stage will significantly reduce the number of iterations required to find an optimal solution. The possible values increase proportionally to their time-consumption.

Default value: `2`

Values are a bitset: bit 0 : Perform standard crash. bit 1 : Perform additional numerical checks during crash. bit 2 : Extend the set of column candidates for crash. bit 3 : Extend the set of row candidates for crash. bit 4 : Force crash, i.e., consider all suitable columns/rows as candidates for crash.
