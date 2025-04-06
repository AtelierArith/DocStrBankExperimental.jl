```
union!(s::Union{AbstractSet,AbstractVector}, itrs...)
```

Konstruiere die [`union`](@ref) der übergebenen Mengen und überschreibe `s` mit dem Ergebnis. Behalte die Reihenfolge bei Arrays bei.

!!! warning
    Das Verhalten kann unerwartet sein, wenn ein mutiertes Argument Speicher mit einem anderen Argument teilt.


# Beispiele

```jldoctest
julia> a = Set([3, 4, 5]);

julia> union!(a, 1:2:7);

julia> a
Set{Int64} mit 5 Elementen:
  5
  4
  7
  3
  1
```
