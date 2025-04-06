```
Adjoint
```

Type d'enveloppe paresseux pour une vue adjoint de l'objet d'algèbre linéaire sous-jacent, généralement un `AbstractVector`/`AbstractMatrix`. En général, le constructeur `Adjoint` ne doit pas être appelé directement, utilisez plutôt [`adjoint`](@ref). Pour matérialiser la vue, utilisez [`copy`](@ref).

Ce type est destiné à une utilisation en algèbre linéaire - pour la manipulation générale des données, voir [`permutedims`](@ref Base.permutedims).

# Exemples

```jldoctest
julia> A = [3+2im 9+2im; 0 0]
2×2 Matrix{Complex{Int64}}:
 3+2im  9+2im
 0+0im  0+0im

julia> Adjoint(A)
2×2 adjoint(::Matrix{Complex{Int64}}) with eltype Complex{Int64}:
 3-2im  0+0im
 9-2im  0+0im
```
