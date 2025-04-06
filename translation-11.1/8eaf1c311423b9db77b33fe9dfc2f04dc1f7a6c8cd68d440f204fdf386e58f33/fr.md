```
ldiv!(A::Tridiagonal, B::AbstractVecOrMat) -> B
```

Calcule `A \ B` sur place par élimination de Gauss avec pivotement partiel et stocke le résultat dans `B`, retournant le résultat. Dans le processus, les diagonales de `A` sont également écrasées.

!!! compat "Julia 1.11"
    `ldiv!` pour les côtés gauche `Tridiagonal` nécessite au moins Julia 1.11.

