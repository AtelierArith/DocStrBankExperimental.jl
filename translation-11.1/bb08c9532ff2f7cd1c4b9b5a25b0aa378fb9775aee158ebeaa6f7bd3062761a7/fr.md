```
zeros([T=Float64,] dims::Tuple)
zeros([T=Float64,] dims...)
```

Crée un `Array`, avec le type d'élément `T`, de tous les zéros avec une taille spécifiée par `dims`. Voir aussi [`fill`](@ref), [`ones`](@ref), [`zero`](@ref).

# Exemples

```jldoctest
julia> zeros(1)
1-element Vector{Float64}:
 0.0

julia> zeros(Int8, 2, 3)
2×3 Matrix{Int8}:
 0  0  0
 0  0  0
```
