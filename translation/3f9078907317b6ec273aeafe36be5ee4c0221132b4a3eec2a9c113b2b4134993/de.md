```
@allocated
```

Ein Makro zur Auswertung eines Ausdrucks, das den resultierenden Wert verwirft und stattdessen die Gesamtanzahl der während der Auswertung des Ausdrucks zugewiesenen Bytes zurückgibt.

Siehe auch [`@allocations`](@ref), [`@time`](@ref), [`@timev`](@ref), [`@timed`](@ref) und [`@elapsed`](@ref).

```julia-repl
julia> @allocated rand(10^6)
8000080
```
