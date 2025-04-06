```
spdiagm(v::AbstractVector)
spdiagm(m::Integer, n::Integer, v::AbstractVector)
```

Construit une matrice creuse avec les éléments du vecteur comme éléments diagonaux. Par défaut (sans `m` et `n` donnés), la matrice est carrée et sa taille est donnée par `length(v)`, mais une taille non carrée `m`×`n` peut être spécifiée en passant `m` et `n` comme premiers arguments.

!!! compat "Julia 1.6"
    Ces fonctions nécessitent au moins Julia 1.6.


# Exemples

```jldoctest
julia> spdiagm([1,2,3])
3×3 SparseMatrixCSC{Int64, Int64} avec 3 entrées stockées :
 1  ⋅  ⋅
 ⋅  2  ⋅
 ⋅  ⋅  3

julia> spdiagm(sparse([1,0,3]))
3×3 SparseMatrixCSC{Int64, Int64} avec 2 entrées stockées :
 1  ⋅  ⋅
 ⋅  ⋅  ⋅
 ⋅  ⋅  3
```
