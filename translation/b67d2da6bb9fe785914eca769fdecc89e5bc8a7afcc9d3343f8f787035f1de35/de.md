```
maximum!(r, A)
```

Berechne den maximalen Wert von `A` über die Singleton-Dimensionen von `r` und schreibe die Ergebnisse in `r`.

!!! warning
    Das Verhalten kann unerwartet sein, wenn ein mutiertes Argument Speicher mit einem anderen Argument teilt.


# Beispiele

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> maximum!([1; 1], A)
2-element Vector{Int64}:
 2
 4

julia> maximum!([1 1], A)
1×2 Matrix{Int64}:
 3  4
```
