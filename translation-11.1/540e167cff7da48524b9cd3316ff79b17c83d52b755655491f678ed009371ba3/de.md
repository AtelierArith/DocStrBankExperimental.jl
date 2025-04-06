```
sparse(A)
```

Konvertiert eine AbstractMatrix `A` in eine spärliche Matrix.

# Beispiele

```jldoctest
julia> A = Matrix(1.0I, 3, 3)
3×3 Matrix{Float64}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0

julia> sparse(A)
3×3 SparseMatrixCSC{Float64, Int64} mit 3 gespeicherten Einträgen:
 1.0   ⋅    ⋅
  ⋅   1.0   ⋅
  ⋅    ⋅   1.0
```
