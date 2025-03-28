```
min(x, y, ...)
```

Gibt das Minimum der Argumente zurück, bezogen auf [`isless`](@ref). Wenn eines der Argumente [`missing`](@ref) ist, wird `missing` zurückgegeben. Siehe auch die Funktion [`minimum`](@ref), um das minimale Element aus einer Sammlung zu entnehmen.

# Beispiele

```jldoctest
julia> min(2, 5, 1)
1

julia> min(4, missing, 6)
missing
```
