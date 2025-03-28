```
xor(x, y)
⊻(x, y)
```

Opération exclusive ou bit à bit de `x` et `y`. Implémente la [logique à trois valeurs](https://en.wikipedia.org/wiki/Three-valued_logic), retournant [`missing`](@ref) si l'un des arguments est `missing`.

L'opération infixe `a ⊻ b` est un synonyme de `xor(a,b)`, et `⊻` peut être tapé en complétant par tabulation `\xor` ou `\veebar` dans le REPL Julia.

# Exemples

```jldoctest
julia> xor(true, false)
true

julia> xor(true, true)
false

julia> xor(true, missing)
missing

julia> false ⊻ false
false

julia> [true; true; false] .⊻ [true; false; false]
3-element BitVector:
 0
 1
 0
```
