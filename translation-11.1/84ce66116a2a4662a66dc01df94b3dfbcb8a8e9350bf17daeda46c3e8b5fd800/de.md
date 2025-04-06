```
nnz(A)
```

Gibt die Anzahl der gespeicherten (gefüllten) Elemente in einem spärlichen Array zurück.

# Beispiele

```jldoctest
julia> A = sparse(2I, 3, 3)
3×3 SparseMatrixCSC{Int64, Int64} mit 3 gespeicherten Einträgen:
 2  ⋅  ⋅
 ⋅  2  ⋅
 ⋅  ⋅  2

julia> nnz(A)
3
```
