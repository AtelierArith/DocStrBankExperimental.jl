```
findmax(A; dims) -> (maxval, index)
```

Für eine Array-Eingabe gibt es den Wert und den Index des Maximums über die angegebenen Dimensionen zurück. `NaN` wird als größer als alle anderen Werte außer `missing` behandelt.

# Beispiele

```jldoctest
julia> A = [1.0 2; 3 4]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> findmax(A, dims=1)
([3.0 4.0], CartesianIndex{2}[CartesianIndex(2, 1) CartesianIndex(2, 2)])

julia> findmax(A, dims=2)
([2.0; 4.0;;], CartesianIndex{2}[CartesianIndex(1, 2); CartesianIndex(2, 2);;])
```
