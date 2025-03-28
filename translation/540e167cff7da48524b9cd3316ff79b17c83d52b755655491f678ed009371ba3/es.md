```
sparse(A)
```

Convierte una `AbstractMatrix` `A` en una matriz dispersa.

# Ejemplos

```jldoctest
julia> A = Matrix(1.0I, 3, 3)
3×3 Matrix{Float64}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0

julia> sparse(A)
3×3 SparseMatrixCSC{Float64, Int64} con 3 entradas almacenadas:
 1.0   ⋅    ⋅
  ⋅   1.0   ⋅
  ⋅    ⋅   1.0
```
