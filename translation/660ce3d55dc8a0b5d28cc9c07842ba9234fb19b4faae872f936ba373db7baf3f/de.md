```
issorted(v, lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward)
```

Überprüfen, ob eine Sammlung in sortierter Reihenfolge ist. Die Schlüsselwörter ändern, welche Reihenfolge als sortiert betrachtet wird, wie in der [`sort!`](@ref) Dokumentation beschrieben.

# Beispiele

```jldoctest
julia> issorted([1, 2, 3])
true

julia> issorted([(1, "b"), (2, "a")], by = x -> x[1])
true

julia> issorted([(1, "b"), (2, "a")], by = x -> x[2])
false

julia> issorted([(1, "b"), (2, "a")], by = x -> x[2], rev=true)
true

julia> issorted([1, 2, -2, 3], by=abs)
true
```
