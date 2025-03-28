```
Vector{T}(nada, m)
```

Construye un [`Vector{T}`](@ref) de longitud `m`, inicializado con entradas de [`nada`](@ref). El tipo de elemento `T` debe ser capaz de contener estos valores, es decir, `Nothing <: T`.

# Ejemplos

```jldoctest
julia> Vector{Union{Nothing, String}}(nada, 2)
2-element Vector{Union{Nothing, String}}:
 nada
 nada
```
