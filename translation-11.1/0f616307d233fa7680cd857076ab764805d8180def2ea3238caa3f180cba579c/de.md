```
max(x, y, ...)
```

Gibt das Maximum der Argumente zurück, bezogen auf [`isless`](@ref). Wenn eines der Argumente [`missing`](@ref) ist, wird `missing` zurückgegeben. Siehe auch die Funktion [`maximum`](@ref), um das maximale Element aus einer Sammlung zu entnehmen.

# Beispiele

```jldoctest
julia> max(2, 5, 1)
5

julia> max(5, missing, 6)
missing
```
