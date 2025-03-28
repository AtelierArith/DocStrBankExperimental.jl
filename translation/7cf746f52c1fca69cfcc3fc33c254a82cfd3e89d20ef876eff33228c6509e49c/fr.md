```
nor(x, y)
⊽(x, y)
```

Nor bit à bit (non ou) de `x` et `y`. Implémente [la logique à trois valeurs](https://en.wikipedia.org/wiki/Three-valued_logic), retournant [`missing`](@ref) si l'un des arguments est `missing` et l'autre n'est pas `true`.

L'opération infixe `a ⊽ b` est un synonyme de `nor(a,b)`, et `⊽` peut être tapé en complétant par tabulation `\nor` ou `\barvee` dans le REPL Julia.

# Exemples

```jldoctest
julia> nor(true, false)
false

julia> nor(true, true)
false

julia> nor(true, missing)
false

julia> false ⊽ false
true

julia> false ⊽ missing
missing

julia> [true; true; false] .⊽ [true; false; false]
3-element BitVector:
 0
 0
 1
```
