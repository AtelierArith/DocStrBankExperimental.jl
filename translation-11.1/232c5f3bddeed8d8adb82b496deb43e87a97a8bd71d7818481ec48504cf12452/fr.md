```
abs(x)
```

La valeur absolue de `x`.

Lorsque `abs` est appliqué à des entiers signés, un dépassement peut se produire, entraînant le retour d'une valeur négative. Ce dépassement se produit uniquement lorsque `abs` est appliqué à la valeur minimale représentable d'un entier signé. C'est-à-dire que lorsque `x == typemin(typeof(x))`, `abs(x) == x < 0`, et non `-x` comme on pourrait s'y attendre.

Voir aussi : [`abs2`](@ref), [`unsigned`](@ref), [`sign`](@ref).

# Exemples

```jldoctest
julia> abs(-3)
3

julia> abs(1 + im)
1.4142135623730951

julia> abs.(Int8[-128 -127 -126 0 126 127])  # dépassement à typemin(Int8)
1×6 Matrix{Int8}:
 -128  127  126  0  126  127

julia> maximum(abs, [1, -2, 3, -4])
4
```
