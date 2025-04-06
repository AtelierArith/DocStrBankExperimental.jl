```
+(x, y...)
```

Opérateur d'addition.

L'infixe `x+y+z+...` appelle cette fonction avec tous les arguments, c'est-à-dire `+(x, y, z, ...)`, qui par défaut appelle alors `(x+y) + z + ...` en commençant par la gauche.

Notez que le débordement est possible pour la plupart des types entiers, y compris le `Int` par défaut, lors de l'addition de grands nombres.

# Exemples

```jldoctest
julia> 1 + 20 + 4
25

julia> +(1, 20, 4)
25

julia> [1,2] + [3,4]
2-element Vector{Int64}:
 4
 6

julia> typemax(Int) + 1 < 0
true
```
