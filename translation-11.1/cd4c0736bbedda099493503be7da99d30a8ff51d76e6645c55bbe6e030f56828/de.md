```
pstrf!(uplo, A, tol) -> (A, piv, rank, info)
```

Berechnet die (obere, wenn `uplo = U`, untere, wenn `uplo = L`) pivotierte Cholesky-Zerlegung der positiv definiten Matrix `A` mit einer benutzerdefinierten Toleranz `tol`. `A` wird durch seine Cholesky-Zerlegung überschrieben.

Gibt `A`, die Pivots `piv`, den Rang von `A` und einen `info`-Code zurück. Wenn `info = 0`, war die Faktorisierung erfolgreich. Wenn `info = i > 0`, ist `A` indefinit oder rangdefizient.
