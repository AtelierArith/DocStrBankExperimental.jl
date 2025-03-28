```
rmul!(A::AbstractArray, b::Number)
```

Échelle un tableau `A` par un scalaire `b` en écrasant `A` sur place. Utilisez [`lmul!`](@ref) pour multiplier le scalaire par la gauche. L'opération de mise à l'échelle respecte la sémantique de la multiplication [`*`](@ref) entre un élément de `A` et `b`. En particulier, cela s'applique également à la multiplication impliquant des nombres non finis tels que `NaN` et `±Inf`.

!!! compat "Julia 1.1"
    Avant Julia 1.1, les entrées `NaN` et `±Inf` dans `A` étaient traitées de manière incohérente.


# Exemples

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> rmul!(A, 2)
2×2 Matrix{Int64}:
 2  4
 6  8

julia> rmul!([NaN], 0.0)
1-element Vector{Float64}:
 NaN
```
