```
XPRS_FEASTOL
```

This tolerance determines when a solution is treated as feasible. (double)

If the amount by which a constraint's activity violates its right-hand side or ranged bound is less in absolute magnitude than `FEASTOL`, then the constraint is treated as satisfied. Similarly, if the amount by which a column violates its bounds is less in absolute magnitude than `FEASTOL`, those bounds are also treated as satisfied.

Default value: `1.0E-06`

Domain: (0,+INF]
