```
ispow2(n::Number) -> Bool
```

Testez si `n` est une puissance entière de deux.

Voir aussi [`count_ones`](@ref), [`prevpow`](@ref), [`nextpow`](@ref).

# Exemples

```jldoctest
julia> ispow2(4)
true

julia> ispow2(5)
false

julia> ispow2(4.5)
false

julia> ispow2(0.25)
true

julia> ispow2(1//8)
true
```

!!! compat "Julia 1.6"
    Le support pour les arguments non-`Integer` a été ajouté dans Julia 1.6.

