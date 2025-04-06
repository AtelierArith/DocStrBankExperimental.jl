```
zero(x)
zero(::Type)
```

Holen Sie sich das additive Identitätselement für den Typ von `x` (`x` kann auch den Typ selbst angeben).

Siehe auch [`iszero`](@ref), [`one`](@ref), [`oneunit`](@ref), [`oftype`](@ref).

# Beispiele

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
