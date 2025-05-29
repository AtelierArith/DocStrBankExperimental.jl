```
XPRS_PREDUPROW
```

Presolve: Determines the type of duplicate rows to look for and eliminate when presolving a problem. (integer)

Default value: `-1`

Values: -1 : Automatically determined. 0 : Do not eliminate duplicate rows. 1 : Eliminate only rows that are identical in all variables. 2 : Same as option 1 plus eliminate duplicate rows with simple penalty variable expressions. (MIP only). 3 : Same as option 2 plus eliminate duplicate rows with more complex penalty variable expressions. (MIP only).
