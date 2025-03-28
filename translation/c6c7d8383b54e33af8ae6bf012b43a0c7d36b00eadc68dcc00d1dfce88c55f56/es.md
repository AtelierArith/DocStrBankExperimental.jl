```
⊊(a, b) -> Bool
⊋(b, a) -> Bool
```

Determina si `a` es un subconjunto de, pero no igual a, `b`.

Véase también [`issubset`](@ref) (`⊆`), [`⊈`](@ref).

# Ejemplos

```jldoctest
julia> (1, 2) ⊊ (1, 2, 3)
true

julia> (1, 2) ⊊ (1, 2)
false
```
