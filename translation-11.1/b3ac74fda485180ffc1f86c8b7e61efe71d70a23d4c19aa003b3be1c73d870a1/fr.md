```
vec(a::AbstractArray) -> AbstractVector
```

Reshape le tableau `a` en un vecteur colonne unidimensionnel. Retourne `a` s'il est déjà un `AbstractVector`. Le tableau résultant partage les mêmes données sous-jacentes que `a`, donc il ne sera mutable que si `a` est mutable, auquel cas modifier l'un modifiera également l'autre.

# Exemples

```jldoctest
julia> a = [1 2 3; 4 5 6]
2×3 Matrix{Int64}:
 1  2  3
 4  5  6

julia> vec(a)
6-element Vector{Int64}:
 1
 4
 2
 5
 3
 6

julia> vec(1:3)
1:3
```

Voir aussi [`reshape`](@ref), [`dropdims`](@ref).
