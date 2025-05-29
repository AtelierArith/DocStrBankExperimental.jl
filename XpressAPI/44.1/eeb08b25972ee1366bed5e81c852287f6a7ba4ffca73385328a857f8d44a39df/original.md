```
XPRS_MAXSTALLTIME
```

The maximum time in seconds that the Optimizer will continue to search for improving solution after finding a new incumbent. (double)

Default value: `0`

Values: 0 : No stall time limit.

> 0


: If an integer solution has been found, stop MIP search after the given number of seconds without a new incumbent. No effect as long as no solution was found.
