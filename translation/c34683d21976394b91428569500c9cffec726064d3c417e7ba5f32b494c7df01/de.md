```
any!(r, A)
```

Überprüfen Sie, ob Werte in `A` entlang der Singleton-Dimensionen von `r` `true` sind, und schreiben Sie die Ergebnisse in `r`.

!!! warning
    Das Verhalten kann unerwartet sein, wenn ein veränderter Parameter Speicher mit einem anderen Parameter teilt.


# Beispiele

```jldoctest
julia> A = [true false; true false]
2×2 Matrix{Bool}:
 1  0
 1  0

julia> any!([1; 1], A)
2-element Vector{Int64}:
 1
 1

julia> any!([1 1], A)
1×2 Matrix{Int64}:
 1  0
```
