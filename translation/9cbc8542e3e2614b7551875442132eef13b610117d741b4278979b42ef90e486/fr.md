```
sin(A::AbstractMatrix)
```

Calcule le sinus matriciel d'une matrice carrée `A`.

Si `A` est symétrique ou hermitienne, sa décomposition en valeurs propres ([`eigen`](@ref)) est utilisée pour calculer le sinus. Sinon, le sinus est déterminé en appelant [`exp`](@ref).

# Exemples

```jldoctest
julia> sin(fill(1.0, (2,2)))
2×2 Matrix{Float64}:
 0.454649  0.454649
 0.454649  0.454649
```
