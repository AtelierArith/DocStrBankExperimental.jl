```
nnz(A)
```

Renvoie le nombre d'éléments stockés (remplis) dans un tableau sparse.

# Exemples

```jldoctest
julia> A = sparse(2I, 3, 3)
3×3 SparseMatrixCSC{Int64, Int64} avec 3 entrées stockées :
 2  ⋅  ⋅
 ⋅  2  ⋅
 ⋅  ⋅  2

julia> nnz(A)
3
```
