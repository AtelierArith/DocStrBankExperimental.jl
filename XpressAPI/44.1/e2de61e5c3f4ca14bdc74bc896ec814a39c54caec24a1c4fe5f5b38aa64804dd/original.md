```
XPRS_MIPADDCUTOFF
```

Branch and Bound: The amount to add to the objective function of the best integer solution found to give the new CURRMIPCUTOFF. (double)

Once an integer solution has been found whose objective function is equal to or better than CURRMIPCUTOFF, improvements on this value may not be interesting unless they are better by at least a certain amount. If `MIPADDCUTOFF` is nonzero, it will be added to CURRMIPCUTOFF each time an integer solution is found which is better than this new value. This cuts off sections of the tree whose solutions would not represent substantial improvements in the objective function, saving processor time. The control MIPABSSTOP provides a similar function but works in a different way.

Default value: `-1.0E-05`

Domain: [-INF,+INF]
