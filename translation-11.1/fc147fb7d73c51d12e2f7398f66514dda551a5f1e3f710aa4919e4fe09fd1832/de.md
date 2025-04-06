```
ldiv!(a::Number, B::AbstractArray)
```

Teile jeden Eintrag in einem Array `B` durch einen Skalar `a` und überschreibe `B` im Platz. Verwende [`rdiv!`](@ref), um den Skalar von rechts zu teilen.

# Beispiele

```jldoctest
julia> B = [1.0 2.0; 3.0 4.0]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> ldiv!(2.0, B)
2×2 Matrix{Float64}:
 0.5  1.0
 1.5  2.0
```
