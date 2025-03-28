```
gebak!(job, side, ilo, ihi, scale, V)
```

Transforma los eigenvectores `V` de una matriz equilibrada usando `gebal!` a los eigenvectores no escalados/no permutados de la matriz original. Modifica `V` en su lugar. `side` puede ser `L` (se transforman los eigenvectores izquierdos) o `R` (se transforman los eigenvectores derechos).
