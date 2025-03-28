```
>>>(x, n)
```

Opérateur de décalage de bits à droite non signé, `x >>> n`. Pour `n >= 0`, le résultat est `x` décalé à droite de `n` bits, en remplissant avec des `0`. Pour `n < 0`, cela équivaut à `x << -n`.

Pour les types d'entiers [`Unsigned`](@ref), cela équivaut à [`>>`](@ref). Pour les types d'entiers [`Signed`](@ref), cela équivaut à `signed(unsigned(x) >> n)`.

# Exemples

```jldoctest
julia> Int8(-14) >>> 2
60

julia> bitstring(Int8(-14))
"11110010"

julia> bitstring(Int8(60))
"00111100"
```

Les [`BigInt`](@ref) sont traités comme s'ils avaient une taille infinie, donc aucun remplissage n'est requis et cela équivaut à [`>>`](@ref).

Voir aussi [`>>`](@ref), [`<<`](@ref).
