```
⊈(a, b) -> Bool
⊉(b, a) -> Bool
```

Négation de `⊆` et `⊇`, c'est-à-dire vérifie que `a` n'est pas un sous-ensemble de `b`.

Voir aussi [`issubset`](@ref) (`⊆`), [`⊊`](@ref).

# Exemples

```jldoctest
julia> (1, 2) ⊈ (2, 3)
true

julia> (1, 2) ⊈ (1, 2, 3)
false
```
