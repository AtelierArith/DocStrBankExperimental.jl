```
stride(A, k::Integer)
```

Retourne la distance en mémoire (en nombre d'éléments) entre les éléments adjacents dans la dimension `k`.

Voir aussi : [`strides`](@ref).

# Exemples

```jldoctest
julia> A = fill(1, (3,4,5));

julia> stride(A,2)
3

julia> stride(A,3)
12
```
