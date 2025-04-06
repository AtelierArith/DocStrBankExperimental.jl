```
transpose!(X::AbstractSparseMatrixCSC{Tv,Ti}, A::AbstractSparseMatrixCSC{Tv,Ti}) where {Tv,Ti}
```

Transposer la matrice `A` et la stocke dans la matrice `X`. `size(X)` doit être égal à `size(transpose(A))`. Aucune mémoire supplémentaire n'est allouée en dehors du redimensionnement de `rowval` et `nzval` de `X`, si nécessaire.

Voir `halfperm!`
