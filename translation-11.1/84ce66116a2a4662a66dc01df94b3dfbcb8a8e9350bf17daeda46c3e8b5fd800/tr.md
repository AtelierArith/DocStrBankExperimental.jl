```
nnz(A)
```

Seyrek bir dizide saklanan (doldurulmuş) elemanların sayısını döndürür.

# Örnekler

```jldoctest
julia> A = sparse(2I, 3, 3)
3×3 SparseMatrixCSC{Int64, Int64} with 3 stored entries:
 2  ⋅  ⋅
 ⋅  2  ⋅
 ⋅  ⋅  2

julia> nnz(A)
3
```
