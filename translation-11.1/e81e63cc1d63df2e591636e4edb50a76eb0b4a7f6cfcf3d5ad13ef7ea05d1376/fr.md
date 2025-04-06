```
dropzeros(x::AbstractCompressedVector)
```

Génère une copie de `x` et supprime les zéros numériques de cette copie.

Pour une version en place et des informations algorithmiques, voir [`dropzeros!`](@ref).

# Exemples

```jldoctest
julia> A = sparsevec([1, 2, 3], [1.0, 0.0, 1.0])
3-élément SparseVector{Float64, Int64} avec 3 entrées stockées :
  [1]  =  1.0
  [2]  =  0.0
  [3]  =  1.0

julia> dropzeros(A)
3-élément SparseVector{Float64, Int64} avec 2 entrées stockées :
  [1]  =  1.0
  [3]  =  1.0
```
