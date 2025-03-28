```
svdvals(A, B)
```

Retourne les valeurs singulières généralisées de la décomposition en valeurs singulières généralisées de `A` et `B`. Voir aussi [`svd`](@ref).

# Exemples

```jldoctest
julia> A = [1. 0.; 0. -1.]
2×2 Matrix{Float64}:
 1.0   0.0
 0.0  -1.0

julia> B = [0. 1.; 1. 0.]
2×2 Matrix{Float64}:
 0.0  1.0
 1.0  0.0

julia> svdvals(A, B)
2-element Vector{Float64}:
 1.0
 1.0
```
