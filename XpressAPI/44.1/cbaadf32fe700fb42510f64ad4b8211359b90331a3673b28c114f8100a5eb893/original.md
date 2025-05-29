```
XPRS_OPTIMALITYTOL
```

Simplex: This is the zero tolerance for reduced costs. (double)

On each iteration, the simplex method searches for a variable to enter the basis which has a negative reduced cost. The candidates are only those variables which have reduced costs less than the negative value of `OPTIMALITYTOL`.

Default value: `1.0E-06`

Domain: (0,+INF]
