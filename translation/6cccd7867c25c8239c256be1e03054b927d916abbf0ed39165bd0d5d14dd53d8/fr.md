```
spzeros([type], I::AbstractVector, J::AbstractVector, [m, n])
```

Créez une matrice creuse `S` de dimensions `m x n` avec des zéros structurels à `S[I[k], J[k]]`.

Cette méthode peut être utilisée pour construire le motif de sparsité de la matrice, et est plus efficace que d'utiliser par exemple `sparse(I, J, zeros(length(I)))`.

Pour une documentation supplémentaire et un pilote expert, voir `SparseArrays.spzeros!`.

!!! compat "Julia 1.10"
    Cette méthode nécessite la version 1.10 de Julia ou ultérieure.

