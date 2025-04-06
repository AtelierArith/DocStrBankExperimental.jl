```
ones([T=Float64,] dims::Tuple)
ones([T=Float64,] dims...)
```

Crée un `Array`, avec le type d'élément `T`, de tous les uns avec une taille spécifiée par `dims`. Voir aussi [`fill`](@ref), [`zeros`](@ref).

# Exemples

```jldoctest
julia> ones(1,2)
1×2 Matrix{Float64}:
 1.0  1.0

julia> ones(ComplexF64, 2, 3)
2×3 Matrix{ComplexF64}:
 1.0+0.0im  1.0+0.0im  1.0+0.0im
 1.0+0.0im  1.0+0.0im  1.0+0.0im
```
