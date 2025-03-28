```
zero(x)
zero(::Type)
```

Obtenez l'élément d'identité additive pour le type de `x` (`x` peut également spécifier le type lui-même).

Voir aussi [`iszero`](@ref), [`one`](@ref), [`oneunit`](@ref), [`oftype`](@ref).

# Exemples

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
