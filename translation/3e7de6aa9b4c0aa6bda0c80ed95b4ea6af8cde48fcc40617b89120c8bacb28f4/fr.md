```
spdiagm(kv::Pair{<:Integer,<:AbstractVector}...)
spdiagm(m::Integer, n::Integer, kv::Pair{<:Integer,<:AbstractVector}...)

Construit une matrice diagonale creuse à partir de `Pair`s de vecteurs et de diagonales. Chaque vecteur `kv.second` sera placé sur la diagonale `kv.first`. Par défaut, la matrice est carrée et sa taille est déduite de `kv`, mais une taille non carrée `m`×`n` (remplie de zéros si nécessaire) peut être spécifiée en passant `m,n` comme premiers arguments.

# Exemples

```

jldoctest julia> spdiagm(-1 => [1,2,3,4], 1 => [4,3,2,1]) 5×5 SparseMatrixCSC{Int64, Int64} avec 8 entrées stockées :  ⋅  4  ⋅  ⋅  ⋅  1  ⋅  3  ⋅  ⋅  ⋅  2  ⋅  2  ⋅  ⋅  ⋅  3  ⋅  1  ⋅  ⋅  ⋅  4  ⋅ ```
