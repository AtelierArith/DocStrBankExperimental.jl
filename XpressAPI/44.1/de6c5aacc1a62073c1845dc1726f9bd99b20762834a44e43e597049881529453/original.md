```
XPRS_IISSOLSTATUS
```

IIS solution status. (integer)

Values: 0 : Unstarted (`XPRS_IIS_UNSTARTED`), typically due to a license or input error. 1 : Feasible (`XPRS_IIS_FEASIBLE`), so no IIS can be produced. 2 : Completed (`XPRS_IIS_COMPLETED`); this is the normal termination. The number of IIS sets can be queried through the NUMIIS attribute. 3 : Unfinished (`XPRS_IIS_UNFINISHED`), either because of hitting the time limit or because of a user interrupt. When the IIS procedure terminates with this status the last IIS set may not be irreducible.
