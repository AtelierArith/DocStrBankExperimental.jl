```
⊊(a, b) -> Bool
⊋(b, a) -> Bool
```

Bestimmt, ob `a` eine Teilmenge von `b` ist, aber nicht gleich `b`.

Siehe auch [`issubset`](@ref) (`⊆`), [`⊈`](@ref).

# Beispiele

```jldoctest
julia> (1, 2) ⊊ (1, 2, 3)
true

julia> (1, 2) ⊊ (1, 2)
false
```
