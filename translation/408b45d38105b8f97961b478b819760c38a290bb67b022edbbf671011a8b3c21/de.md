```
blockdiag(A...)
```

Kombiniere Matrizen block-diagonal. Derzeit nur für spärliche Matrizen implementiert.

# Beispiele

```jldoctest
julia> blockdiag(sparse(2I, 3, 3), sparse(4I, 2, 2))
5×5 SparseMatrixCSC{Int64, Int64} mit 5 gespeicherten Einträgen:
 2  ⋅  ⋅  ⋅  ⋅
 ⋅  2  ⋅  ⋅  ⋅
 ⋅  ⋅  2  ⋅  ⋅
 ⋅  ⋅  ⋅  4  ⋅
 ⋅  ⋅  ⋅  ⋅  4
```
