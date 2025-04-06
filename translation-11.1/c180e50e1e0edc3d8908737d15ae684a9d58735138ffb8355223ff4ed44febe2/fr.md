```
ftranspose!(X::AbstractSparseMatrixCSC{Tv,Ti}, A::AbstractSparseMatrixCSC{Tv,Ti}, f::Function) where {Tv,Ti}
```

Transposer `A` et le stocker dans `X` tout en appliquant la fonction `f` aux éléments non nuls. Ne supprime pas les zéros créés par `f`. `size(X)` doit être égal à `size(transpose(A))`. Aucune mémoire supplémentaire n'est allouée en dehors du redimensionnement de rowval et nzval de `X`, si nécessaire.

Voir `halfperm!`
