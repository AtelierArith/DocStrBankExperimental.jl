```
trtrs!(uplo, trans, diag, A, B)
```

Résout `A * X = B` (`trans = N`), `transpose(A) * X = B` (`trans = T`), ou `adjoint(A) * X = B` (`trans = C`) pour la matrice triangulaire `A` (supérieure si `uplo = U`, inférieure si `uplo = L`). Si `diag = N`, `A` a des éléments diagonaux non unitaires. Si `diag = U`, tous les éléments diagonaux de `A` sont un. `B` est écrasé avec la solution `X`.
