```
issorted(v, lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward)
```

Testez si une collection est triée. Les mots-clés modifient quel ordre est considéré comme trié, comme décrit dans la documentation de [`sort!`](@ref).

# Exemples

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
