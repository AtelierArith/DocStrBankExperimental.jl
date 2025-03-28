```
diff(A::AbstractVector)
diff(A::AbstractArray; dims::Integer)
```

Opérateur de différence finie sur un vecteur ou un tableau multidimensionnel `A`. Dans ce dernier cas, la dimension sur laquelle opérer doit être spécifiée avec l'argument clé `dims`.

!!! compat "Julia 1.1"
    `diff` pour les tableaux avec une dimension supérieure à 2 nécessite au moins Julia 1.1.


# Exemples

```jldoctest
julia> a = [2 4; 6 16]
2×2 Matrix{Int64}:
 2   4
 6  16

julia> diff(a, dims=2)
2×1 Matrix{Int64}:
  2
 10

julia> diff(vec(a))
3-element Vector{Int64}:
  4
 -2
 12
```
