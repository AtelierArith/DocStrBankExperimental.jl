```
trrfs!(uplo, trans, diag, A, B, X, Ferr, Berr) -> (Ferr, Berr)
```

Estime l'erreur dans la solution de `A * X = B` (`trans = N`), `transpose(A) * X = B` (`trans = T`), `adjoint(A) * X = B` (`trans = C`) pour `side = L`, ou les équations équivalentes d'un `side = R` `X * A` après avoir calculé `X` en utilisant `trtrs!`. Si `uplo = U`, `A` est triangulaire supérieure. Si `uplo = L`, `A` est triangulaire inférieure. Si `diag = N`, `A` a des éléments diagonaux non unitaires. Si `diag = U`, tous les éléments diagonaux de `A` sont un. `Ferr` et `Berr` sont des entrées optionnelles. `Ferr` est l'erreur avant et `Berr` est l'erreur arrière, chacune composante par composante.
