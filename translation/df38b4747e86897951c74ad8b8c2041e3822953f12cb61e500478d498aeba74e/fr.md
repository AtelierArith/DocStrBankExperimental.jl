```
x & y
```

Et logique. Implémente la [logique à trois valeurs](https://en.wikipedia.org/wiki/Three-valued_logic), retournant [`missing`](@ref) si un opérande est `missing` et l'autre est `true`. Ajoutez des parenthèses pour la forme d'application de fonction : `(&)(x, y)`.

Voir aussi : [`|`](@ref), [`xor`](@ref), [`&&`](@ref).

# Exemples

```jldoctest
julia> 4 & 10
0

julia> 4 & 12
4

julia> true & missing
missing

julia> false & missing
false
```
