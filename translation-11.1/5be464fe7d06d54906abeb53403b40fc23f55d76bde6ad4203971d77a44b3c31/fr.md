```
sparse_hvcat(rows::Tuple{Vararg{Int}}, values...)
```

Concaténation horizontale et verticale sparse en un seul appel. Cette fonction est appelée pour la syntaxe de matrice bloc. Le premier argument spécifie le nombre d'arguments à concaténer dans chaque ligne de bloc.

!!! compat "Julia 1.8"
    Cette méthode a été ajoutée dans Julia 1.8. Elle imite le comportement de concaténation précédent, où la concaténation avec des types de matrice "sparse" spécialisés de LinearAlgebra.jl produisait automatiquement une sortie sparse même en l'absence de tout argument SparseArray.

