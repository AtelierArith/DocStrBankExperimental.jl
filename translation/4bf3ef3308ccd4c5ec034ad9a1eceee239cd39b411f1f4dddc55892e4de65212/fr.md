```
UniformScaling{T<:Number}
```

Opérateur de mise à l'échelle uniforme de taille générique défini comme un scalaire multiplié par l'opérateur d'identité, `λ*I`. Bien qu'il n'ait pas de `size` explicite, il agit de manière similaire à une matrice dans de nombreux cas et inclut le support pour certains indexages. Voir aussi [`I`](@ref).

!!! compat "Julia 1.6"
    L'indexation utilisant des plages est disponible depuis Julia 1.6.


# Exemples

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
