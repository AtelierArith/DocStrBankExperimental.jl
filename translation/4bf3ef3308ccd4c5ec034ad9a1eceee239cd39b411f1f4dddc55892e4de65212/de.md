```
UniformScaling{T<:Number}
```

Generisch dimensionierter einheitlicher Skalierungsoperator, definiert als ein Skalar mal den Identitätsoperator, `λ*I`. Obwohl ohne eine explizite `size`, verhält er sich in vielen Fällen ähnlich wie eine Matrix und unterstützt einige Indizierungen. Siehe auch [`I`](@ref).

!!! compat "Julia 1.6"
    Indizierung mit Bereichen ist seit Julia 1.6 verfügbar.


# Beispiele

```jldoctest
julia> J = UniformScaling(2.)
UniformScaling{Float64}
2.0*I

julia> A = [1. 2.; 3. 4.]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> J*A
2×2 Matrix{Float64}:
 2.0  4.0
 6.0  8.0

julia> J[1:2, 1:2]
2×2 Matrix{Float64}:
 2.0  0.0
 0.0  2.0
```
