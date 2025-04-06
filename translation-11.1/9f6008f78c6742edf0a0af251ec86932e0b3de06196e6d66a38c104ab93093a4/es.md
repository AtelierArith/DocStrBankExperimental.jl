```
deleteat!(a::Vector, i::Integer)
```

Elimina el elemento en el índice dado `i` y devuelve el `a` modificado. Los elementos posteriores se desplazan para llenar el hueco resultante.

Véase también: [`keepat!`](@ref), [`delete!`](@ref), [`popat!`](@ref), [`splice!`](@ref).

# Ejemplos

```jldoctest
julia> deleteat!([6, 5, 4, 3, 2, 1], 2)
5-element Vector{Int64}:
 6
 4
 3
 2
 1
```
