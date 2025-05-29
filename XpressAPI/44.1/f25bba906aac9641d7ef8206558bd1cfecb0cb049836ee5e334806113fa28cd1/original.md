```
XPRS_SOLSTATUS
```

Status of the solution of the last problem solved with XPRSoptimize. (integer)

Values: 0 : `XPRS_SOLSTATUS_NOTFOUND` No solution available. 1 : `XPRS_SOLSTATUS_OPTIMAL` An optimal solution has been found. 2 : `XPRS_SOLSTATUS_FEASIBLE` A solution that is not proven optimal is found. 3 : `XPRS_SOLSTATUS_INFEASIBLE` No solution exists. 4 : `XPRS_SOLSTATUS_UNBOUNDED` The problem is unbounded, if feasible.
