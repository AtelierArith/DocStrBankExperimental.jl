```
AbstractRange{T} <: AbstractVector{T}
```

Supertype pour les plages linéaires avec des éléments de type `T`. [`UnitRange`](@ref), [`LinRange`](@ref) et d'autres types sont des sous-types de cela.

Tous les sous-types doivent définir [`step`](@ref). Ainsi, [`LogRange`](@ref Base.LogRange) n'est pas un sous-type de `AbstractRange`.
