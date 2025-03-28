```
>>(x, n)
```

Opérateur de décalage à droite, `x >> n`. Pour `n >= 0`, le résultat est `x` décalé à droite de `n` bits, remplissant avec des `0` si `x >= 0`, des `1` si `x < 0`, préservant le signe de `x`. Cela équivaut à `fld(x, 2^n)`. Pour `n < 0`, cela équivaut à `x << -n`.

# Exemples

```jldoctest
julia> Int8(13) >> 2
3

julia> bitstring(Int8(13))
"00001101"

julia> bitstring(Int8(3))
"00000011"

julia> Int8(-14) >> 2
-4

julia> bitstring(Int8(-14))
"11110010"

julia> bitstring(Int8(-4))
"11111100"
```

Voir aussi [`>>>`](@ref), [`<<`](@ref).
