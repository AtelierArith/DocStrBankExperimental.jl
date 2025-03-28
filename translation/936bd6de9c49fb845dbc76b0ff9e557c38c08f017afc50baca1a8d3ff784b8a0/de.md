```
findmin(A; dims) -> (minval, index)
```

Für eine Array-Eingabe gibt es den Wert und den Index des Minimums über die angegebenen Dimensionen zurück. `NaN` wird als kleiner als alle anderen Werte außer `missing` behandelt.

# Beispiele

```jldoctest
julia> A = [1.0 2; 3 4]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> findmin(A, dims=1)
([1.0 2.0], CartesianIndex{2}[CartesianIndex(1, 1) CartesianIndex(1, 2)])

julia> findmin(A, dims=2)
([1.0; 3.0;;], CartesianIndex{2}[CartesianIndex(1, 1); CartesianIndex(2, 1);;])
```
