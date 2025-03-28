```
tan(A::AbstractMatrix)
```

Calcule la tangente matricielle d'une matrice carrée `A`.

Si `A` est symétrique ou hermitienne, sa décomposition en valeurs propres ([`eigen`](@ref)) est utilisée pour calculer la tangente. Sinon, la tangente est déterminée en appelant [`exp`](@ref).

# Exemples

```jldoctest
julia> tan(fill(1.0, (2,2)))
2×2 Matrix{Float64}:
 -1.09252  -1.09252
 -1.09252  -1.09252
```
