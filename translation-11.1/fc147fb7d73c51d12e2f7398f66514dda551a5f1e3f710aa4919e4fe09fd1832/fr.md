```
ldiv!(a::Number, B::AbstractArray)
```

Divise chaque entrée d'un tableau `B` par un scalaire `a` en écrasant `B` sur place. Utilisez [`rdiv!`](@ref) pour diviser le scalaire par la droite.

# Exemples

```jldoctest
julia> B = [1.0 2.0; 3.0 4.0]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> ldiv!(2.0, B)
2×2 Matrix{Float64}:
 0.5  1.0
 1.5  2.0
```
