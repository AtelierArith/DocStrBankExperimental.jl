```
cispi(x)
```

Méthode plus précise pour `cis(pi*x)` (surtout pour de grandes valeurs de `x`).

Voir aussi [`cis`](@ref), [`sincospi`](@ref), [`exp`](@ref), [`angle`](@ref).

# Exemples

```jldoctest
julia> cispi(10000)
1.0 + 0.0im

julia> cispi(0.25 + 1im)
0.030556854645954562 + 0.03055685464595456im
```

!!! compat "Julia 1.6"
    Cette fonction nécessite Julia 1.6 ou une version ultérieure.

