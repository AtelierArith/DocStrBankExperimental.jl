```
similar(A::AbstractSparseMatrixCSC{Tv,Ti}, [::Type{TvNew}, ::Type{TiNew}, m::Integer, n::Integer]) where {Tv,Ti}
```

Créez un tableau mutable non initialisé avec le type d'élément, le type d'index et la taille donnés, basé sur la source `SparseMatrixCSC` donnée. La nouvelle matrice creuse maintient la structure de la matrice creuse originale, sauf dans le cas où les dimensions de la matrice de sortie sont différentes de la sortie.

La matrice de sortie a des zéros aux mêmes emplacements que l'entrée, mais des valeurs non initialisées pour les emplacements non nuls.
