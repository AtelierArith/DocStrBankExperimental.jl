```
eigvals(A; permute::Bool=true, scale::Bool=true, sortby) -> values
```

Retourne les valeurs propres de `A`.

Pour les matrices non symétriques générales, il est possible de spécifier comment la matrice est équilibrée avant le calcul des valeurs propres. Les mots-clés `permute`, `scale` et `sortby` sont les mêmes que pour [`eigen`](@ref).

# Exemples

```jldoctest
julia> diag_matrix = [1 0; 0 4]
2×2 Matrix{Int64}:
 1  0
 0  4

julia> eigvals(diag_matrix)
2-element Vector{Float64}:
 1.0
 4.0
```
