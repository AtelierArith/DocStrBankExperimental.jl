```
cholesky!(A::AbstractMatrix, NoPivot(); check = true) -> Cholesky
```

Le même que [`cholesky`](@ref), mais économise de l'espace en écrasant l'entrée `A`, au lieu de créer une copie. Une exception [`InexactError`](@ref) est levée si la factorisation produit un nombre non représentable par le type d'élément de `A`, par exemple pour les types entiers.

# Exemples

```jldoctest
julia> A = [1 2; 2 50]
2×2 Matrix{Int64}:
 1   2
 2  50

julia> cholesky!(A)
ERROR: InexactError: Int64(6.782329983125268)
Stacktrace:
[...]
```
