```
extrema!(r, A)
```

Berechne den minimalen und maximalen Wert von `A` über die Singleton-Dimensionen von `r` und schreibe die Ergebnisse in `r`.

!!! warning
    Das Verhalten kann unerwartet sein, wenn ein veränderter Parameter Speicher mit einem anderen Parameter teilt.


!!! compat "Julia 1.8"
    Diese Methode erfordert Julia 1.8 oder höher.


# Beispiele

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> extrema!([(1, 1); (1, 1)], A)
2-element Vector{Tuple{Int64, Int64}}:
 (1, 2)
 (3, 4)

julia> extrema!([(1, 1);; (1, 1)], A)
1×2 Matrix{Tuple{Int64, Int64}}:
 (1, 3)  (2, 4)
```
