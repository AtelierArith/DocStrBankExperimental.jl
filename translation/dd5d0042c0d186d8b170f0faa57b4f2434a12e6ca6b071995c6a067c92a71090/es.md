```
Vector{T}(missing, m)
```

Construye un [`Vector{T}`](@ref) de longitud `m`, inicializado con entradas de [`missing`](@ref). El tipo de elemento `T` debe ser capaz de contener estos valores, es decir, `Missing <: T`.

# Ejemplos

```jldoctest
julia> Vector{Union{Missing, String}}(missing, 2)
2-element Vector{Union{Missing, String}}:
 missing
 missing
```
