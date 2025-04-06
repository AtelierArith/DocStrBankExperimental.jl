```
@allocations
```

Ein Makro, um einen Ausdruck auszuwerten, den resultierenden Wert zu verwerfen und stattdessen die Gesamtzahl der Allokationen während der Auswertung des Ausdrucks zurückzugeben.

Siehe auch [`@allocated`](@ref), [`@time`](@ref), [`@timev`](@ref), [`@timed`](@ref) und [`@elapsed`](@ref).

```julia-repl
julia> @allocations rand(10^6)
2
```

!!! compat "Julia 1.9"
    Dieses Makro wurde in Julia 1.9 hinzugefügt.

