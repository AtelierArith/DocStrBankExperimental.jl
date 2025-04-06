```
rdiv!(A::AbstractArray, b::Number)
```

Teile jeden Eintrag in einem Array `A` durch einen Skalar `b`, wobei `A` vor Ort überschrieben wird. Verwende [`ldiv!`](@ref), um den Skalar von links zu teilen.

# Beispiele

```jldoctest
julia> A = [1.0 2.0; 3.0 4.0]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> rdiv!(A, 2.0)
2×2 Matrix{Float64}:
 0.5  1.0
 1.5  2.0
```
