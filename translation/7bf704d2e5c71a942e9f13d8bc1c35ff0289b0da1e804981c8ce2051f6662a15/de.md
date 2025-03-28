```
rmul!(A::AbstractArray, b::Number)
```

Skaliere ein Array `A` mit einem Skalar `b`, indem `A` vor Ort überschrieben wird. Verwende [`lmul!`](@ref), um den Skalar von links zu multiplizieren. Die Skalierungsoperation respektiert die Semantik der Multiplikation [`*`](@ref) zwischen einem Element von `A` und `b`. Insbesondere gilt dies auch für Multiplikationen, die nicht-finite Zahlen wie `NaN` und `±Inf` betreffen.

!!! compat "Julia 1.1"
    Vor Julia 1.1 wurden `NaN` und `±Inf` Einträge in `A` inkonsistent behandelt.


# Beispiele

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> rmul!(A, 2)
2×2 Matrix{Int64}:
 2  4
 6  8

julia> rmul!([NaN], 0.0)
1-element Vector{Float64}:
 NaN
```
