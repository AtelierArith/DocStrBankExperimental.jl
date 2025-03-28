```
rdiv!(A, B)
```

Calcule `A / B` sur place et écrase `A` pour stocker le résultat.

L'argument `B` ne doit *pas* être une matrice. Au lieu de matrices, il doit s'agir d'un objet de factorisation (par exemple, produit par [`factorize`](@ref) ou [`cholesky`](@ref)). La raison en est que la factorisation elle-même est à la fois coûteuse et nécessite généralement de l'allocation de mémoire (bien qu'elle puisse également être effectuée sur place via, par exemple, [`lu!`](@ref)), et les situations critiques en termes de performance nécessitant `rdiv!` exigent généralement un contrôle fin sur la factorisation de `B`.

!!! note
    Certains types de matrices structurées, tels que `Diagonal` et `UpperTriangular`, sont autorisés, car ils sont déjà sous une forme factorisée.

