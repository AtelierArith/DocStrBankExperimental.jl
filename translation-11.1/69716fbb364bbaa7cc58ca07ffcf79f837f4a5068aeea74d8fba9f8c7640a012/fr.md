```
abs2(x)
```

Valeur absolue au carré de `x`.

Cela peut être plus rapide que `abs(x)^2`, en particulier pour les nombres complexes où `abs(x)` nécessite une racine carrée via [`hypot`](@ref).

Voir aussi [`abs`](@ref), [`conj`](@ref), [`real`](@ref).

# Exemples

```jldoctest
julia> abs2(-3)
9

julia> abs2(3.0 + 4.0im)
25.0

julia> sum(abs2, [1+2im, 3+4im])  # LinearAlgebra.norm(x)^2
30
```
