```
⊈(a, b) -> Bool
⊉(b, a) -> Bool
```

Negación de `⊆` y `⊇`, es decir, verifica que `a` no sea un subconjunto de `b`.

Véase también [`issubset`](@ref) (`⊆`), [`⊊`](@ref).

# Ejemplos

```jldoctest
julia> (1, 2) ⊈ (2, 3)
true

julia> (1, 2) ⊈ (1, 2, 3)
false
```
