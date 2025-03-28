```
sparse_hcat(A...)
```

Concaténer le long de la dimension 2. Retourne un objet SparseMatrixCSC.

!!! compat "Julia 1.8"
    Cette méthode a été ajoutée dans Julia 1.8. Elle imite le comportement de concaténation précédent, où la concaténation avec des types de matrices "sparse" spécialisés de LinearAlgebra.jl produisait automatiquement une sortie sparse même en l'absence de tout argument SparseArray.

