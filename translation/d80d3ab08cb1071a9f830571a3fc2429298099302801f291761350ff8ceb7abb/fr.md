```
dropzeros(A::AbstractSparseMatrixCSC;)
```

Génère une copie de `A` et supprime les zéros numériques stockés de cette copie.

Pour une version en place et des informations algorithmiques, voir [`dropzeros!`](@ref).

# Exemples

```jldoctest
julia> A = sparse([1, 2, 3], [1, 2, 3], [1.0, 0.0, 1.0])
3×3 SparseMatrixCSC{Float64, Int64} avec 3 entrées stockées :
 1.0   ⋅    ⋅
  ⋅   0.0   ⋅
  ⋅    ⋅   1.0

julia> dropzeros(A)
3×3 SparseMatrixCSC{Float64, Int64} avec 2 entrées stockées :
 1.0   ⋅    ⋅
  ⋅    ⋅    ⋅
  ⋅    ⋅   1.0
```
