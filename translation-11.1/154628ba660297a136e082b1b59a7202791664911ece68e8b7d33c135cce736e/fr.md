```
getrs!(trans, A, ipiv, B)
```

Résout l'équation linéaire `A * X = B`, `transpose(A) * X = B`, ou `adjoint(A) * X = B` pour une matrice carrée `A`. Modifie la matrice/vecteur `B` sur place avec la solution. `A` est la factorisation `LU` provenant de `getrf!`, avec `ipiv` les informations de pivotement. `trans` peut être l'un de `N` (aucune modification), `T` (transposée), ou `C` (transposée conjuguée).
