```
zeros([T=Float64,] dims::Tuple)
zeros([T=Float64,] dims...)
```

Crea un `Array`, con tipo de elemento `T`, de todos ceros con tamaño especificado por `dims`. Véase también [`fill`](@ref), [`ones`](@ref), [`zero`](@ref).

# Ejemplos

```jldoctest
julia> zeros(1)
1-element Vector{Float64}:
 0.0

julia> zeros(Int8, 2, 3)
2×3 Matrix{Int8}:
 0  0  0
 0  0  0
```
