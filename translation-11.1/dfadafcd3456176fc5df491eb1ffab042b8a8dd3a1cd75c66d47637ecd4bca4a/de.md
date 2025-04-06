```
argmin(A; dims) -> Indizes
```

Für eine Array-Eingabe geben Sie die Indizes der minimalen Elemente über die angegebenen Dimensionen zurück. `NaN` wird als kleiner als alle anderen Werte außer `missing` behandelt.

# Beispiele

```jldoctest
julia> A = [1.0 2; 3 4]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> argmin(A, dims=1)
1×2 Matrix{CartesianIndex{2}}:
 CartesianIndex(1, 1)  CartesianIndex(1, 2)

julia> argmin(A, dims=2)
2×1 Matrix{CartesianIndex{2}}:
 CartesianIndex(1, 1)
 CartesianIndex(2, 1)
```
