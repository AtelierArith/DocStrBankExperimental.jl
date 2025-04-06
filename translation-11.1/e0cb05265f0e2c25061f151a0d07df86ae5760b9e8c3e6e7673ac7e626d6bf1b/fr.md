```
cos(A::AbstractMatrix)
```

Calcule le cosinus matriciel d'une matrice carrée `A`.

Si `A` est symétrique ou hermitienne, sa décomposition en valeurs propres ([`eigen`](@ref)) est utilisée pour calculer le cosinus. Sinon, le cosinus est déterminé en appelant [`exp`](@ref).

# Exemples

```jldoctest
julia> cos(fill(1.0, (2,2)))
2×2 Matrix{Float64}:
  0.291927  -0.708073
 -0.708073   0.291927
```
