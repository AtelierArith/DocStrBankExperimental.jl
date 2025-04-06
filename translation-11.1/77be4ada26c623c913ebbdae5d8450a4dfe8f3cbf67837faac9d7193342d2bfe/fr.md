```
exp(x)
```

Calculez l'exponentielle à base naturelle de `x`, en d'autres termes $ℯ^x$.

Voir aussi [`exp2`](@ref), [`exp10`](@ref) et [`cis`](@ref).

# Exemples

```jldoctest
julia> exp(1.0)
2.718281828459045

julia> exp(im * pi) ≈ cis(pi)
true
```
