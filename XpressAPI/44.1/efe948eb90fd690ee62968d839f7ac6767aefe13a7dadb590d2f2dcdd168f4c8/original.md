```
XPRS_MAXTIME
```

**Deprecated**The maximum time in seconds that the Optimizer will run before it terminates, including the problem setup time and solution time. (integer)

For MIP problems, this is the total time taken to solve all nodes.

Default value: `0`

Values: 0 : No time limit. n>0 : If an integer solution has been found, stop MIP search after n seconds, otherwise continue until an integer solution is finally found. n<0 : Stop in LP or MIP search after n seconds.
