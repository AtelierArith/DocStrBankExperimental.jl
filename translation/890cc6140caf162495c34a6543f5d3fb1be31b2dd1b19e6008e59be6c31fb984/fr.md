```
!(x)
```

Non booléen. Implémente la [logique à trois valeurs](https://en.wikipedia.org/wiki/Three-valued_logic), retournant [`missing`](@ref) si `x` est `missing`.

Voir aussi [`~`](@ref) pour non bit à bit.

# Exemples

```jldoctest
julia> !true
false

julia> !false
true

julia> !missing
missing

julia> .![true false true]
1×3 BitMatrix:
 0  1  0
```
