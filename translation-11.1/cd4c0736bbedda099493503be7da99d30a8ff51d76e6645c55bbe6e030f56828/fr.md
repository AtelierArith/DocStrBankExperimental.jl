```
pstrf!(uplo, A, tol) -> (A, piv, rank, info)
```

Calcule la décomposition de Cholesky pivotée (supérieure si `uplo = U`, inférieure si `uplo = L`) de la matrice définie positive `A` avec une tolérance définie par l'utilisateur `tol`. `A` est écrasée par sa décomposition de Cholesky.

Renvoie `A`, les pivots `piv`, le rang de `A`, et un code `info`. Si `info = 0`, la factorisation a réussi. Si `info = i > 0`, alors `A` est indéfinie ou déficiente en rang.
