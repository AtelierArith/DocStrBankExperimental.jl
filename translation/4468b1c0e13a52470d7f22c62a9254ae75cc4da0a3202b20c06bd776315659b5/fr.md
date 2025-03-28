```
rdiv!(A::AbstractArray, b::Number)
```

Divise chaque entrée d'un tableau `A` par un scalaire `b` en écrasant `A` sur place. Utilisez [`ldiv!`](@ref) pour diviser le scalaire par la gauche.

# Exemples

```jldoctest
julia> A = [1.0 2.0; 3.0 4.0]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> rdiv!(A, 2.0)
2×2 Matrix{Float64}:
 0.5  1.0
 1.5  2.0
```
