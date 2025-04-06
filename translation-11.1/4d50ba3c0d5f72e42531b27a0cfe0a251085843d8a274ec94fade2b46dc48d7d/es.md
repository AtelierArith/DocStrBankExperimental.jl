```
selectdim(A, d::Integer, i)
```

Devuelve una vista de todos los datos de `A` donde el índice para la dimensión `d` es igual a `i`.

Equivalente a `view(A,:,:,...,i,:,:,...)` donde `i` está en la posición `d`.

Véase también: [`eachslice`](@ref).

# Ejemplos

```jldoctest
julia> A = [1 2 3 4; 5 6 7 8]
2×4 Matrix{Int64}:
 1  2  3  4
 5  6  7  8

julia> selectdim(A, 2, 3)
2-element view(::Matrix{Int64}, :, 3) with eltype Int64:
 3
 7

julia> selectdim(A, 2, 3:4)
2×2 view(::Matrix{Int64}, :, 3:4) with eltype Int64:
 3  4
 7  8
```
