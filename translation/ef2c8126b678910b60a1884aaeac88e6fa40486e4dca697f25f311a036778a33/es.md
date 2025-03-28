```
Matrix{T}(missing, m, n)
```

Construye una [`Matrix{T}`](@ref) de tamaño `m`×`n`, inicializada con entradas de [`missing`](@ref). El tipo de elemento `T` debe ser capaz de contener estos valores, es decir, `Missing <: T`.

# Ejemplos

```jldoctest
julia> Matrix{Union{Missing, String}}(missing, 2, 3)
2×3 Matrix{Union{Missing, String}}:
 missing  missing  missing
 missing  missing  missing
```
