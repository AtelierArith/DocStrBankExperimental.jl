```
minimum!(r, A)
```

Berechne den Minimalwert von `A` über die Einzel-Dimensionen von `r` und schreibe die Ergebnisse in `r`.

!!! warning
    Das Verhalten kann unerwartet sein, wenn ein veränderter Parameter Speicher mit einem anderen Parameter teilt.


# Beispiele

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> minimum!([1; 1], A)
2-element Vector{Int64}:
 1
 3

julia> minimum!([1 1], A)
1×2 Matrix{Int64}:
 1  2
```
