```
⊈(a, b) -> Bool
⊉(b, a) -> Bool
```

Negation von `⊆` und `⊇`, d.h. überprüft, dass `a` keine Teilmenge von `b` ist.

Siehe auch [`issubset`](@ref) (`⊆`), [`⊊`](@ref).

# Beispiele

```jldoctest
julia> (1, 2) ⊈ (2, 3)
true

julia> (1, 2) ⊈ (1, 2, 3)
false
```
