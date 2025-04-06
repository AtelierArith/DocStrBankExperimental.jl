```
lmul!(a::Number, B::AbstractArray)
```

Skaliere ein Array `B` mit einem Skalar `a`, indem `B` vor Ort überschrieben wird. Verwende [`rmul!`](@ref), um den Skalar von rechts zu multiplizieren. Die Skalierungsoperation respektiert die Semantik der Multiplikation [`*`](@ref) zwischen `a` und einem Element von `B`. Insbesondere gilt dies auch für Multiplikationen, die nicht-finite Zahlen wie `NaN` und `±Inf` betreffen.

!!! compat "Julia 1.1"
    Vor Julia 1.1 wurden `NaN` und `±Inf` Einträge in `B` inkonsistent behandelt.


# Beispiele

```jldoctest
julia> B = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> lmul!(2, B)
2×2 Matrix{Int64}:
 2  4
 6  8

julia> lmul!(0.0, [Inf])
1-element Vector{Float64}:
 NaN
```
