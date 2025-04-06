```
coalesce(x...)
```

Gibt den ersten Wert in den Argumenten zurück, der nicht gleich [`missing`](@ref) ist, falls vorhanden. Andernfalls wird `missing` zurückgegeben.

Siehe auch [`skipmissing`](@ref), [`something`](@ref), [`@coalesce`](@ref).

# Beispiele

```jldoctest
julia> coalesce(missing, 1)
1

julia> coalesce(1, missing)
1

julia> coalesce(nothing, 1)  # gibt `nothing` zurück

julia> coalesce(missing, missing)
missing
```
