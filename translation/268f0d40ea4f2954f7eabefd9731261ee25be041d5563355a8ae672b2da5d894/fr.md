```
Transposé
```

Type d'enveloppe paresseux pour une vue transposée de l'objet d'algèbre linéaire sous-jacent, généralement un `AbstractVector`/`AbstractMatrix`. En général, le constructeur `Transpose` ne doit pas être appelé directement, utilisez plutôt [`transpose`](@ref). Pour matérialiser la vue, utilisez [`copy`](@ref).

Ce type est destiné à une utilisation en algèbre linéaire - pour la manipulation générale des données, voir [`permutedims`](@ref Base.permutedims).

# Exemples

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
