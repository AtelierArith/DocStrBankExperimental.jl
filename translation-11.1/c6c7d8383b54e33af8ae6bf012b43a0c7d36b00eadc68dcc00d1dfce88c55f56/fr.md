```
⊊(a, b) -> Bool
⊋(b, a) -> Bool
```

Détermine si `a` est un sous-ensemble de, mais pas égal à, `b`.

Voir aussi [`issubset`](@ref) (`⊆`), [`⊈`](@ref).

# Exemples

```jldoctest
julia> (1, 2) ⊊ (1, 2, 3)
true

julia> (1, 2) ⊊ (1, 2)
false
```
