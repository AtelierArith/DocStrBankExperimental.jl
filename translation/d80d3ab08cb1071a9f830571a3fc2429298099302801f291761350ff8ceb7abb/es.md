```
dropzeros(A::AbstractSparseMatrixCSC;)
```

Genera una copia de `A` y elimina los ceros numéricos almacenados de esa copia.

Para una versión en su lugar e información algorítmica, consulta [`dropzeros!`](@ref).

# Ejemplos

```jldoctest
julia> A = sparse([1, 2, 3], [1, 2, 3], [1.0, 0.0, 1.0])
3×3 SparseMatrixCSC{Float64, Int64} con 3 entradas almacenadas:
 1.0   ⋅    ⋅
  ⋅   0.0   ⋅
  ⋅    ⋅   1.0

julia> dropzeros(A)
3×3 SparseMatrixCSC{Float64, Int64} con 2 entradas almacenadas:
 1.0   ⋅    ⋅
  ⋅    ⋅    ⋅
  ⋅    ⋅   1.0
```
