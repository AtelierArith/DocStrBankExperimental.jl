```
iszero(x)
```

Renvoie `true` si `x == zero(x)` ; si `x` est un tableau, cela vérifie si tous les éléments de `x` sont zéro.

Voir aussi : [`isone`](@ref), [`isinteger`](@ref), [`isfinite`](@ref), [`isnan`](@ref).

# Exemples

```jldoctest
julia> iszero(0.0)
true

julia> iszero([1, 9, 0])
false

julia> iszero([false, 0, 0])
true
```
