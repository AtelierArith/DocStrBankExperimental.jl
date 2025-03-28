```
setdiff!(s, itrs...)
```

Entferne aus der Menge `s` (in-place) jedes Element aus jedem Iterable von `itrs`. Behalte die Reihenfolge bei Arrays bei.

!!! warning
    Das Verhalten kann unerwartet sein, wenn ein mutiertes Argument Speicher mit einem anderen Argument teilt.


# Beispiele

```jldoctest
julia> a = Set([1, 3, 4, 5]);

julia> setdiff!(a, 1:2:6);

julia> a
Set{Int64} mit 1 Element:
  4
```
