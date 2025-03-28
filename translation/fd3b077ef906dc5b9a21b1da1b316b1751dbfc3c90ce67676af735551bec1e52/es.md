```
zero(x)
zero(::Type)
```

Obtiene el elemento de identidad aditiva para el tipo de `x` (`x` también puede especificar el tipo en sí).

Véase también [`iszero`](@ref), [`one`](@ref), [`oneunit`](@ref), [`oftype`](@ref).

# Ejemplos

```jldoctest
julia> zero(1)
0

julia> zero(big"2.0")
0.0

julia> zero(rand(2,2))
2×2 Matrix{Float64}:
 0.0  0.0
 0.0  0.0
```
