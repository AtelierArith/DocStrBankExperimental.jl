```
issetequal(a, b) -> Bool
```

Bestimmen Sie, ob `a` und `b` die gleichen Elemente haben. Entspricht `a ⊆ b && b ⊆ a`, ist aber effizienter, wenn möglich.

Siehe auch: [`isdisjoint`](@ref), [`union`](@ref).

# Beispiele

```jldoctest
julia> issetequal([1, 2], [1, 2, 3])
false

julia> issetequal([1, 2], [2, 1])
true
```
