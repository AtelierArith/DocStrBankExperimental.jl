```
x || y
```

Opérateur booléen OU avec court-circuit.

Voir aussi : [`|`](@ref), [`xor`](@ref), [`&&`](@ref).

# Exemples

```jldoctest
julia> pi < 3 || ℯ < 3
true

julia> false || true || println("aucun n'est vrai !")
true
```
