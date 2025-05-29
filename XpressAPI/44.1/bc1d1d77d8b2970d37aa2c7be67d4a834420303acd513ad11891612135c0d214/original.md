```
XPRS_MAXCUTTIME
```

The maximum amount of time allowed for generation of cutting planes and reoptimization. (double)

The limit is checked during generation and no further cuts are added once this limit has been exceeded.

Default value: `0`

Values: 0 : No time limit.

> 0


: Stop cut generation after the given number of seconds.
