```
isdisjoint(a, b) -> Bool
```

Bestimmen Sie, ob die Sammlungen `a` und `b` disjunkt sind. Entspricht `isempty(a ∩ b)`, ist aber effizienter, wenn möglich.

Siehe auch: [`intersect`](@ref), [`isempty`](@ref), [`issetequal`](@ref).

!!! compat "Julia 1.5"
    Diese Funktion erfordert mindestens Julia 1.5.


# Beispiele

```jldoctest
julia> isdisjoint([1, 2], [2, 3, 4])
false

julia> isdisjoint([3, 1], [2, 4])
true
```
