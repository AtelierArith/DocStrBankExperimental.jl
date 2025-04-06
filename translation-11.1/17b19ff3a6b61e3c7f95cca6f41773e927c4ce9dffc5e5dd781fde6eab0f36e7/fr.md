```
gesv!(A, B) -> (B, A, ipiv)
```

Résout l'équation linéaire `A * X = B` où `A` est une matrice carrée utilisant la factorisation `LU` de `A`. `A` est écrasé avec sa factorisation `LU` et `B` est écrasé avec la solution `X`. `ipiv` contient les informations de pivotage pour la factorisation `LU` de `A`.
