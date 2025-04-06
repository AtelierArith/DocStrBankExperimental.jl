```
issetequal(a, b) -> Bool
```

Determina si `a` y `b` tienen los mismos elementos. Equivalente a `a ⊆ b && b ⊆ a` pero más eficiente cuando es posible.

Véase también: [`isdisjoint`](@ref), [`union`](@ref).

# Ejemplos

```jldoctest
julia> issetequal([1, 2], [1, 2, 3])
false

julia> issetequal([1, 2], [2, 1])
true
```
