```
widemul(x, y)
```

Multipliez `x` et `y`, en donnant le résultat sous un type plus grand.

Voir aussi [`promote`](@ref), [`Base.add_sum`](@ref).

# Exemples

```jldoctest
julia> widemul(Float32(3.0), 4.0) isa BigFloat
true

julia> typemax(Int8) * typemax(Int8)
1

julia> widemul(typemax(Int8), typemax(Int8))  # == 127^2
16129
```
