```
*(x, y...)
```

Opérateur de multiplication.

L'infixe `x*y*z*...` appelle cette fonction avec tous les arguments, c'est-à-dire `*(x, y, z, ...)`, qui par défaut appelle alors `(x*y) * z * ...` en commençant par la gauche.

La juxtaposition comme `2pi` appelle également `*(2, pi)`. Notez que cette opération a une priorité plus élevée qu'un `*` littéral. Notez également que la juxtaposition "0x..." (zéro entier multiplié par une variable dont le nom commence par `x`) est interdite car elle entre en conflit avec les littéraux d'entiers non signés : `0x01 isa UInt8`.

Notez que le débordement est possible pour la plupart des types d'entiers, y compris le `Int` par défaut, lors de la multiplication de grands nombres.

# Exemples

```jldoctest
julia> 2 * 7 * 8
112

julia> *(2, 7, 8)
112

julia> [2 0; 0 3] * [1, 10]  # matrice * vecteur
2-element Vector{Int64}:
  2
 30

julia> 1/2pi, 1/2*pi  # la juxtaposition a une priorité plus élevée
(0.15915494309189535, 1.5707963267948966)

julia> x = [1, 2]; x'x  # vecteur adjoint * vecteur
5
```
