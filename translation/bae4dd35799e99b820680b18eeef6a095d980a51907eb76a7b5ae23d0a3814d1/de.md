```
UnionAll
```

Eine Vereinigung von Typen über alle Werte eines Typparameters. `UnionAll` wird verwendet, um parametrische Typen zu beschreiben, bei denen die Werte einiger Parameter nicht bekannt sind. Siehe den Handbuchabschnitt über [UnionAll Types](@ref).

# Beispiele

```jldoctest
julia> typeof(Vector)
UnionAll

julia> typeof(Vector{Int})
DataType
```
