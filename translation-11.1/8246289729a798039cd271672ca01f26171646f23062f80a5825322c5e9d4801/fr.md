```
inv(x)
```

Retourne l'inverse multiplicatif de `x`, tel que `x*inv(x)` ou `inv(x)*x` donne [`one(x)`](@ref) (l'identité multiplicative) jusqu'aux erreurs d'arrondi.

Si `x` est un nombre, c'est essentiellement la même chose que `one(x)/x`, mais pour certains types, `inv(x)` peut être légèrement plus efficace.

# Exemples

```jldoctest
julia> inv(2)
0.5

julia> inv(1 + 2im)
0.2 - 0.4im

julia> inv(1 + 2im) * (1 + 2im)
1.0 + 0.0im

julia> inv(2//3)
3//2
```

!!! compat "Julia 1.2"
    `inv(::Missing)` nécessite au moins Julia 1.2.

