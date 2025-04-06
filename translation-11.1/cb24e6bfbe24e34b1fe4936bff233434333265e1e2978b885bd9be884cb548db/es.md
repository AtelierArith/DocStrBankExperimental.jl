```
Array{T}(nothing, dims)
Array{T,N}(nothing, dims)
```

Construye un [`Array`](@ref) de `N` dimensiones que contenga elementos del tipo `T`, inicializado con entradas de [`nothing`](@ref). El tipo de elemento `T` debe ser capaz de contener estos valores, es decir, `Nothing <: T`.

# Ejemplos

```jldoctest
julia> Array{Union{Nothing, String}}(nothing, 2)
2-element Vector{Union{Nothing, String}}:
 nothing
 nothing

julia> Array{Union{Nothing, Int}}(nothing, 2, 3)
2×3 Matrix{Union{Nothing, Int64}}:
 nothing  nothing  nothing
 nothing  nothing  nothing
```
