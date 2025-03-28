```
dropzeros(A::AbstractSparseMatrixCSC;)
```

Generiert eine Kopie von `A` und entfernt gespeicherte numerische Nullen aus dieser Kopie.

Für eine In-Place-Version und algorithmische Informationen siehe [`dropzeros!`](@ref).

# Beispiele

```jldoctest
julia> A = sparse([1, 2, 3], [1, 2, 3], [1.0, 0.0, 1.0])
3×3 SparseMatrixCSC{Float64, Int64} mit 3 gespeicherten Einträgen:
 1.0   ⋅    ⋅
  ⋅   0.0   ⋅
  ⋅    ⋅   1.0

julia> dropzeros(A)
3×3 SparseMatrixCSC{Float64, Int64} mit 2 gespeicherten Einträgen:
 1.0   ⋅    ⋅
  ⋅    ⋅    ⋅
  ⋅    ⋅   1.0
```
