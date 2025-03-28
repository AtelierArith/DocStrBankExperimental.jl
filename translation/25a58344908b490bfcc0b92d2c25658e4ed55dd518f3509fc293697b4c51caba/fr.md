```
permute(A::AbstractSparseMatrixCSC{Tv,Ti}, p::AbstractVector{<:Integer},
        q::AbstractVector{<:Integer}) where {Tv,Ti}
```

Permute bilatéralement `A`, retournant `PAQ` (`A[p,q]`). La longueur de la permutation de colonne `q` doit correspondre au nombre de colonnes de `A` (`length(q) == size(A, 2)`). La longueur de la permutation de ligne `p` doit correspondre au nombre de lignes de `A` (`length(p) == size(A, 1)`).

Pour des utilisateurs avancés et des informations supplémentaires, voir [`permute!`](@ref).

# Exemples

```jldoctest
julia> A = spdiagm(0 => [1, 2, 3, 4], 1 => [5, 6, 7])
4×4 SparseMatrixCSC{Int64, Int64} avec 7 entrées stockées :
 1  5  ⋅  ⋅
 ⋅  2  6  ⋅
 ⋅  ⋅  3  7
 ⋅  ⋅  ⋅  4

julia> permute(A, [4, 3, 2, 1], [1, 2, 3, 4])
4×4 SparseMatrixCSC{Int64, Int64} avec 7 entrées stockées :
 ⋅  ⋅  ⋅  4
 ⋅  ⋅  3  7
 ⋅  2  6  ⋅
 1  5  ⋅  ⋅

julia> permute(A, [1, 2, 3, 4], [4, 3, 2, 1])
4×4 SparseMatrixCSC{Int64, Int64} avec 7 entrées stockées :
 ⋅  ⋅  5  1
 ⋅  6  2  ⋅
 7  3  ⋅  ⋅
 4  ⋅  ⋅  ⋅
```
