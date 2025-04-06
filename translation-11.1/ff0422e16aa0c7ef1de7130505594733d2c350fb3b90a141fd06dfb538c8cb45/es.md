```
isdisjoint(a, b) -> Bool
```

Determina si las colecciones `a` y `b` son disjuntas. Equivalente a `isempty(a ∩ b)` pero más eficiente cuando es posible.

Véase también: [`intersect`](@ref), [`isempty`](@ref), [`issetequal`](@ref).

!!! compat "Julia 1.5"
    Esta función requiere al menos Julia 1.5.


# Ejemplos

```jldoctest
julia> isdisjoint([1, 2], [2, 3, 4])
false

julia> isdisjoint([3, 1], [2, 4])
true
```
