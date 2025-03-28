```
popat!(a::Vector, i::Integer, [default])
```

Entfernt das Element an der angegebenen `i` und gibt es zurück. Nachfolgende Elemente werden verschoben, um die resultierende Lücke zu füllen. Wenn `i` kein gültiger Index für `a` ist, wird `default` zurückgegeben oder ein Fehler ausgelöst, wenn `default` nicht angegeben ist.

Siehe auch: [`pop!`](@ref), [`popfirst!`](@ref), [`deleteat!`](@ref), [`splice!`](@ref).

!!! compat "Julia 1.5"
    Diese Funktion ist seit Julia 1.5 verfügbar.


# Beispiele

```jldoctest
julia> a = [4, 3, 2, 1]; popat!(a, 2)
3

julia> a
3-element Vector{Int64}:
 4
 2
 1

julia> popat!(a, 4, missing)
missing

julia> popat!(a, 4)
ERROR: BoundsError: attempt to access 3-element Vector{Int64} at index [4]
[...]
```
