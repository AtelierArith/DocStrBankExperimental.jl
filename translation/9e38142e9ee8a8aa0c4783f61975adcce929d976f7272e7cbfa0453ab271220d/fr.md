```
nand(x, y)
⊼(x, y)
```

Nand bitwise (non et) de `x` et `y`. Implémente la [logique à trois valeurs](https://en.wikipedia.org/wiki/Three-valued_logic), retournant [`missing`](@ref) si l'un des arguments est `missing`.

L'opération infixe `a ⊼ b` est un synonyme de `nand(a,b)`, et `⊼` peut être tapé en complétant par tabulation `\nand` ou `\barwedge` dans le REPL Julia.

# Exemples

```jldoctest
julia> nand(true, false)
true

julia> nand(true, true)
false

julia> nand(true, missing)
missing

julia> false ⊼ false
true

julia> [true; true; false] .⊼ [true; false; false]
3-element BitVector:
 0
 1
 1
```
