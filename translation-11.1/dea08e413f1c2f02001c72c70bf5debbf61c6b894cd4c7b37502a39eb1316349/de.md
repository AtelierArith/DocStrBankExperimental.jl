```
Adjoint
```

Fauler Wrapper-Typ für eine adjungierte Ansicht des zugrunde liegenden linearen Algebraobjekts, normalerweise ein `AbstractVector`/`AbstractMatrix`. Normalerweise sollte der `Adjoint`-Konstruktor nicht direkt aufgerufen werden, verwenden Sie stattdessen [`adjoint`](@ref). Um die Ansicht zu materialisieren, verwenden Sie [`copy`](@ref).

Dieser Typ ist für die Verwendung in der linearen Algebra gedacht - für allgemeine Datenmanipulation siehe [`permutedims`](@ref Base.permutedims).

# Beispiele

```jldoctest
julia> A = [3+2im 9+2im; 0 0]
2×2 Matrix{Complex{Int64}}:
 3+2im  9+2im
 0+0im  0+0im

julia> Adjoint(A)
2×2 adjoint(::Matrix{Complex{Int64}}) mit eltype Complex{Int64}:
 3-2im  0+0im
 9-2im  0+0im
```
