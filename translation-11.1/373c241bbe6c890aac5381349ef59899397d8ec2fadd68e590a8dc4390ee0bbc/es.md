```
Matrix{T}(nothing, m, n)
```

Construye una [`Matrix{T}`](@ref) de tamaño `m`×`n`, inicializada con entradas de [`nothing`](@ref). El tipo de elemento `T` debe ser capaz de contener estos valores, es decir, `Nothing <: T`.

# Ejemplos

```jldoctest
julia> Matrix{Union{Nothing, String}}(nothing, 2, 3)
2×3 Matrix{Union{Nothing, String}}:
 nothing  nothing  nothing
 nothing  nothing  nothing
```
