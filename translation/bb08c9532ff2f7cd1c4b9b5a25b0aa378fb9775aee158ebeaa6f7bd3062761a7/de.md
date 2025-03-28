```
zeros([T=Float64,] dims::Tuple)
zeros([T=Float64,] dims...)
```

Erstellt ein `Array` mit dem Elementtyp `T`, das aus lauter Nullen besteht und dessen Größe durch `dims` angegeben wird. Siehe auch [`fill`](@ref), [`ones`](@ref), [`zero`](@ref).

# Beispiele

```jldoctest
julia> zeros(1)
1-element Vector{Float64}:
 0.0

julia> zeros(Int8, 2, 3)
2×3 Matrix{Int8}:
 0  0  0
 0  0  0
```
