```
issubset(a, b) -> Bool
⊆(a, b) -> Bool
⊇(b, a) -> Bool
```

Bestimmen Sie, ob jedes Element von `a` auch in `b` enthalten ist, unter Verwendung von [`in`](@ref).

Siehe auch [`⊊`](@ref), [`⊈`](@ref), [`∩`](@ref intersect), [`∪`](@ref union), [`contains`](@ref).

# Beispiele

```jldoctest
julia> issubset([1, 2], [1, 2, 3])
true

julia> [1, 2, 3] ⊆ [1, 2]
false

julia> [1, 2, 3] ⊇ [1, 2]
true
```
