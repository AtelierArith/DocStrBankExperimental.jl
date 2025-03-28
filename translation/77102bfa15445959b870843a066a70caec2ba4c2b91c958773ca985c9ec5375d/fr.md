```
lmul!(a::Number, B::AbstractArray)
```

Échelle d'un tableau `B` par un scalaire `a` en écrasant `B` sur place. Utilisez [`rmul!`](@ref) pour multiplier le scalaire par la droite. L'opération de mise à l'échelle respecte la sémantique de la multiplication [`*`](@ref) entre `a` et un élément de `B`. En particulier, cela s'applique également à la multiplication impliquant des nombres non finis tels que `NaN` et `±Inf`.

!!! compat "Julia 1.1"
    Avant Julia 1.1, les entrées `NaN` et `±Inf` dans `B` étaient traitées de manière incohérente.


# Exemples

```jldoctest
julia> B = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> lmul!(2, B)
2×2 Matrix{Int64}:
 2  4
 6  8

julia> lmul!(0.0, [Inf])
1-element Vector{Float64}:
 NaN
```
