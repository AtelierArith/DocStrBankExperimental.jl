```
mod1(x, y)
```

Modulus après division par plancher, retournant une valeur `r` telle que `mod(r, y) == mod(x, y)` dans l'intervalle $(0, y]$ pour `y` positif et dans l'intervalle $[y,0)$ pour `y` négatif.

Avec des arguments entiers et un `y` positif, cela est égal à `mod(x, 1:y)`, et donc naturel pour l'indexation à partir de 1. En comparaison, `mod(x, y) == mod(x, 0:y-1)` est naturel pour les calculs avec des décalages ou des pas.

Voir aussi [`mod`](@ref), [`fld1`](@ref), [`fldmod1`](@ref).

# Exemples

```jldoctest
julia> mod1(4, 2)
2

julia> mod1.(-5:5, 3)'
1×11 adjoint(::Vector{Int64}) avec eltype Int64:
 1  2  3  1  2  3  1  2  3  1  2

julia> mod1.([-0.1, 0, 0.1, 1, 2, 2.9, 3, 3.1]', 3)
1×8 Matrix{Float64}:
 2.9  3.0  0.1  1.0  2.0  2.9  3.0  0.1
```
