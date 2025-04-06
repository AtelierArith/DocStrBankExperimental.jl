```
issetequal(a, b) -> Bool
```

Déterminez si `a` et `b` ont les mêmes éléments. Équivalent à `a ⊆ b && b ⊆ a` mais plus efficace lorsque c'est possible.

Voir aussi : [`isdisjoint`](@ref), [`union`](@ref).

# Exemples

```jldoctest
julia> issetequal([1, 2], [1, 2, 3])
false

julia> issetequal([1, 2], [2, 1])
true
```
