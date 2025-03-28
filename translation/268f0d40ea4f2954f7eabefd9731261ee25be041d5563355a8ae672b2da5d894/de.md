```
Transponieren
```

Fauler Wrapper-Typ für eine Transponierungsansicht des zugrunde liegenden linearen Algebraobjekts, normalerweise ein `AbstractVector`/`AbstractMatrix`. Normalerweise sollte der `Transpose`-Konstruktor nicht direkt aufgerufen werden, verwenden Sie stattdessen [`transpose`](@ref). Um die Ansicht zu materialisieren, verwenden Sie [`copy`](@ref).

Dieser Typ ist für die Verwendung in der linearen Algebra gedacht - für allgemeine Datenmanipulation siehe [`permutedims`](@ref Base.permutedims).

# Beispiele

```jldoctest
julia> A = [2 3; 0 0]
2×2 Matrix{Int64}:
 2  3
 0  0

julia> Transpose(A)
2×2 transpose(::Matrix{Int64}) with eltype Int64:
 2  0
 3  0
```
