```
Array{T}(missing, dims)
Array{T,N}(missing, dims)
```

Construye un [`Array`](@ref) de `N` dimensiones que contenga elementos del tipo `T`, inicializado con entradas de [`missing`](@ref). El tipo de elemento `T` debe ser capaz de contener estos valores, es decir, `Missing <: T`.

# Ejemplos

```jldoctest
julia> Array{Union{Missing, String}}(missing, 2)
2-element Vector{Union{Missing, String}}:
 missing
 missing

julia> Array{Union{Missing, Int}}(missing, 2, 3)
2×3 Matrix{Union{Missing, Int64}}:
 missing  missing  missing
 missing  missing  missing
```
