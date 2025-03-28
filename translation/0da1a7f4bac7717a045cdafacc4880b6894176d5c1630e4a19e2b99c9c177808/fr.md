```
cholesky!(A::AbstractMatrix, RowMaximum(); tol = 0.0, check = true) -> CholeskyPivoted
```

Le même que [`cholesky`](@ref), mais économise de l'espace en écrasant l'entrée `A`, au lieu de créer une copie. Une exception [`InexactError`](@ref) est levée si la factorisation produit un nombre non représentable par le type d'élément de `A`, par exemple pour les types entiers.
