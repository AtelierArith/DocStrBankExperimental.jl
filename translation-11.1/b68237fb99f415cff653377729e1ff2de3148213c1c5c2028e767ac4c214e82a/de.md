```
mean!(r, v)
```

Berechne den Mittelwert von `v` über die Einzel-Dimensionen von `r` und schreibe die Ergebnisse in `r`.

# Beispiele

```jldoctest
julia> using Statistics

julia> v = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> mean!([1., 1.], v)
2-element Vector{Float64}:
 1.5
 3.5

julia> mean!([1. 1.], v)
1×2 Matrix{Float64}:
 2.0  3.0
```
