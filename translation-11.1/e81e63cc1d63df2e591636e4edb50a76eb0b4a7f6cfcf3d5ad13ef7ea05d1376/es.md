```
dropzeros(x::AbstractCompressedVector)
```

Genera una copia de `x` y elimina ceros numéricos de esa copia.

Para una versión en su lugar e información algorítmica, consulta [`dropzeros!`](@ref).

# Ejemplos

```jldoctest
julia> A = sparsevec([1, 2, 3], [1.0, 0.0, 1.0])
3-element SparseVector{Float64, Int64} with 3 stored entries:
  [1]  =  1.0
  [2]  =  0.0
  [3]  =  1.0

julia> dropzeros(A)
3-element SparseVector{Float64, Int64} with 2 stored entries:
  [1]  =  1.0
  [3]  =  1.0
```
