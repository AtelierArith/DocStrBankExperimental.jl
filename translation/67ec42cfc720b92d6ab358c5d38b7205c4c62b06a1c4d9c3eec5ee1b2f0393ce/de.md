```
gebak!(job, side, ilo, ihi, scale, V)
```

Transformiere die Eigenvektoren `V` einer mit `gebal!` balancierten Matrix in die unskalierten/unpermuten Eigenvektoren der ursprünglichen Matrix. Modifiziert `V` in-place. `side` kann `L` (linke Eigenvektoren werden transformiert) oder `R` (rechte Eigenvektoren werden transformiert) sein.
