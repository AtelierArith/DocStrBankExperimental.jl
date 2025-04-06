```
isdisjoint(a, b) -> Bool
```

Déterminez si les collections `a` et `b` sont disjointes. Équivalent à `isempty(a ∩ b)` mais plus efficace lorsque c'est possible.

Voir aussi : [`intersect`](@ref), [`isempty`](@ref), [`issetequal`](@ref).

!!! compat "Julia 1.5"
    Cette fonction nécessite au moins Julia 1.5.


# Exemples

```jldoctest
julia> isdisjoint([1, 2], [2, 3, 4])
false

julia> isdisjoint([3, 1], [2, 4])
true
```
