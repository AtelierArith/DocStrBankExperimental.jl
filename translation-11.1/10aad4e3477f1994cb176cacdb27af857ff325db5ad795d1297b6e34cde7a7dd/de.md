```
something(x...)
```

Gibt den ersten Wert in den Argumenten zurück, der nicht gleich [`nothing`](@ref) ist, falls vorhanden. Andernfalls wird ein Fehler ausgelöst. Argumente vom Typ [`Some`](@ref) werden entpackt.

Siehe auch [`coalesce`](@ref), [`skipmissing`](@ref), [`@something`](@ref).

# Beispiele

```jldoctest
julia> something(nothing, 1)
1

julia> something(Some(1), nothing)
1

julia> something(Some(nothing), 2) === nothing
true

julia> something(missing, nothing)
missing

julia> something(nothing, nothing)
ERROR: ArgumentError: Keine Wertargumente vorhanden
```
