```
exp2(x)
```

Calcule l'exponentielle de base 2 de `x`, en d'autres termes $2^x$.

Voir aussi [`ldexp`](@ref), [`<<`](@ref).

# Exemples

```jldoctest
julia> exp2(5)
32.0

julia> 2^5
32

julia> exp2(63) > typemax(Int)
true
```
