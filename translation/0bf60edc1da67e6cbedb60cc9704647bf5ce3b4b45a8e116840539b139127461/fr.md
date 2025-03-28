```
signbit(x)
```

Retourne `true` si la valeur du signe de `x` est négative, sinon `false`.

Voir aussi [`sign`](@ref) et [`copysign`](@ref).

# Exemples

```jldoctest
julia> signbit(-4)
true

julia> signbit(5)
false

julia> signbit(5.5)
false

julia> signbit(-4.1)
true
```
