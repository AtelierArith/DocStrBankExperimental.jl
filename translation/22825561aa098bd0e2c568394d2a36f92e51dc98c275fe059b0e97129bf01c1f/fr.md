```
x | y
```

Opérateur binaire ou. Implémente la [logique à trois valeurs](https://en.wikipedia.org/wiki/Three-valued_logic), retournant [`missing`](@ref) si un opérande est `missing` et l'autre est `false`.

Voir aussi : [`&`](@ref), [`xor`](@ref), [`||`](@ref).

# Exemples

```jldoctest
julia> 4 | 10
14

julia> 4 | 1
5

julia> true | missing
true

julia> false | missing
missing
```
