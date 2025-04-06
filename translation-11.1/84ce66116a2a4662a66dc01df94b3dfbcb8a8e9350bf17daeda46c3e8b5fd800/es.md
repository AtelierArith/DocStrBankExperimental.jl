```
nnz(A)
```

Devuelve el número de elementos almacenados (rellenos) en un arreglo disperso.

# Ejemplos

```jldoctest
julia> A = sparse(2I, 3, 3)
3×3 SparseMatrixCSC{Int64, Int64} con 3 entradas almacenadas:
 2  ⋅  ⋅
 ⋅  2  ⋅
 ⋅  ⋅  2

julia> nnz(A)
3
```
