```
*(A, B::AbstractMatrix, C)
A * B * C * D
```

La multiplication en chaîne de 3 ou 4 matrices est effectuée dans la séquence la plus efficace, en fonction des tailles des tableaux. C'est-à-dire que le nombre de multiplications scalaires nécessaires pour `(A * B) * C` (avec 3 matrices denses) est comparé à celui pour `A * (B * C)` afin de choisir laquelle de ces opérations exécuter.

Si le dernier facteur est un vecteur, ou le premier un vecteur transposé, il est efficace de traiter ces cas en premier. En particulier, `x' * B * y` signifie `(x' * B) * y` pour une matrice ordinaire en colonne `B::Matrix`. Contrairement à `dot(x, B, y)`, cela alloue un tableau intermédiaire.

Si le premier ou le dernier facteur est un nombre, cela sera fusionné avec la multiplication matricielle, en utilisant [`mul!`](@ref) à 5 arguments.

Voir aussi [`muladd`](@ref), [`dot`](@ref).

!!! compat "Julia 1.7"
    Ces optimisations nécessitent au moins Julia 1.7.

